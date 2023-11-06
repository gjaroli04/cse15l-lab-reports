# Lab Report 2
***

**Part 1**
My code for StringServer.java:

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

