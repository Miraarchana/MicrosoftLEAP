C# Essential 1:


**C# interactive - Getting Started**
1. to get the result of an expression, dont end the line with ;

*Declaring variables:*
2. implicit typing- supports untyped or weakly typed language

``` eg., var stringFirst = "This is a String";
      stringFirst
	"This is a String"
```
3. unlike weak typing language (JS) "" represents string and '' represents char

*Built-in data types:*
primitive types: types that cannot be deconstructed into 
4. int - signed integer
   uint - unsigned integer (double the max value to use larger positive integer value)
   
 ```
 eg., >int bigInt = int.MAX_VALUE;
      >uint positiveInt = uint.MAX_VALUE;
      >bigInt
      2147483647
      >positiveInt
      4294967295
```
short, long, float
5. convert ambiguous assignment to unambiguous.
```
>float pie = 3.14;
error: literal of type double cannot be implicitly converted to type 'float'
>float pie = 3.14f;
```
*Everything is an Object:*

6. all data types are treated as an Object with collection of static and member variables
```
 >int.Parse("15")
 15
 >var test ="abcde";
 >test.ToUpper()
 "ABCDE"
``` 
*Working with Strings:*

7. Trim,TrimEnd,TrimeStart
8. ToUpper(),ToLower()
challenge: 
uppercase string begining at 24 to second attribute from end
remove trailing or leading spaces.
```
> var challenge ="  Text processing in C# is really great  ";
>challenge.Trim().SubString(24, challenge.Trim().Length-25).ToUpper().Trim()
"REALLY GREAT"
>
```
9. String concatenation - 
```
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
```
10. string formatter- string.Format()
format string with locale setting

11.PArsing strings
```
    >int.Parse("14")
    14
    >int.Parse("12,234")
    Input string was not in a correct format..

    >var test = "12,234";
    >int.Parse(test.Replace(",",""))
    12234
```

int.TryParse(str,out)- will attempt to parse, if it fails exception is not thrown. uniqueness of TryParse() is its return has two parts.
out variable is set in case of successful execution of TryParse(). it returns a boolean and its out variable holds int.

```
   >int result;
   >int.TryParse("12,234",out result)
   false
   >result
   0
   >int.TryParse("12234",out result)
   true
   >result
   12234
```
*Math in C#:*

12. +,-,*,/,%,++,-- operators and other Math functions like abs,pow,round,floor,ceiling

*Constants and enumeration*

13. constants - const float pi =3.14f;
```
>enum weekDays {Monday, Tuesday, Wednesday, Thursday, Friday };
>var someDays = weekDays.Monday;
```
we can also set the value of each item in enum explicitly like Monday=1, Tuesday=3..

*Date and Time*

14. DateTime.Now -	current date and time
    TimeSpan - is used for arithmetic operations
    
    ```
    >var birthday = new DateTime(1967,10,2);
    >var difference = DateTime.Now - birthday;
    >difference
    [18455:34:34:33.23246510]
    >difference.Days
    18023
    ```
    gives the number days on earth since birth for a birthdate
    
    ```
    >var dateTime = new DateTime(2010,10,18,9,51,32);
    ```
    dateTime.AddMinute() - positive number indicates addition, negative number indicates subtraction
    dateTime.ToFileTime() - outputs a timestamp for file processing
    dateTime.ToLongDateString()
    [Wednesday 18, October, 2010]


**Working with Classes**

1. Creating a class
	File>New>Project -> ClassLibrary(.dll) - VC++
2. Namespaces
	similar to package in Java
3. Auto-properties - Automatic property in C# is a property that has backing field generated by compiler. It saves developers from writing primitive getters and setters that just return value of backing field or assign to it
```
public class Dummy
{
    private string _name;//backing field
 
    public string Name
    {
        get { return _name;  }
        set { _name = value;  }
    }
}
```
can be written as
```
public class Dummy
{
    public string Name { get; set; }
}
```
4. Backing field - getter setter
5. Encapsulation and access specifier

    public  - seen outside of the class
    private - seen inside of the class
    protected
    internal
    
6. Constructor
	- run immediately when an object is instantiated.
	Hint: editor trick enter 'ctor' and hit tab key twice - creates the default constructor for the class
	constructor access specifier - public
	
