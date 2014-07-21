SockJScompletion
================

A simple example of how to connect to completion server using sockjs. 

Instead of implementing the server by hand, you might consider to run sockjsproxy (https://bitbucket.org/vladev/sockjsproxy) 
## Data Format
This script is intended to speak with a completion server that returns the suggestions in the following format (here we show two suggestions with different image formats):

```
{"suggestionList":
  [
    [ "$Label1",
      "{"img":"data:image/jpg;base64,$imageInBase64", 
        "href":"$URL1"}"
    ],
    ["$Label2",
      "{"img":"$imageURI",
        "href":"$URL2"}"
    ]
  ]
}
```

