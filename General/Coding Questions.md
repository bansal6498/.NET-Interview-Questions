## Most Asked Coding Questions
### Check if a string is a Palindrome
```csharp
using System;
class Program
{
    // Function to check if a string is a palindrome
    public static bool IsPalindrome(string str)
    {
        int start = 0;
        int end = str.Length - 1;
        // Check characters from start and end until they meet
        while (start < end)
        {
            // If characters are different, it's not a palindrome
            if (str[start] != str[end])
            return false;
            start++;
            end--;
        }
        return true; // It is a palindrome
    }
    static void Main(string[] args)
    {
        string input = "madam"; // You can test with other strings
        bool result = IsPalindrome(input);
        if (result)
        Console.WriteLine($"'{input}' is a palindrome.");
        else
        Console.WriteLine($"'{input}' is not a palindrome.");
    }
}
```
This code defines a method `IsPalindrome` that compares characters from the beginning (start) and the end (end) of the string. If any characters don't match, it returns `false`. Otherwise, it returns `true` indicating the string is a palindrome.
The Main method tests the function using a sample string ("madam").
### Find Palindromes in a Sentence (Finding Palindromes from a String):
```csharp
using System;
using System.Collections.Generic;
class Program
{
    // Function to check if a string is a palindrome
    public static bool IsPalindrome(string str)
    {
        int start = 0;
        int end = str.Length - 1;
        while (start < end)
        {
            if (str[start] != str[end])
            return false;
            start++;
            end--;
        }
        return true;
    }
    // Function to find palindromes in a sentence
    public static List<string> FindPalindromes(string sentence)
    {
        List<string> palindromes = new List<string>();
        string[] words = sentence.Split(' '); // Split sentence into words
        foreach (string word in words)
        {
            // Check if word is a palindrome and add to the list
            if (IsPalindrome(word.ToLower())) // Convert to lowercase for case-insensitive check
            {
                palindromes.Add(word);
            }
        }
        return palindromes;
    }
    static void Main(string[] args)
    {
        string sentence = "Madam Arora teaches malayalam";
        List<string> palindromes = FindPalindromes(sentence);
        Console.WriteLine("Palindromes in the sentence:");
        foreach (string palindrome in palindromes)
        {
            Console.WriteLine(palindrome);
        }
    }
}
```
-   `IsPalindrome` Function: This checks if a single word is a palindrome.
-   `FindPalindromes` Function: This splits the input sentence into words and uses `IsPalindrome` to check each word. If a word is a palindrome, it's added to a list of palindromes.
-   **Case-insensitive check**: Converts each word to lowercase before checking to ensure the check is case-insensitive (e.g., "Madam" is treated the same as "madam").
####  OUTPUT
For the input string "Madam Arora teaches malayalam", the output will be:
```csharp
Palindromes in the sentence:
Madam
Arora
malayalam
```
### Swap Numbers Without Using a Temporary Variable:
```csharp
using System;
class Program
{
    static void Main(string[] args)
    {
        // Input two numbers
        Console.Write("Enter first number: ");
        int num1 = Convert.ToInt32(Console.ReadLine());
        Console.Write("Enter second number: ");
        int num2 = Convert.ToInt32(Console.ReadLine());
        // Display before swapping
        Console.WriteLine($"Before swapping: num1 = {num1}, num2 = {num2}");
        // Swap using arithmetic operations
        num1 = num1 + num2; // Step 1: num1 becomes the sum of both numbers
        num2 = num1 - num2; // Step 2: num2 becomes the original num1 (num1 - num2)
        num1 = num1 - num2; // Step 3: num1 becomes the original num2 (num1 - num2)
        // Display after swapping
        Console.WriteLine($"After swapping: num1 = {num1}, num2 = {num2}");
    }
}
```
The numbers are swapped using basic arithmetic operations:
-   First, `num1` is assigned the sum of both `num1` and `num2`.
-   Then, `num2` is updated by subtracting the new `num1` (which is the sum) from num2, effectively giving the original `num1`.
-   Finally, `num1` is updated by subtracting the new `num2` from `num1`, giving the original num2.
#### OUTPUT
```csharp
Enter first number: 5
Enter second number: 10
Before swapping: num1 = 5, num2 = 10
After swapping: num1 = 10, num2 = 5
```
### LINQ for Duplicates
```csharp
var duplicates = arr.GroupBy(x => x)
                    .Where(g => g.Count() > 1)
                    .Select(g => g.Key);
```
### Reverse Linked List
```csharp
Node prev = null, curr = head;
while(curr != null) {
    var next = curr.Next;
    curr.Next = prev;
    prev = curr;
    curr = next;
}
head = prev;
```
### First Non-Repeating Character
```csharp
var ch = str.GroupBy(c => c)
            .Where(g => g.Count() == 1)
            .Select(g => g.Key)
            .FirstOrDefault();
```
### Pagination with EF Core
```csharp
var pageSize = 10;
var data = db.Users
             .Skip((page-1)*pageSize)
             .Take(pageSize)
             .ToList();
```
#### Write a C# code you have a string "Priyanshu Bansal" Write it in reverse order but if the alphabet is vowel then it should print as Capital and if it is a consonent it should print as lower case and space should be as it is.
**Answer:**
```csharp
using System;
using System.Linq;

class Program
{
    static void Main()
    {
        string input = "Priyanshu Bansal";
        string result = ReverseWithCustomCase(input);
        Console.WriteLine(result);
    }

    static string ReverseWithCustomCase(string input)
    {
        char[] vowels = { 'a', 'e', 'i', 'o', 'u' };
        string reversed = new string(input.Reverse().ToArray());

        char[] output = new char[reversed.Length];
        for (int i = 0; i < reversed.Length; i++)
        {
            char currentChar = reversed[i];
            if (vowels.Contains(char.ToLower(currentChar)))
            {
                output[i] = char.ToUpper(currentChar);
            }
            else if (char.IsLetter(currentChar))
            {
                output[i] = char.ToLower(currentChar);
            }
            else
            {
                output[i] = currentChar; // Keep spaces as they are
            }
        }

        return new string(output);
    }
}
```
