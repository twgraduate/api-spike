# **API Basic**

* Get all books information list:                 GET       /books
* Read a book detailed information by book i      GET       /books/:id
* Add a book to the list                          POST      /book
* Edit detail information by book id              PUT       /book/:id
* Delete book information by book id              DELETE    /book/:id

***
# **API error**

When an error occured, HTTP Status Code is 404,422,500.

Layout of error:

```
{
    'msg':'error message'
}
```

* 404:  Book not found;
* 422:  Some parameters are illegal, book entity is unprocessable;
* 500:  other error


|Error Message                          |Status Code        |     Error describe
|---------------------------------------|:-----------------:|-------------------------------------------------------------------------
|Book not found                         |    404            | {:id} don't refers to any book
|Exception                              |    500            | Other error
|Book name can't be empty               |    422            | The book name in your parameters is empty
|Name&&author can't be same at same time|    422            | The book you POST or PUT has the same name and author with books in SQL
|Author can't be empty                  |    422            | The book author in your parameters is empty
|Isbn can't be empty                    |    422            | The book isbn in your parameters is empty
|Isbn should be unique                  |    422            |The book you POST or PUT has the same ISBN with other books in SQL

***
# **Get books list**

`GET localhost:3000/books`

Return books list, status=200

 ```
[
{
  "id": 1,
  "name": "Rails之道",
  "isbn": "4727011",
  "author": "(美)Obie Fernandez",
  "price": 89,
  "img_url": "https://img3.doubanio.com/mpic/s4282672.jpg",
  "description": "《Rails之道》按照Rails的各个子系统进行组织编排，分别介绍了Rails的环境、初始过程、配置和日志记录，Rails的分配器、控制器、页面生成和路由，REST、资源和Rails，ActiveRecord的基础、关联、验证和高级技巧，ActionView的模板、缓存和帮助器，Ajax、Prototype和Scriptaculous等JavaScript代码库和RJS，Session管理、用户登录和认证系统，XML和ActiveResource，后台处理和ActionMaile，测试和specs(包括RSpec on Rails和Selenium)，安装、管理、编写插件，Rails的生产部署、配置和Capistrano等内容。 《Rails之道》详细讨论了Rails的程序代码并通过分析Rails中的代码片段来深入解释它的功能，同时，《Rails之道》部分章节也摘录了一些API文档中的内容，使读者能够快速地找到对应的API文档、相关的示例代码以及深入的解析说明。 《Rails之道》是Rails的权威参考书，适合对Rails已经有一定了解的开发人员学习和使用。"
},
{
  "id": 2,
  "name": "Programming Ruby中文版",
  "isbn": "2032343",
  "author": "托马斯",
  "price": 99,
  "img_url": "https://img3.doubanio.com/mpic/s2370875.jpg",
  "description": "《Programming Rudy》(中文版)(第2版)是它的第2版，其中包括超过200页的新内容，以及对原有内容的修订，涵盖了Ruby 1．8中新的和改进的特性以及标准库模块。它不仅是您学习Ruby语言及其丰富特性的一本优秀教程，也可以作为日常编程时类和模块的参考手册。Ruby是一种跨平台、面向对象的动态类型编程语言。Ruby体现了表达的一致性和简单性，它不仅是一门编程语言，更是表达想法的一种简练方式。它不仅受到广大程序员的欢迎，无数的软件大师亦为其倾倒。Programming Rubyr是关于Ruby语言的一本权威著作，也被称为PickAxe Book(镐头书，由封面上的工具得名)。"
}
]
 ```

***
# **Get a book message**

`GET  /books/:id`

Return a book's information,status=200

```
{
    "id": 2,
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

`POST localhost:3000/books`

Create a new book, status=201

Parameters information:

```
{
   book[name]:Rail之道
   book[isbn]:4727011
   book[author]:(美)Obie Fernandez
   book[price]:89
   book[img_url]:https://img3.doubanio.com/mpic/s4282672.jpg
   book[description]:《Rails之道》按照Rails的各...
}
```

***
# **Edit a book**

`PUT localhost:3000/books/:id`

Edit a book, status=202

Parameters information:

 ```
{
   book[name]:Rail之道
   book[isbn]:4727011
   book[author]:(美)Obie Fernandez
   book[price]:89
   book[img_url]:https://img3.doubanio.com/mpic/s4282672.jpg
   book[description]:《Rails之道》按照Rails的各...
}
 ```

***
# **Destroy a book**

`DELETE localhost:3000/books/:id`

Delete a book, status=200