7. Creating Methods
	*Common Method block*
	```
	public float AverageOfThreeNumbers(float a, float b, float c){
		return (a+b+c)/3;
	}
	```
	*Function bodied expressions* (new in C# 6)
		- simple method can be concisely written using function bodied expression.
	```
	public float AverageOfThreeNumbers(float a, float b, float c) => (a+b+c)/3;
	```
	*static Methods* - used without instantiation
	

*4. Object-Oriented Features:*
    *Inheritance :*
    ```
    public abstract class Person
    {
    	public string Name {get; set;}
	public string Email {get; set;}
	public abstract float ComputeGradeLevel(); //abstract method - which is rquired to be overridden in all sub class
    }
    
    public class Student : Person
    {
    	public override float ComputeGradeLevel()
	{
		//logic goes here
		return 4.0f;
	}
    }
    
    public class Teacher : Person
    {
    	public override float ComputeGradeLevel()
	{
		//logic goes here
		return 0.0f;
	}
    }
    ```
*Virtual Methods:*
 - If anything that is to be overriden in sub class, we must use Virtual keyword (may be override later - optional), abstract method (must be overridden in all sub classes)

*Interface:*
 - contract between all programmers to implement certain behavior.
 - multiple interfaces can be implemented
 
 *Extension Methods:*
 -  allows you to inject additional methods without modifying , deriving and recompiling the original class.
 - additional method can be added to user defined class, .Net framework classes, or third party classes or interfaces



*C# : Basics 2*

*Array in C#*

- Like in Java, Arrays are tightly coupled with size and type
- to resize an array Array.resize(ref <arrayref>, int size) must be passed
- mulitdimensional array - use case for problems involving analytical programming like spread sheet
``` 
var multi = new int[3, 4] {
. {0,1,2,3 },
. {4,5,6,7 },
. {8,9,10,11 }};
> multi
int[3, 4] { { 0, 1, 2, 3 }, { 4, 5, 6, 7 }, { 8, 9, 10, 11 } }
> multi[2,3]
11
```
- Feature Set  - Language Integrated Query (LINQ) - hook on to any Collection and allows us to use
	implemented as extension classes
	```
	> var listOfNumbers = new int[5] { 1, 2, 3, 4, 5 };
> listOfNumbers.Sum()
15
> listOfNumbers.Average()
3
> listOfNumbers.Where(item => item>=3)
Enumerable.WhereArrayIterator<int> { 3, 4, 5 }
> 
	```
*Dictionary*

```
> var dictWord = new Dictionary<string, string>();
> dictWord.Add("var", "shorthand for variable");
> dictWord.Add("function", "work on data");
> dictWord.Add("variable", "a container for data");
> dictWord.Count
3
> dictWord.Keys
Dictionary<string, string>.KeyCollection(3) { "var", "function", "variable" }
> 
```

*Testing With Assembly*

*Assembly in C#*
An assembly is a file that is automatically generated by the compiler upon successful compilation of every . NET application. It can be either a Dynamic Link Library or an executable file. It is generated only once for an application and upon each subsequent compilation the assembly gets updated.

1. Goto C# Interactive window
2. Use '#r' with the path of the assembly (Solution Explorer > rightclick project> OPen in File Explorer >goto"bin\debug\netstandard2.0\")<assembly name>
	
```
> #r "C:\Users\shara\source\repos\EssentialTraining\EssentialTraining\bin\Debug\netstandard2.0\EssentialTraining.dll"
> var test = new EssentialTraining.ProgrammingLoops();
> test.ForEachLoop()
22
```

*Using() in C#*
The using statement in C# defines a boundary for the object outside of which, the object is automatically destroyed. The using statement is exited when the end of the "using" statement block or the execution exits the "using" statement block indirectly, for example - an exception is thrown.

*Reading a file*
Note: To specify path in C#
we use c:\\temp\\test
instead we can use @"C:\temp\test.txt"

```
private static void ReadTextFile()
        {
            try
            {
                using (var sr = new System.IO.StreamReader(@"C:\temp\test.txt"))
                {
                    string contents = sr.ReadToEnd();
                    Console.WriteLine(contents);
                }

            }
            catch(System.IO.DirectoryNotFoundException ex)
            {
                Console.WriteLine("Could not find a directory");
            }
            catch(System.IO.FileNotFoundException ex)
            {
                Console.WriteLine("Couldnt find the file");
            }
            catch(Exception ex)
            {
                Console.WriteLine("Unknown error occured " + ex.Message);
            }
            finally
            {
                Console.WriteLine("The finally runs all the time");
            }
        }
```
