A palindrome is a word that reads the same backward or forward.

Write a function that checks if a given word is a palindrome. Character case should be ignored.

For example, `is_palindrome("Deleveled")` should return `True` as character case should be ignored, resulting in `"deleveled"`, which is a palindrome since it reads the same backward and forward.

``` python
class Palindrome:

    @staticmethod
    def is_palindrome(word):
        return None

print(Palindrome.is_palindrome('Deleveled'))
``` 

<details><summary>Answer</summary>

``` python
class Palindrome:

    @staticmethod
    def is_palindrome(word):
        lower = word.lower()
        return lower == lower[::-1]

print(Palindrome.is_palindrome('Deleveled'))
``` 

</details>
