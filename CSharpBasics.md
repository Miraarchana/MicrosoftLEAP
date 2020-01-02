C# Essential 1:


*C# interactive*
1. to get the result of an expression, dont end the line with ;

*Declaring variables:*
2. implicit typing- supports untyped or weakly typed language

''' eg., var stringFirst = "This is a String";
      stringFirst
	"This is a String"
'''
3. unlike weak typing language (JS) "" represents string and '' represents char

*Built-in data types:*
primitive types: types that cannot be deconstructed into 
4. int - signed integer
   uint - unsigned integer (double the max value to use larger positive integer value)
   
 '''eg., >int bigInt = int.MAX_VALUE;
      >uint positiveInt = uint.MAX_VALUE;
      >bigInt
      2147483647
      >positiveInt
      4294967295
 '''
short, long, float
5. convert ambiguous assignment to unambiguous.

>float pie = 3.14;
error: literal of type double cannot be implicitly converted to type 'float'
>float pie = 3.14f;

*Everything is an Object:*

6. all data types are treated as an Object with collection of static and member variables

 >int.Parse("15")
 15
 >var test ="abcde";
 >test.ToUpper()
 "ABCDE"
 
*Working with Strings:*

7. Trim,TrimEnd,TrimeStart
8. ToUpper(),ToLower()
challenge: 
uppercase string begining at 24 to second attribute from end
remove trailing or leading spaces.
> var challenge ="  Text processing in C# is really great  ";
>challenge.Trim().SubString(24, challenge.Trim().Length-25).ToUpper().Trim()
"REALLY GREAT"
>
9. String concatenation - 
'''
      >var sb = new StringBuilder();
      >sb.Append("aa");
      >sb.Append("bb");
      >sb.ToString()
      "aabb"
      >sb =new StringBuilder();
      >sb.AppendLine("aabb");
      >sb.AppendLine("dsfgdfG");
      >sb.ToString()
      "aabb\r\ndsfgdfG\r\n"
'''
10. string formatter- string.Format()
format string with locale setting

11.PArsing strings
'''
    >int.Parse("14")
    14
    >int.Parse("12,234")
    Input string was not in a correct format..

    >var test = "12,234";
    >int.Parse(test.Replace(",",""))
    12234
'''
int.TryParse(str,out)- will attempt to parse, if it fails exception is not thrown. uniqueness of TryParse() is its return has two parts.
out variable is set in case of successful execution of TryParse(). it returns a boolean and its out variable holds int.
'''
   >int result;
   >int.TryParse("12,234",out result)
   false
   >result
   0
   >int.TryParse("12234",out result)
   true
   >result
   12234
'''
