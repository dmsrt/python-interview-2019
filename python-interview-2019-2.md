## Python开发工程师笔试题

> 答题要求：将该项目从[地址1](<https://github.com/jackfrued/python-interview-2019>)或[地址2](<https://gitee.com/jackfrued/python-interview-2019>)fork到自己的[github]()或[gitee]()仓库并填写答案，完成之后将自己的仓库（public）地址发给面试官即可，答题时间120分钟。

1. 下面的Python代码会输出什么。

   ```Python
   print([(x, y) for x, y in zip('abcd', (1, 2, 3, 4, 5))])
   print({x: f'item{x ** 2}' for x in range(5) if x % 2})
   print(len({x for x in 'hello world' if x not in 'abcdefg'}))
   ```

   答案：

   ```
   [('a',1),('b',2),('c',3),('d',4)]
   {1:item1, 3:item3}
   6
   ```

2. 下面的Python代码会输出什么。

   ```Python
   from functools import reduce
   
   items = [11, 12, 13, 14] 
   print(reduce(int.__mul__, map(lambda x: x // 2, filter(lambda x: x ** 2 > 150, items))))
   ```

   答案：

   ```
   42
   ```

3. 有一个通过网络获取数据的Python函数（可能会因为网络或其他原因出现异常），写一个装饰器让这个函数在出现异常时可以重新执行，但尝试重新执行的次数不得超过指定的最大次数。

   答案：

   ```Python
   from functools import wraps


   def record(output):
    """自定义带参数的装饰器"""
	   count = 5
	   def decorate(func):
		
         @wraps(func)
         def wrapper(*args, **kwargs):
            n = 0
            result = func(*args, **kwargs)
            output(func.__name__, time() - start)
            return result

         return wrapper

      return decorate
   ```

4. 下面的字典中保存了某些公司今日的股票代码及价格，用一句Python代码从中找出价格最高的股票对应的股票代码，用一句Python代码创建股票价格大于100的股票组成的新字典。

   > 说明：美股的股票代码是指英文字母代码，如：AAPL、GOOG。

   ```Python
   prices = {
       'AAPL': 191.88,
       'GOOG': 1186.96,
       'IBM': 149.24,
       'ORCL': 48.44,
       'ACN': 166.89,
       'FB': 208.09,
       'SYMC': 21.29
   }
   ```

   答案：

   ```Python
   prices2 = {key: value for key, value in prices.items() if value > 100}
   print(prices2)
   ```

5. 用生成式实现矩阵的转置操作。例如，用`[[1, 2], [3, 4], [5, 6]`表示矩阵$\begin{bmatrix}1 & 2\\\\3 &4\\\\5 & 6\end{bmatrix}$，写一个生成式将其转换成`[[1, 3, 5], [2, 4, 6]]`即$\begin{bmatrix}1 & 3 & 5\\\\2 & 4 & 6\end{bmatrix}$。

   答案：

   ```Python
   
   ```

6. 写一个函数，传入的参数是一个列表（列表中的元素可能也是一个列表），返回该列表最大的嵌套深度，例如：

   > 参数：`[1, 2, 3]`
   >
   > 返回：`1`
   >
   > 参数：`[[1], [2, [3]]]`
   >
   > 返回：`3`

   答案：

   ```Python
   
   ```

7. 写一个函数，实现将输入的长链接转换成短链接，每个长链接对应的短链接必须是独一无二的且每个长链接只应该对应到一个短链接，假设短链接统一以`http://t.cn/`开头。

   > 参数：`http://jackfrued.xyz/api/users/10001`
   >
   > 返回：`http://t.cn/E6MUth1`

   答案：

   ```Python
   
   ```

8. 用5个线程，将1~100的整数累加到一个初始值为0的变量上，每次累加时将线程ID和本次累加后的结果打印出来。

    答案：

    ```Python
    
    ```

9. 请阐述Python是如何进行内存管理的。

    答案：

    ```
    python内存管理机制 ( Pymalloc ) 包括三个方面：引用计数、垃圾收集、内存池。

   1.  引用计数：python程序中使用的每个变量后台都有一个引用计数。赋值或调用操作，计数加一；相反，删除或移出窗口对象，计数减一。

   2.  垃圾收集：将引用计数为0的对象所占有的内存空间释放。还有一个循环垃圾收集器，负责清理未引用的循环，如两个对象互相引用的情况。

   3.  内存池：内存池是预先从内存中申请的内存块，当创建小于256 bits 的对象时，从内存池申请内存空间。创建大于256 bits 的对象从内存申请空间。释放内存时，来自内存池的内存空间返回给内存池。这样做的目的是为了减少内存碎片，提升效率。
    ```

10. 在MySQL数据库中有名为`tb_result`的表如下所示，请写出能查询出如下所示结果的SQL。

  `tb_result`表：

  | rq         | shengfu |
  | ---------- | ------- |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 负      |
  | 2017-04-09 | 负      |
  | 2017-04-10 | 胜      |
  | 2017-04-10 | 负      |
  | 2017-04-10 | 负      |

  查询结果：

  | rq         | 胜   | 负   |
  | ---------- | ---- | ---- |
  | 2017-04-09 | 2    | 2    |
  | 2017-04-10 | 1    | 2    |

  答案：

  ```SQL
  
  ```

11. 列举出你知道的HTTP请求头选项并说明其作用。

    答案：

    ```
    origin
    referer
    user-agent
    cookies
    ```

12. 阐述JSON Web Token的工作原理和优点。

    答案：

    ```
    1. 客户端使用账号和密码请求登录接口。
    2. 登录成功后服务器使用签名密钥生成JWT，然后返回JWT给客户端。
    3. 客户端再次向服务端请求其他接口时会带上JWT。
    4. 服务器接收到JWT后验证签名的有效性，对客户端做出相应的响应。
    优点：
    
    ```

13. 请阐述访问一个用Django或Flask开发的Web应用，从用户在浏览器中输入网址回车到浏览器收到Web页面的整个过程中，到底发生了哪些事情，越详细越好。

    答案：

    ```
    
    ```

14. 请阐述HTTPS的工作原理，并说明该协议与HTTP之间的区别。

    答案：

    ```
    超⽂文本传输协议HTTP协议被⽤用于在Web浏览器器和⽹网站服务器器之间传递信息，HTTP协议以明⽂文⽅方式送内容，不不提供任何⽅方式的数据加密安全套接字层超⽂文本传输协议HTTPS，为了了数据传输的安全，HTTPS在HTTP的基础上加⼊入了了SSL协议，SSL依靠证书来验证服务器器的身份，并为浏览器器和服务器器之间的通信加密。
    ```

15. 简述如何检查数据库是不是系统的性能瓶颈以及你在工作中是如何优化数据库操作性能的。

    答案：

    ```
    在mysql中设置慢查询
    建立中间表、建立索引
    ```

16. 在Linux系统中，假设Nginx的访问日志位于`/var/log/nginx/access.log`，该文件的每一行代表一条访问记录，每一行都由若干列（以制表键分隔）构成，其中第1列记录了访问者的IP地址。请用一条命令找出最近的100000次访问中，访问频率最高的IP地址及访问次数。

    答案：

    ```Shell
    
    ```

