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

<br><img src="images/APIRestArchitecture.png?raw=true"/><br>

<i>All the source codes of this implementation can be found in the GitHub repository.</i>

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/jmcorbera/ApiRestNetCore.git)<br> <br>
---
## <b>.Net Framework</b> 

## Implementing WCF SOAP Service

Here we are going to show a basic architecture implementation of a service SOAP with WCF, the tool included in the .NET Framework, to be hosted in IIS/WAS. For this, a layered architecture is created and the Dependency Injection (DI) Pattern is used.

<br><img src="images/WCFArquitecture.png?raw=true"/><br>

<i>All the source codes of this implementation can be found in the GitHub repository.</i>

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/jmcorbera/WCFService.git)
---
<!-- Remove above link if you don't want to attibute -->
