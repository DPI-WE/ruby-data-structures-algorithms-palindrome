
# Check if a String is a Palindrome 🔁

- [video](https://youtu.be/p47demc6huc)

## The Problem
Write a function that:

- Takes a string as input.
- Considers only alphanumeric characters and ignores case sensitivity.
- Checks if the given string is a palindrome (reads the same backward as forward).
- Returns true if the string is a palindrome and false otherwise.
- Does not use the `String#reverse` method 😅.

## Understand the Problem
Let's start with simple examples to get you comfortable with string manipulation and the concept of palindromes.

- Consider the following strings. Can you identify the strings that are palindromes? (according to the rules outlined above)
- "A man, a plan, a canal: Panama"
  - Correct. If we ignore everything but alphanumeric characters and case sensitivity, it reads the same backward as forward. This string is a palindrome.
- "race a car"
  - Incorrect. Applying the same rules, it does not read the same backward and forward, so it is not a palindrome.
- "race car"
  - Correct. It read the same forward as backward. This string is a palindrome.
- "palindrome"
  - Incorrect. The word "palindrome" is spelled "emordnilap" backwards.
{: .choose_all #problem_example title="Can you identify the strings that are palindromes?" points="1" answer="[1,3]" }

Keep these examples in mind as we proceed with the coding task. Your function should work with any string input, following the rules outlined above.

## Think Aloud
When approaching this problem, verbalize your thought process. Start by considering how to iterate through the string from both ends simultaneously, comparing characters. Consider what it means for characters to "match" under our criteria (alphanumeric and case-insensitive).

## Test Your Code
```ruby
strings = [
  "A man, a plan, a canal: Panama",
  "race a car",
  "No lemon, no melon"
]

string = strings.sample
# write your function using this method
def palindrome?(string)

end

puts palindrome?(string)
```
{: .repl #string_palindrome title="Check if a String is a Palindrome" readonly_lines="[1,2,3,4,5,6,7]"}

```ruby
describe "Check if a String is a Palindrome" do
  it "returns true for 'A man, a plan, a canal: Panama'" do
    expect(palindrome?("A man, a plan, a canal: Panama")).to eq(true)
  end
end
```
{: .repl-test #string_palindrome_test_1 for="string_palindrome" title="String Palindrome returns true for a valid palindrome" points="1"}

```ruby
describe "Check if a String is a Palindrome" do
  it "returns false for 'race a car'" do
    expect(palindrome?("race a car")).to eq(false)
  end
end
```
{: .repl-test #string_palindrome_test_2 for="string_palindrome" title="String Palindrome returns false for a non-palindrome" points="1"}

```ruby
describe "Check if a String is a Palindrome" do
  it "returns true for 'No lemon, no melon'" do
    expect(palindrome?("No lemon, no melon")).to eq(true)
  end
end
```
{: .repl-test #string_palindrome_test_3 for="string_palindrome" title="String Palindrome correctly handles case insensitivity and non-alphanumeric characters" points="1"}

```ruby
describe "Check if a String is a Palindrome" do
  before(:each) do
    # Temporarily override the String#reverse method
    class String
      alias_method :original_reverse, :reverse
      def reverse
        raise "String#reverse is not allowed"
      end
    end
  end

  after(:each) do
    # Restore the original String#reverse method
    class String
      alias_method :reverse, :original_reverse
    end
  end

  it "does not use String#reverse for 'A man, a plan, a canal: Panama'" do
    expect { palindrome?("A man, a plan, a canal: Panama") }.not_to raise_error
  end
end
```
{: .repl-test #string_palindrome_test_4 for="string_palindrome" title="String palindrome does not use String#reverse" points="1"}

## Tips and Clues for Solving the Problem
- **Two Pointer Technique**: Start with two pointers, one at the beginning of the string and one at the end. Increment and decrement these pointers respectively as you iterate through the string, comparing characters.
- **String Manipulation**: Consider using Ruby's string manipulation methods to ignore non-alphanumeric characters and handle case sensitivity. Methods like gsub and downcase can be very helpful.
- **Edge Cases**: Don't forget to consider edge cases, such as empty strings or strings with only one character.

## Quiz

- What does the two-pointer technique primarily provide in string manipulation problems?
- A method to compare the beginning and end of a string simultaneously
  - Correct! The two-pointer technique is especially useful for comparing characters from both ends of a string, moving towards the center.
- A way to sort characters within the string
  - Incorrect. While the two-pointer technique is versatile, it's not primarily used for sorting within this context.
- A tool for encoding strings
  - Incorrect. The focus here is on comparison and manipulation, not encoding.
- A structure for organizing hierarchical data within a string
  - Incorrect. The two-pointer technique is about comparison, not organizing data hierarchically.
{: .choose_best #two_pointer_use title="What does the two-pointer technique primarily provide in string manipulation problems?" points="1" answer="1" }

- In Ruby, which method can be used to ignore non-alphanumeric characters in a string?
- `gsub`
  - Correct! The gsub method can be used with a regular expression to replace non-alphanumeric characters with an empty string, effectively ignoring them.
- `strip`
  - Incorrect. strip removes whitespace from the beginning and end of a string, not non-alphanumeric characters.
- `split`
  - Incorrect. split divides a string into an array of substrings, not directly related to filtering characters.
- `match`
  - Incorrect. match is used to find portions of a string that match a regular expression, not to ignore characters.
{: .choose_best #ignore_non_alphanumeric title="In Ruby, which method can be used to ignore non-alphanumeric characters in a string?" points="1" answer="1" }

- Which best describes a palindrome?
- A string that contains only letters
  - Incorrect. A palindrome's defining feature is its ability to read the same backward as forward, not its character content.
- A string that reads the same backward and forward
  - Correct! This is the defining characteristic of a palindrome.
- A string that has an even number of characters
  - Incorrect. A palindrome can have either an even or odd number of characters.
- A string that consists of repeating characters
  - Incorrect. While some palindromes may have repeating characters, this is not a requirement.
{: .choose_best #palindrome_definition title="Which best describes a palindrome?" points="1" answer="2" }

## Conclusion
In this lesson, we've delved into the challenge of determining whether a string is a palindrome. By employing techniques such as the two-pointer method and string manipulation, and by considering case sensitivity and alphanumeric characters, we've provided you with a comprehensive toolkit for addressing similar string-related problems in your coding endeavors.
