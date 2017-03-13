# IceBreakRestServer
A super tiny HTTP server for JAVA.


## Introduction

IceBreak REST server Is a tiny stand alone server side HTTP stack you can embed in your JAVA program. Just drop one small jar file into you project and you are golden.

Sometimes you just need to be able to get request and send response back by the HTTP protocol. In these cases it will be totally overkill to user i.e. a Tomcat or Glassfish server. What you need is a small Representational State Transfer - REST server http://en.wikipedia.org/wiki/Representational_State_Transfer


## Details

The aim is to utilize Java classes server side i.e. into PHP, CGI etc. simply by issuing server side HTTP request on the loop-back port, and their by gaining performance since the class loader is only invoke once - you don't have to jump in and out of the java environment.

We have used this tiny server for integrating iText, NemID among other java projects to incorporate into a non-Java project like IceBreak-RPG , C#, RPG-CGI, PHP.

The following code illustrates how easy it is to use:

```
import IceBreakRestServer.*; // Drop this jar-file into you project
import java.io.IOException;

public class Simple {

  public static void main(String[] args) {

    IceBreakRestServer rest;   // Declare the HTTP server class

    try { 
      rest  = new IceBreakRestServer();  // Instantiate it once

      while (true) {
        rest.getHttpRequest();                  // wait for any HTTP request 
        String name = rest.getQuery("name", "N/A");
        rest.write("Hello world - the 'name' parameter is: " + name );
      }
    }
    catch (IOException ex) {
      System.out.println(ex.getMessage());
    }
  }
}
```
