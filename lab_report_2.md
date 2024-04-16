# Lab Report 2
## Part 1: ChatServer
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // List to store strings.
    ArrayList<String> words = new ArrayList<String>();

    // Handle requests to the server
    public String handleRequest(URI url) {
        // Root path provides general info
        if (url.getPath().equals("/")) {
            String formattedString = words.toString()
                .replace(",", "\n")
                .replace("[", "")
                .replace("]", "")
                .trim();   
            return formattedString;
        } else if (url.getPath().contains("/add-message")) {
            // Extract query from URL and add to list
            String[] params = url.getQuery().split("=");
            String user = params[2];
            String[] message_list = params[1].split("&");
            String message = message_list[0];
            String text = user + ": " + message;
            words.add(text);
            String formattedString = words.toString()
                .replace(",", "\n")
                .replace("[", "")
                .replace("]", "")
                .trim();   
            return formattedString;
        }
        return "404 Not Found!";
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
## Input 1:
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/671d3bde-7e64-4df2-bb3e-b5474d0a95e8)
- The methods called in my code include `handleRequest()`,  `public String handleRequest(URI url)` and other basic java methods within Handler (`getQuery()`, `contains()`, `toString()`, `replace()`, `trim()`, etc.)
- Relevant arguments to those methods:
    - `replace(",", "\n")` to turn commas into new lines, etc. The rest to reformat the list into the desired visual
    - `url.getQuery().split("=")` and `url.getQuery().split("&")` for splitting at different characters to extract preferred values
    - `url.getPath().contains("/add-message")` and `url.getPath().contains("/")` to see whether or not to add a user: message text
- Relevant fields of the class includes:
    - `words` which is a list of all user: message strings.
    -  `params`, `user`, `message_list`, `message`, `text`, for finding the user and their message
    -  `formattedString` to print words in the desired way on the website
- How do the values of any relevant fields of the class change from this specific request?
    - `text` gets appended to 'words'
    - `params`, `user`, `message_list`, `message`, `text`, `words`, `formattedString` all get altered by the specific request, namely by the username and their message as identified in the prompt.
## Input 2:
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/8eee43f2-2dbd-490b-aedc-ae83952b921b)
- The methods called in my code include `handleRequest()`,  `public String handleRequest(URI url)` and other basic java methods within Handler (`getQuery()`, `contains()`, `toString()`, `replace()`, `trim()`, etc.)
- Relevant arguments to those methods:
    - `replace(",", "\n")` to turn commas into new lines, etc. The rest to reformat the list into the desired visual
    - `url.getQuery().split("=")` and `url.getQuery().split("&")` for splitting at different characters to extract preferred values
    - `url.getPath().contains("/add-message")` and `url.getPath().contains("/")` to see whether or not to add a user: message text
- Relevant fields of the class includes:
    - `words` which is a list of all user: message strings.
    -  `params`, `user`, `message_list`, `message`, `text`, for finding the user and their message
    -  `formattedString` to print words in the desired way on the website
- How do the values of any relevant fields of the class change from this specific request?
    - `text` gets appended to 'words'
    - `params`, `user`, `message_list`, `message`, `text`, `words`, `formattedString` all get altered by the specific request, namely by the username and their message as identified in the prompt.
 
## Part 2
1. <img width="321" alt="image" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/3b3ac94a-138a-4ba9-a382-2122882b59e5">
2. ![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/a48ac71b-f5d7-4571-a2bd-1512814dfb17)
3. ![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/f678e701-184c-4435-bf8b-6b3d38189063)

## Part 3
Something I learned from lab 3 is how to create keys for ssh. In my lab, I ssh into my lab's computer/nodes often and knew of passkeys, but never knew how to make them.

