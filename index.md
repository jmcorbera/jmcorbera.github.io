# Portfolio
---

## <b> SOA </b>

## Service Oriented Architecture

SOA (Service Oriented Architecture) It is a service oriented architecture paradigm. It defines a way to make software components reusable and interoperable through service interfaces.
SOA represents an important stage in the evolution and integration of applications.
Each service in an SOA embeds the code and data necessary to execute a complete business logic function. Service interfaces provide loose coupling, without the need to know how they are implemented underneath, reducing dependencies between applications.
This "interface" is a service contract between the service provider and the service consumer. Applications behind the service interface can be written in Java, Microsoft .Net, Cobol, or any other programming language.
Services are exposed using standard network protocols, such as Simple Object Access Protocol (SOAP)/HTTP or Restful HTTP (JSON/HTTP), to send requests to read or change data.
### SOAP (Simple Object Access Protocol)
SOAP services generally work through the HTTP protocol, which is the most common when we invoke a Web Service, however, SOAP is not limited to this protocol, but can be sent by FTP, POP3, TCP, Messaging Queues (JMS , MQ, etc) .
SOAP only supports XML format.
### REST (REpresentational State Transfer)
REST is a much more flexible technology that transports data through the HTTP protocol, this allows you to use the various methods that HTTP provides to communicate, such as GET, POST, PUT, DELETE, PATCH and, at the same time, uses the response codes HTTP natives (404,200,204,409).
REST supports XML, JSON, Binaries (images, documents), Text, etc. (the advantage of using JSON is that it is interpreted naturally by JavaScript)

---

## <b>.Net 5 </b>

## Implementing API Rest

With this implementation, the aim is to generate a structural model for a API REST application using .NET 5. For this, a layered architecture is created and the Repository Pattern is used.

<img src="images/APIRestArchitecture.png?raw=true"/>

<i>All the source codes of this implementation can be found in the GitHub repository.</i>

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/jmcorbera/ApiRestNetCore.git)

---

## <b>.Net Framework</b> 

## Implementing WCF SOAP Service

Here we are going to show a basic architecture implementation of a service SOAP with WCF, the tool included in the .NET Framework, to be hosted in IIS/WAS. For this, a layered architecture is created and the Dependency Injection (DI) Pattern is used.

<br><img src="images/WCFArquitecture.png?raw=true"/><br>

<i>All the source codes of this implementation can be found in the GitHub repository.</i>

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/jmcorbera/WCFService.git)

---

## <b> C# Exceptions Handling</b>

## Exception Handling Best Practices

Exceptions allow an application to transfer control from one part of the code to another. When an exception is thrown, the current flow of the code is interrupted and handed back to a parent try catch block. C# exception handling is done with the follow keywords:

<b>try</b> ??? A try block is used to encapsulate a region of code. If any code throws an exception within that try block, the exception will be handled by the corresponding catch.

<b>catch</b> ??? When an exception occurs, the catch block of code is executed. This is where you are able to handle the exception, log it, or ignore it.

<b>finally</b> ??? The finally block allows you to execute certain code if an exception is thrown or not.

<b>throw</b> ??? The throw keyword is used to actually create a new exception that is the bubbled up to a try catch finally block. 

```
public code GetLengthRatio(string s1, string s2)
    var s1Length = s1.Length; // Can throw NullReferenceException if s1 is null
    var s2Length = s2.Length; // Can throw NullReferenceException if s1 is null

    var ratio = s1Length / s2Length;// Can throw DivideByZeroException if s2 is empty

    return ratio;
}
```
The code written above can throw at least 2 different exceptions: *`NullReferenceException`* and *`DivideByZeroException`*

### Write code that handles exceptions

```
public code GetLengthRatio(string s1, string s2)
try
{
    double ratio;

    var s1Length = s1.Length;
    var s2Length = s2.Length;

    var ratio = s1Length / s2Length;
}
catch(NullReferenceException ex)  // Handling NullReferenceException
{
    Console.WriteLine(string.Format("An empty parameter was passed - Exception : {0}", ex.Message));
    ratio = 0.0;
}
catch (DivideByZeroException ex) // Handling DivideByZeroException
{
    Console.WriteLine(string.Format("s2 is empty! - Exception : {0}", ex.Message));
    ratio = double.MaxValue;
}
catch (Exception ex) // Handling all other exceptions
{
    Console.WriteLine(string.Format("Unknown error - Exception : {0}", ex.Message));
    ratio = 0.0;
}

    return ratio;
}
```

<b>try catch blocks chain</b> - <i><b>go from the most specific exception to the most general</i></b>.
When an exception occurs inside the try block, CLR first checks it against the first catch block; if it fits, that catch block is executed. If the first catch block doesn't match, it checks the second catch block, then the third, and so on, ending with the last catch block. 

How would I know which exceptions the code throws? the answer is... <b>Documentation</b>. e.g. for <b>int.Parse</b> You can find it [here](https://docs.microsoft.com/en-us/dotnet/api/system.int32.parse?view=netframework-4.7.2?target=_blank)


### try catch hierarchy function

```
public static void Main()
{
    try
    {
        SomeMethod();
    }
    catch (Exception ex) // The exception is handled here
    {
        Console.WriteLine(ex);
    }
}

public static void SomeMethod() // The exception "jumps out" from here
{
    throw new ArgumentException("Argument is wrong!");
}
```
In the code written above, when we call SomeMethod() function, the program could terminate because of an unhandled exception if we don??t handle the exception call,  by adding a try - catch block in the Main function, we fix this problem..

When an exception occurs, it looks for the closest try - catch block to the line where the exception occurred. If there is no try - catch nearby, it 'jumps out' from the function and looks for the try - catch in the function that called the current one, and so on, until it gets to the highest in the hierarchy function ( Main ), and if that one doesn't have a try-catch for this exception, your program will crash 

We'll illustrate How it??s work.

<br><img src="images/try_catch_hierarchy_function.png?raw=true"/><br>

### Third block called finally

When we create an object of our class or create an int variable, all the resources for those are going to be managed by C#, or more precisely, CLR ( Common Language Runtime ). But if you start working with a world outside of your application; for example, files on a hard disk drive; then CLR will not help in clearing all the resources, and you need to call special functions to do this.

A try , catch construction has a third block, called finally . It's used to clean up any resources that were allocated in the try block. It can be used without a catch block ( try - finally ), or with it ( try - catch - finally ). 

The code in finally (almost) always executes. That's why the finally block is used for deallocation of the system resources.

```
System.IO.StreamReader fileReader = new System.IO.StreamReader("anyFile.txt");

int nextCharacter;
try
{
    // Trying to read from file
    nextCharacter = fileReader.Read();
}
catch (System.IO.IOException e)
{
    // Handle an IOException error
    Console.WriteLine(string.Format("Error reading from anyFile.txt - Exception : {0}", ex.Message));
}
finally
{
    if (fileReader != null)
    {
        // Close the file! Cleans up resources in operating system.
        fileReader.Close();
    }
}
// Do something with nextCharacter
```

---

<!-- 

-- item 4 - C# Custom Exception Types

-- item 5 - C# Exception Logging Best Practices -->

<!-- Remove above link if you don't want to attibute -->
