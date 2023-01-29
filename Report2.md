  # Part1
  ```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            if (str == null || str.equals(""))
            {
                return String.format("No string");
            }
            else
            {
                return String.format("%s",str);
            }
        }  
        else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    str += parameters[1];
                    str += "\n";
                    return String.format(str );
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing string");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
    
}
  ```
  ![Image](Image1.png)
  In the first picture, I call the method ```handleRequest```. My program have the setting that it must detect ```/add-message?s=``` before input the string we want to add, which means that if there do not have ```/add-message?s=``` it won't add the string and would goes to the other output that we are not expected. After the program detecting ```/add-message?s=```, I make the ```parameters[1]``` become "Hello". Here I add the ```Hello ``` to  ```str```, ```str```  become ```Hello\n```. It acctually finish the thing we expected what it should do.
  ![Image](Image2.png)
    In the second picture, I call the method ```handleRequest``` too. I make the ```parameters[1]``` become "How are you". Here I add the ```How are you ``` to  ```str```, ```str```  become ```Hello\nHow are you\n```. By the way, my program have the setting that it must detect ```/add-message?s=``` before input the string we want to add, which means that if there do not have ```/add-message?s=``` it won't add the string and would goes to the other output that we are not expected.  It acctually finish the thing we expected what it should do.
  # Part2
  # Part3
