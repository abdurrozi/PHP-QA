Implement methods and properties in the `DecoratorStream` class:

- `Write` method should write the prefix into the underlying stream member only on the first `Write` invocation. It should always write the bytes it receives to the underlying stream.
- The prefix should be written in UTF-8 encoding.

For example, if the `DecoratorStream` is instantiated with `"First line: "` as the prefix parameter and Write method is called with UTF-8 byte representation of `"Hello, world!"`, it should write `"First line: Hello, world!"` into the underlying stream.

``` csharp
using System;
using System.IO;
using System.Text;

public class DecoratorStream : Stream
{
	private Stream stream;
	private string prefix;
	
	public override bool CanSeek { get { return false; } }
	public override bool CanWrite { get { return true; } }
	public override long Length { get; }
	public override long Position { get; set; }
	public override bool CanRead { get { return false; } }
	
	public DecoratorStream(Stream stream, string prefix) : base()
	{
		this.stream = stream;
		this.prefix = prefix;
	}
	
	public override void SetLength(long length)
	{
		throw new NotSupportedException();
	}
	
	public override void Write(byte[] bytes, int offset, int count)
	{
        throw new NotImplementedException();
	}
	
	public override int Read(byte[] bytes, int offset, int count)
	{
		throw new NotSupportedException();
	}
	
	public override long Seek(long offset, SeekOrigin origin)
	{
		throw new NotSupportedException();
	}
	
	public override void Flush()
	{
		stream.Flush();
	}
    
    public static void Main(string[] args)
    {
        byte[] message = new byte[]{0x48, 0x65, 0x6c, 0x6c, 0x6f, 0x2c, 0x20, 0x77, 0x6f, 0x72, 0x6c, 0x64, 0x21};
        using (MemoryStream stream = new MemoryStream())
        {
            using (DecoratorStream decoratorStream = new DecoratorStream(stream, "First line: "))
            {
                decoratorStream.Write(message, 0, message.Length);
                stream.Position = 0;
                Console.WriteLine(new StreamReader(stream).ReadLine());  //should print "First line: Hello, world!"
            }
        }
    }
}
```

<details><summary>Answer</summary>

``` csharp
using System;
using System.IO;
using System.Text;

public class DecoratorStream : Stream
{
    private readonly Stream _stream;
    private readonly string _prefix;
    private bool _firstWriteCall;
    
    public override bool CanSeek => false;
    public override bool CanWrite => true;
    public override long Length { get; }
    public override long Position { get; set; }
    public override bool CanRead => false;

    public DecoratorStream(Stream stream, string prefix)
    {
        _stream = stream;
        _prefix = prefix;
    }

    public override void SetLength(long length)
    {
        _stream.SetLength(length);
    }

    public override void Write(byte[] bytes, int offset, int count)
    {
        if (!_firstWriteCall)
        {
            var prefixBytes = Encoding.UTF8.GetBytes(_prefix);
            _stream.Write(prefixBytes, 0, prefixBytes.Length);
            _firstWriteCall = true;
        }
        
        _stream.Write(bytes, offset, count);
    }

    public override int Read(byte[] bytes, int offset, int count)
    {
        return _stream.Read(bytes, offset, count);
    }

    public override long Seek(long offset, SeekOrigin origin)
    {
        return _stream.Seek(offset, origin);
    }

    public override void Flush()
    {
        _stream.Flush();
    }

    public static void Main(params string[] args)
    {
        var message = new byte[]
        {
            0x48, 
            0x65, 
            0x6c, 
            0x6c, 
            0x6f, 
            0x2c, 
            0x20, 
            0x77, 
            0x6f, 
            0x72, 
            0x6c, 
            0x64, 
            0x21
        };
        using (var memoryStream = new MemoryStream())
        {
            using (var decoratorStream = new DecoratorStream(memoryStream, "First line: "))
            {
                decoratorStream.Write(message, 0, message.Length);
                memoryStream.Position = 0;
                
                // Should print "First line: Hello, world!"
                Console.WriteLine(new StreamReader(memoryStream).ReadLine());  
            }
        }
    }
}
```

</details>
