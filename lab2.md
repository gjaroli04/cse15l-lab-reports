# Lab Report 2
***

**Part 1** <br>

My code for StringServer.java:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.List;

class Handler implements URLHandler {

    List<String> messages = new ArrayList<>();
    int sequence = 1;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            if (query != null && query.startsWith("s=")) {
                String newMessage = sequence + ". " + message;
                messages.add(newMessage);
                sequence++;
                return String.join("\n", messages);
            }
        }
        return "404 Not Found!";
    }
}

class StringServer {
   
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
Screenshot 1 (Adding Hello): <br>
![Image](AddingHello.png)	

* Method called: handleRequest(URI url) in the Handler class is called.
* Relevant arguments: "URI" object representing the URL (http://localhost:4005/add-message?s=Hello) with path "/add-message" and query "s=Hello".
* Relevant fields: 'messages' which is an empty list before the code is ran, and the 'sequence' is 1.
* How the values change: The 'messages' list will have one element added which would be taken from the query: "1.Hello" and "sequece" will increment to 2.

Screenshot 2 (Adding How Are you): <br>
![Image](AddingHowAreYou.png)	

* Method called: handleRequest(URI url) in the Handler class is called.
* Relevant arguments: "URI" object representing the URL (http://localhost:4005/add-message?s=How%20are%20you) with path "/add-message" and query "s=How are you".
* Relevant fields: 'messages' which is a list with an element "1.Hello" from the previous request, and the 'sequence' is 2 due to adding "1.Hello".
* How the values change: The messages list will have two elements: "1. Hello" and "2. How are you", and sequence will increment to 3.

**Part 2** <br>
* The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer): <br>
![Image](PrivateKey.png)	

* The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6): <br>
![Image](PublicKey.png)	

* A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password.
![Image](TerminalInteraction.png)	

**Part 3** <br>

During Week 2, I gained experience in establishing an SSH connection to a remote server using my individual account. Furthermore, I explored the fundamentals of web servers by running a basic Java web server on my own machine. This allowed me to understand concepts such as ports, accessing the server via a web browser, and testing various URL paths and queries to observe the server's responses. Additionally, I collaborated with my peers by connecting by loading their server on my local machine and experimented with testing various URL paths and queries. <br>

In Week 3, I gained experience by running a server on my local computer accessible through the web browser at http://localhost:4000 (where 4000 was my chosen port number). Additionally, I set up convenient access to SSH keys using the 'scp' and 'mkdir' commands for the first time. These two labs offered a range of new insights. Running a server on my local machine was a new experience for me. This allowed me to compare the process of running a server on a remote server and my local machine. I also got a deeper understanding of URL paths and queries and how the server responds to various requests. Furthermore, I learned the functions of the 'scp' command, which ensures secure file copying, and the 'mkdir' command, which enables us to create new directions and structuring within the file system.




























