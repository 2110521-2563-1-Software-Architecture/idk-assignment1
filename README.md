# idk-assignment1
## idk Team Members
* 6030026021 Kritsana Khankaew
* 6030033321 Kongtap Arunlakvilart
* 6030038521 Kantorn Chitchuen
* 6030478021 Melvin Macaranas
* 6030482421 Yodsavee Lertthirathanaphong
* 6031015221 David Tumcharoen

## Assignment #1: gRPC and REST API implementation

Things to be delivered:
1. Screenshots of Swagger for your APIs in 2.
   ![alt text][swagger]
   ![alt text][swagger01]
   ![alt text][swagger02]
   ![alt text][swagger03]
   ![alt text][swagger04]
2. Source codes of 2 and 3.
   * Server side
   ![alt text][code]
   * Client side
   ![alt text][code2]
   ![alt text][code3]
3. Compare how to call the methods based on gRPC and REST API side-by-side, e.g. in a Table format as shown below. 

    | Functions | gRPC | REST API |
    |--|--|--|
    | List books | client.list({}, function(error, books) {<br>&nbsp;&nbsp;printResponse(error, books);<br>}); | `axios.get('http://localhost:3000/book/list')`  |
    | Insert books | client.insert(book, function(error, empty) {<br>&nbsp;&nbsp;printResponse(error, empty);<br>}); | `axios.post('http://localhost:3000/book/insert', book)` |
    | Get books | client.get({ id: parseInt(id) }, function(error, book) {<br>&nbsp;&nbsp;printResponse(error, book);<br>}); | ```axios.get(`http://localhost:3000/book/${bookId}`, book)``` |
    | Delete books | client.delete({ id: parseInt(id) }, function(error, empty) {<br>&nbsp;&nbsp;printResponse(error, empty);<br>}); | ```axios.delete(`http://localhost:3000/book/${bookId}`)``` |
    | Watch books | client.watch({}) | - |
4. What are the main differences between REST API and gRPC?
   - gRPC uses HTTP/2 which is much faster than HTTP/1.1 used in REST by default

   - gRPC uses Protocol buffer to serialize payload data, which is binary and smaller, while REST uses JSON, which is larger.

   - The API contract in gRPC is strict, and required to be clearly defined in the proto file. While in REST, it’s often loose and optional. We can define it via OpenAPI if we want, but it’s not mandatory.

   - Code generation is built-in in gRPC with the help of protocol buffer compiler. While in REST, we must use third-party tool like OpenAPI and Swagger.

   - Streaming is bidirectional in gRPC, while only 1 way request from client to server in REST.

   - REST is fully supported by all browsers, the support for gRPC is limited and required gRPC-web with a proxy layer to convert between HTTP/1 and HTTP/2.

5. What is the benefits of introduceinterface in front of the gRPC and REST API of the book services.
   - Hiding the code from user
   - Understanding the code easier
   - Maintaining the code easier
6. Based on the introduced interface, compare how to call the methods based on gRPC and REST API side-by-side, e.g. in a
Table format as shown below. 

    | Functions | gRPC | REST API |
    |--|--|--|
    | List books | listBooks(); |  bookData.getBookList(); |
    | Insert books |insertBook(int id, str title, str author);  | bookData.insertBook(req.body); |
    | Get books | getBook(int id); |  bookData.getBookById(req.params.bookId) |
    | Delete books | deleteBook(int id); | bookData.deleteBookById(req.params.bookId); |
    | Watch books | watchBooks(); | - |
7. Draw a component diagram representing the book services with and without interfaces. 

   ![alt text][comp]
   
[code]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Source_Code.png "Server"
[code2]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/code_2.png "Client1"
[code3]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/code_3.png "Client2"
[comp]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Component_Diagram_update.png "Component Diagram"
[swagger]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Swagger.png "Swagger"
[swagger01]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Swagger01.png "Swagger01"
[swagger02]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Swagger02.png "Swagger02"
[swagger03]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Swagger03.png "Swagger03"
[swagger04]: https://raw.githubusercontent.com/2110521-2563-1-Software-Architecture/idk-assignment1/master/Swagger04.png "Swagger04"
