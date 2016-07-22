# **API Basic**

* Get all books information list:                  GET       /books
* Read a book detailed information by book i:      GET       /books/:isbn
* Add a book to the list:                          POST      /book
* Edit detail information by book id:              PUT       /book/:isbn
* Delete book information by book id:              DELETE    /book/:isbn

When you POST/PUT?DELETE, username&password is needed, they are assigined in the authorization header.

***
# **API error**

When an error occured, HTTP Status Code is 401,404,409,500.

Layout of error:

```
{
    'msg':'error message'
}
```

* 401:  Access denied;
* 404:  Book not found;
* 409:  Parameters conflict;
* 500:  Other error


|Error Message                          |Status Code        |     Error describe
|---------------------------------------|:-----------------:|--------------------------------------------
|Access denied                          |    401            | :username or :password is error
|Book not found                         |    404            | {:id} don't refers to any book
|Name&&author can't be same at same time|    409            | Book name&author conflict
|Isbn should be unique                  |    409            | ISBN conflict
|Author can't be empty                  |    409            | {book[author]} in your parameters is empty
|Isbn can't be empty                    |    409            | {book[isbn]} in your parameters is empty
|Book name can't be empty               |    409            | {book[name]} in your parameters is empty
|Exception                              |    500            | Internal Server Error

***
# **Get books list**

`GET /books`

Return books list, without id&describe, status=200

```
{
    [
        {
          "name": "Rails之道",
          "isbn": "4727011",
          "author": "(美)Obie Fernandez",
          "price": 89,
          "img_url": "https://img3.doubanio.com/mpic/s4282672.jpg",
          "description": "《Rails之道》按照Rails的各个子系统进行组织编排……"
        },
        {
          "name": "Programming Ruby中文版",
          "isbn": "2032343",
          "author": "托马斯",
          "price": 99,
          "img_url": "https://img3.doubanio.com/mpic/s2370875.jpg",
          "description": "《Programming Rudy》(中文版)(第2版)是……"
        }
    ]
}
```

***
# **Get a book message**

`GET  /books/:isbn`

Return a book's information,status=200

```
{
    "name": "Programming Ruby中文版",
    "isbn": "2032343",
    "author": "托马斯",
    "price": 99,
    "img_url": "https://img3.doubanio.com/mpic/s2370875.jpg",
    "description": "《Programming Rudy》(中文版)(第2版)是……"
}
```

***
# **Post a new book**

`POST /books`

Create a new book, needs verification, status=201

Parameters information:

```
Authorization header: username = &password = 
Data:
{
    "name": "Rails之道",
    "isbn": "4727011",
    "author": "(美)Obie Fernandez",
    "price": 89,
    "img_url": "https://img3.doubanio.com/mpic/s4282672.jpg"
    "description": "《Rails之道》按照Rails的各个子系统进行组织编排……"
}
```

***
# **Edit a book**

`PUT /books/:isbn`

Edit a book. Only price,img_url,description can be changed.Verification is needed when you make these changes, status=202

Parameters information:

```
Authorization header: username = &password = 
Data:
{
    "price": 89,
    "img_url": "https://img3.doubanio.com/mpic/s4282672.jpg"
    "description": "《Rails之道》按照Rails的各个子系统进行组织编排……"
}
```

***
# **Destroy a book**

`DELETE /books/:isbn`

`Authorization header: username = &password = `

Delete a book, needs verification, status=200














