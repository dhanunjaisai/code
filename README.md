# code
this is code


*) If you have a predicate method, it's customary to name it with a trailing question mark, e.g. palindrome?.

*) Boolean expressions evaluate to a boolean, so you don't need to explicitly return true or false. Hence a short idiomatic version would be

def palindrome?(str)
  str == str.reverse
end
*) Since Ruby's classes are open, you could add this to the string class:

class String
  def palindrome?
    self == self.reverse
  end
end
*) If you don't want to monkey-patch String, you can directly define the method on single object (or use a module and Object#extend):

foo = "racecar"
def foo.palindrome?
  self == self.reverse
end
*) You might want to make the palindrome check a bit more complex, e.g. when it comes to case or whitespace, so you are also able to detect palindromic sentences, capitalized words like "Racecar" etc.

pal = "Never a foot too far, even."
class String
  def palindrome?
    letters = self.downcase.scan(/\w/)
    letters == letters.reverse
  end
end
pal.palindrome? #=> true
