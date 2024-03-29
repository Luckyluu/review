



# HTTP

## 一、HTTP基本知识

### HTTP是什么

HTTP是超文本传输协议，它可以拆分成三个部分：超文本、传输、协议

![图片](https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZfXG1113Sjm0iaOXfoOv0tlU4cfNS4t8C0AjG8YleW3FjITV4h4aQNn1iboHhjALOGicsFsLuQAXwVaQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

1. 协议

   HTTP是用在计算机世界里的协议。它使用计算机能够理解的语言确立了一种计算机之间交流通信的规范，以及相关的各种控制和错误处理方式。

2. 传输

   HTTP是一个双向协议，我们在上网冲浪时，浏览器是请求方 A ，百度网站就是应答方 B。双方约定用 HTTP 协议来通信，于是浏览器把请求数据发送给网站，网站再把一些数据返回给浏览器，最后由浏览器渲染在屏幕，就可以看到图片、视频了。

   ![图片](https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZfXG1113Sjm0iaOXfoOv0tlUZzUNhbz8lJy4NPLT3iaFFU09Wg5OcrHwXLYP8a1pmaBseMLKxJd7cLw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

   HTTP是一个在计算机世界里专门用来在**两点之间传输数据**的约定和规范。

3. 超文本

   文字、图片、视频等的混合体。HTML是最常见的超文本，本身为纯文字，但是内部用很多标签定义了图片，视频，音频等的连接，经过浏览器的解释，呈现给我们的就是我们平时上网看到的效果了。

**定义：**HTTP是一个在计算机世界里面专门在**两点**之间**传输**文字、图片、音频、视频等**超文本**数据的**约定和规范**。

### HTTP常见的状态码

- 1xx：**提示信息**，表示目前是协议处理的中间状态。

  100：客户端应继续其请求。

- 2xx：**成功**，报文已经收到并被正确处理。

  | 状态码 | 英文名称        | 解释                                                         |
  | ------ | --------------- | :----------------------------------------------------------- |
  | 200    | OK              | 一切正常，如果是非HEAD请求，服务器返回的相应头都会有内容     |
  | 204    | No Content      | 服务器成功处理，但未返回内容。在未更新网页的情况下，确保浏览器继续显示当前文档 |
  | 206    | Partial Content | 应用于HTTP分块下载或断电续传，表示响应返回的数据并不是资源的全部，而是其中一部分 |

- 3xx：**重定向**，表示客户端请求的资源发生了变动，需要客户端用新的url重新发送请求获取资源。

  | 状态码 | 英文名称          | 解释                                                         |
  | ------ | ----------------- | ------------------------------------------------------------ |
  | 301    | Moved Permanently | 永久重定向，说明请求的资源已经不存在了，需要改动新的url再次访问 |
  | 302    | Found             | 临时重定向，表示资源还在，但是暂时需要用另一个url来访问<br />301和302都会在响应头里使用字段Location，指明后续要跳转的url，浏览器会自动重定向新的url |
  | 304    | Not Modified      | 不具有跳转意义，表示资源未修改，重定向已存在的缓冲文件，也称缓存重定向，用于缓存控制 |

- 4xx：表示客户端发送的**报文有误**，服务器无法处理，也就是错误码的含义。

  | 状态码 | 英文名称    | 解释                                                         |
  | ------ | ----------- | ------------------------------------------------------------ |
  | 400    | Bad Request | 表示客户端请求的报文有误，但只是个笼统的错误                 |
  | 403    | Forbidden   | 表示服务器禁止访问资源，并不是客户端的请求出错               |
  | 404    | Not Found   | 表示请求的资源在服务器上不存在或未找到，所以无法提供给客户端 |

- 5xx：表示客户端请求报文正确，但是**服务器处理时内部发生了错误**，属于服务器端的错误码。

  | 状态码 | 英文名称              | 解释                                                         |
  | ------ | --------------------- | ------------------------------------------------------------ |
  | 500    | Internal Server Error | 与400类似，是个笼统的错误                                    |
  | 501    | Not Implemented       | 表示客服端请求的功能还不支持                                 |
  | 502    | Bad Gateway           | 通常是服务器作为网关或代理时返回的错误码，表示服务器自身工作正常，访问后端服务器发生了错误 |
  | 503    | Service Unavailable   | 表示服务器当前很忙，暂时无法响应客服端的请求                 |

  

### HTTP常见字段

- Host：客户端发送请求时，用来指定服务器的**域名**。有了Host字段，就可以将请求发往**同一台**服务器上的不同网站。

- Content-Length：服务器返回数据时，表明本息回应的数据的长度。（单位：字节）

- Connection：用于客户端要求服务器使用TCP持久连接，以便其他请求复用。

  HTTP/1.1 版本默认连接都是持久连接，但为了兼容老版本的HTTP，需要指定Connection首部字段的值**Connection：keep-alive**，知道客服端或服务器主动关闭连接。

- Connect-Type：用于服务器回应时，向客户端表明数据格式。

  ```C++
  Connect-Type:text/html; charset=tuf-8
      //表明发送的是网页，编码是utf-8
  ```

- Accept：客户端请求时，声明自己可以接受哪些数据格式。Accept：* / * 表明自己可以接受任何格式的数据。

- Connect-Encoding：表示服务器返回的数据使用了什么压缩格式。

- Accept-Encoding：客户端在请求时说明自己可以接受哪些压缩方法。

  

## 二、GET与POST

**GET：**请求葱服务器获取资源。这个资源可以是文本、页面、图片视频等。

例如点开一个文章，浏览器就会发送GET请求给服务器，服务器就会返回文章的所有文字及资源。

**POST：**它是向URI指定的资源提交数据，数据就放在报文的body里。

例如在一篇文章下留言，提交之后浏览器就会执行一次POST请求，把我们的留言放在body里，然后拼接好POST的请求头，通过TCP协议发送给服务器。

GET和POST是HTTP协议中的两种请求方式，而HTTP的底层是TCP/IP，所以GET和POST用的都是同一传输层的协议。



### GET和POST的安全性和幂等

| 安全                     | GET                                                          | POST                                                 |
| ------------------------ | ------------------------------------------------------------ | ---------------------------------------------------- |
| 会不会破坏服务器上的资源 | 不会。GET是只读操作，无论操作多少次，服务器上的数据都是安全的。 | 会。POST是新增或提交数据操作，会修改服务器上的资源。 |
| 传送的数据的位置         | 放在url中，隐私信息可以直接被第三方看到。                    | 放在request body里，对用户不可见                     |

url的长度受浏览器和服务器的限制，所以GET传送的数据量会受到限制。

如果使用GET服务，并且在request body里写入数据，不同的服务器处理方式不同，有些服务器会读出数据，而有些会直接忽略。所以虽然GET可以带request body数据，但是不能保证会被收到。

**幂等：**意思是多次执行相同的操作，结果都是相同的。

所以 GET方案就是幂等的，而POST不是幂等的。

### 产生数据包

GET请求：浏览器会把http header 和打他一并发送出去，服务器响应200 ok；

POST请求：浏览器先发送header，服务器响应100 continue；浏览器再发送data，服务器响应200 ok。



## 三、HTTP特性

### 优点

1. 简单

   HTTP基本的报文格式是header+body，头部信息也是key-value简单文本的形式，易于理解，降低了学习的使用的门槛。

2. 灵活与易于扩展

   HTTP协议里的各类请求方法、URL/URI、状态码、头字段等每个组成要求都没有被固定死，都允许开发人员**自定义和扩充**。
   同时HTTP由于是工作在应用层，则它的下层可以随意变化。

3. 应用广泛和跨平台

   从台式机的浏览器到手机上的各种app，从看新闻到刷贴吧到购物，玩游戏等等，HTTP的应用非常广泛，且具有跨平台的优越性。

### 缺点

1. 无状态双刃剑

   **好处：**因为服务器不会去记忆HTTP的状态，所以不需要额外的资源来记录状态信息，这能减轻服务器的负担，能够把更多的CPU和内存用来对外援提供服务。

   **坏处：**服务器没有记忆能力，那么在完成有关联性的操作时会比较麻烦。
   例如登录->添加购物车->下单->结算->支付。这系列操作都要知道用户的身份才行。但服务器不知道这些请求是有关联的，每次都要问一遍身份信息。

   **解决方案：**例如Cookie技术。
   Cookie通过在请求和响应报文中写入Cookie信息来控制客户端的状态，相当于客户端第一次请求后，服务器会生产Cookie记住客户端是谁，并在响应中添加Cookie；后续客户端请求服务器的时候带上Cookie，服务器就能认识了。

2. 明文传输双刃剑

   **好处：**明文意味着在传输过程中的信息，是可方便阅读的，通过浏览器F12控制台或Wires hark抓包都可以肉眼查看，为我们条调试工作带来了极大的便利。

   **坏处：**在传输的过程中，信息的内容都毫无隐私可言，很容易就能被窃取。

3. 不安全

   - 通信使用明文传输（不加密），内容可能会被窃取，账号信息容易泄露
   - 不验证通信方的身份，因此有可能遭遇伪装。比如访问了假的购物网站，那你钱没了。
   - 无法证明报文的完整性，所以有可能已遭篡改。比如网页上的垃圾广告。

   HTTP的安全问题，可以用HTTPS的方式解决，也就是通过引入SSL/TLS层。

   

## 四、HTTP与HTTPS

### 区别

1. HTTP信息是明文传输，存在安全风险。HTTP在TCP和HTTP之间加入了SSL/TLS安全协议，使得报文能够加密传输。
2. HTTP连接建立相对简单，TCP三次握手之后便可以进行HTTP的报文传输。而HTTPS在TCP三次握手之后，还需要进行SSL/TLS的握手过程，才可以进入加密报文传输。
3. HTTP端口号是80，HTTPS端口号是443。
4. HTTPS需要向CA（证书权威机构）申请数字证书，来保证服务器身份是可信的。

### HTTPS如何解决HTTP不安全的问题

1. 混合加密

   实现信息的机密性，解决了窃听的风险。

   混合加密：**对称加密**和**非对称加密**结合。

   - 在通信建立前采用**非对称加密**的方式交换**会话密钥**，后续就不再使用非对称加密。
   - 在通信过程中全部使用**对称加密**的**会话密钥**的方式加密明文数据。

   采用混合加密方式的原因：

   - 对称加密只是用一个密钥，运算速度快，密钥必须保密，无法做到安全的密钥交换。
   - 非对称加密使用两个密钥：公钥和私钥。公钥可以任意分发，而私钥保密，解决了密钥交换，但速度较慢。

2. 摘要算法

   用于校验数据的完整性，防止被篡改。

   客户端在发送明文之前会通过摘要算法算出明文的“指纹”，发送的时候把“指纹+明文”一同加密成密文后，发送给服务器，服务器解密后，用相同的摘要算法算出送过来的明文。通过比较客户端携带的“指纹”和当前算出的“指纹”作比较，若相同则说明数据是完整的。

3. 数字证书

   将服务器公钥放入到数字证书中，解决了冒充的风险。

   客户端先向服务器索要公钥，然后用公钥加密信息，服务器收到密文后，用自己的私钥解密。

   **如何保证公钥不被篡改？**

   借助第三方权威机构 CA （数字证书认证机构），将服务器公钥放在数字证书（由数字证书认证机构颁发）中，只要证书是可信的，公钥就是可信的。

### HTTPS如何建立连接

SSL/TLS 协议基本流程：

- 客户端向服务器索要并验证服务器的公钥

- 双方协商产生“会话密钥”

- 双方采用“会话密钥”进行加密通信

  前两步为SSL/TLS 的握手阶段



## 五、HTTP/1.1、HTTP/2、HTTP/3 演变

### HTTP/1.1的性能

HTTP协议是基于TCP/IP，并且使用了“请求-应答”的通信模式。

1. 长连接

   早期HTTP/1.0，每发起一个请求，都要新建立一次TCP连接（三握手），而且是串行请求，做了无谓的TCP连接建立和断开，增加了通信的开销。

   HTTP/1.1提出了**长连接**的通信方式，也叫持久连接，**只要任意一端没有明确提出断开连接，则保持TCP连接状态**。减少了TCP连接的重复建立和断开所造成的额外开销，减轻了服务器的负载。

2. 管道网络传输

   可以在同一个TCP连接里，客户端可以发起多个请求，只要第一个请求发出去了，不必等待响应，就可以发送第二个请求，可以减少整体响应时间。
   
3. 队头阻塞

   虽然允许浏览器同时发出多个请求，但是服务器还是按照顺序做出回应。当顺序发送的请求序列中的一个请求因为某种元婴被阻塞时，在后面排队的所有请求也一同被阻塞了，会导致客户端一直请求不到数据。
