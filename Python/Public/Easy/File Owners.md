Implement a `group_by_owners` function that:

- Accepts a dictionary containing the file owner name for each file name.
- Returns a dictionary containing a list of file names for each owner name, in any order.

For example, for dictionary `{'Input.txt': 'Randy', 'Code.py': 'Stan', 'Output.txt': 'Randy'}` the `group_by_owners` function should return `{'Randy': ['Input.txt', 'Output.txt'], 'Stan': ['Code.py']}`.

``` python
class FileOwners:

    @staticmethod
    def group_by_owners(files):
        return None

files = {
    'Input.txt': 'Randy',
    'Code.py': 'Stan',
    'Output.txt': 'Randy'
}
print(FileOwners.group_by_owners(files))
```

<details><summary>Answer</summary>

``` python
class FileOwners:

    @staticmethod
    def group_by_owners(files):
        owners = {}
        for filename in files.keys():
            owner = files[filename]
            if owner not in owners:
                owners[owner] = list()
            owners[owner].append(filename)
        return owners

files = {
    'Input.txt': 'Randy',
    'Code.py': 'Stan',
    'Output.txt': 'Randy'
}
print(FileOwners.group_by_owners(files))
``` 

</details>
