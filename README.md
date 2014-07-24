#CompletionClient

## Thrift
The [[feature/thrift|https://github.com/Completionary/SockJScompletion/tree/feature/thrift]] branch contains a simple completion client based on Thrift generated javascript code using `--gen js:jquery` and following thrift file:

```
/*
 * Data sent back from the suggestion service
 * @param suggestion
 *            The suggested string (equals 'output' of SuggestionField)
 * @param payload The additional data stored with the suggested term
 *            The format must be like following JSON:
 *              {"href":"$URL","image":"$URL_or_BASE64Image"}
 */
struct Suggestion {
        1: string suggestion;
        //will be a JSON and we have to specify supported base format
        2: string payload;
}

service SuggestionService {
        /**
         * Returns the top k completions of <query> stored in the given index
         */
        list<Suggestion> findSuggestionsFor(1: string index, 2: string query, 3: short k),
}

```


##SockJScompletion


A simple example of how to connect to completion server using sockjs. 

Instead of implementing the server by hand, you might consider to run sockjsproxy (https://bitbucket.org/vladev/sockjsproxy) 
### Data Format
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

