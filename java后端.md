# java基础

jdk：java开发环境：jre和javakit

jre：java运行环境：jvm和一些class类库

jvm：java虚拟机：运行字节码文件

### hashcode和equals（最终）的关系

如果2个对象的hashcode一样，对象不一定一样，进一步用equals来比较

如果不一样，对象肯定不一样

对象一样，hashcode一样

### string、stringbuffer、stringbuilder区别

string是不可变的，修改会生成一个新的字符串对象

stringbuffer线程安全。但是效率低

### 封装继承多态抽象

封装和继承归结于多态，多态存在方法的重写

### 抽象和接口的关系

类和接口的关系，抽象类中允许存在非抽象方法；接口所有方法必须抽象

接口不能实例化

抽象子类必须重写所有抽象方法

### static和final区别

static修饰类的内部结构：属性、方法、代码块、内部类

final变量只能赋一次值

final方法不能被子类重写

final类不能被继承







# java集合

### list和set区别

list有序，可重复，允许null，可以根据下标取元素

set最多允许一个null

### arraylist和linkedlist区别

底层数据结构不一样

适合的场景不同，链表更适合插入删除

### hashmap的put方法

先算出数据下表，如果元素为空，就封装成entry对象；

不为空，根据node类型，看是红黑树还是链表（尾插法）

# java并发

### 线程

sleep和wait

sleep属于thread，wait属于object

sleep不要释放锁，wait需要

然后要用interrupt中断



# jvm

# 操作系统

# 计算机网络

# spring

### ioc和aop

依赖注入

对象创建的权力交给外部容器；把对象的依赖关系交给ioc容器来处理；bean就是那些被ioc容器管理的对象

- `@Component`：通用的注解，可标注任意类为 `Spring` 组件。如果一个 Bean 不知道属于哪个层，可以使用`@Component` 注解标注。
- `@Repository` : 对应持久层即 Dao 层，主要用于数据库相关操作。
- `@Service` : 对应服务层，主要涉及一些复杂的逻辑，需要用到 Dao 层。
- `@Controller` : 对应 Spring MVC 控制层，主要用于接受用户请求并调用 `Service` 层返回数据给前端页面。
- @primary 赋予bean更高的优先级

### 



# mysql

![image-20240304151941208](/Users/teresa/Library/Application Support/typora-user-images/image-20240304151941208.png)

## 存储引擎

### innodb

是mysql5.5之后的默认引擎

支持事务、行级锁、外键约束

#### 存储结构

![image-20240304153620251](/Users/teresa/Library/Application Support/typora-user-images/image-20240304153620251.png)

表、段、区、页、行

一区包含64页

行就是一行数据

#### innodb如何实现事务

innodb在收到一个update语句后，根据条件找到数据所在的页，并将该页缓存在buffer pool中；

执行update语句，修改bufferpool数据

针对update语句生成一个redolog对象，存入logbuffer中

针对update语句生成undolog日志，用于事务回滚

如果事务提交，将redolog持久化

如果事务回滚，用undolog进行回滚

### myisam

早期默认引擎

不支持行锁、外键约束、事务；支持表锁，访问速度快



## 外键约束

主表和从表互相约束，修改数据时会相关联（比如学生表和成绩表，删除一个学生，成绩表也会删除）

## 事务

### 四大事务

原子性：要么全部完成，要么全部不完成（中途失败会回滚）

隔离性：事务的执行互不干扰

一致性：数据库从一个一致性的状态转换到另一个一致性的状态（比如事务失败了回滚会和原来的数据一样，没有发生变化）

持久性：一旦事务提交，修改会永久保存

### 隔离级别

读未提交: 读到其他事务未提交的数据，脏读

读已提交：2次读取结果不一致

可重复读：（mysql默认）每次读取都一样

串行化：给每一行读取的数据加锁（导致大量超时，一般不用）

## 锁



## 索引

是什么：索引的作用就相当于书的目录

为什么要用：对 SQL 的性能提升非常明显，是一个性价比较高的 SQL 优化手段。

### 索引覆盖

就是一个sql在执行时，可以利用索引来快速查找，并且sql查询字段再当前索引对应的字段中都包含

### 最左前缀原则

当一个sql想要利用索引，就要提供该索引所对应字段中最左边的字段；这是由于：底层b+树是按照字段排序的

## 排行榜











## redis

### 缓存三兄弟

缓存穿透：访问数据在redis中不存在（解决：使用布隆过滤器）

缓存击穿：某一个热点数据失效（解决：给这个热点key不设置过期时间）

缓存雪崩：如果某一时刻大批热点数据同时过期，导致大量数据同时访问mysql（解决：在过期时间上加一点随机值/搭建一个高可用redis集群）

### AOF-----redis持久化

redis是一个键值对数据库服务器，是内存数据库，数据保存在内存；服务器进程退出会失去数据，为了避免，要将内存数据转移到磁盘中（使用aof和rdb机制）

aof持久化默认关闭，如果开启，默认使用aof（aof更为可靠）

和rdb保存方式不同：rdb保存键值对，aof保存命令



### 缓存过期

定时过期：设定过期时间

惰性过期：访问到才判断是否过期

### 使用

##### 安装brew install redis

// 1. 使用 brew 启动软件 brew services start redis // 2. 执行命令，启动服务 redis-server



##### 查看 Redis 服务进程

```bash
ps axu | grep redis
```



##### 通过 redis-cli 连接 redis 服务

redis 默认端口号6379，输入以下命令即可连接

```bash
redis-cli -h 127.0.0.1 -p 6379
```



##### redis-cli 启动 Redis 客户端

打开终端并输入命令，该命令会连接本地的 redis 服务。

$redis-cli
redis 127.0.0.1:6379>
redis 127.0.0.1:6379> PING
PONG
// PING 命令，该命令用于检测 redis 服务是否启动。



##### 关闭 Redis Server

命令关闭
向 Redis 发送 SHUTDOWN 命令，即 redis-cli SHUTDOWN。Redis 收到命令后，服务端会断开所有客户端的连接，然后根据配置执行持久化，最后退出。

redis-cli shutdown

强行终止

sudo pkill redis-server



#### 操作

查看当前数据库中key的数量：dbsize

---

切换库命令：select （数字）
库的下标从0开始，redis.conf配置中默认16个库。下标0-15

---

删除当前数据库的所有数据：flushdb

---



#### Redis的key的操作命令

语法	功能
keys pattern	查看数据库所有符合pattern的key
exists key [key…]	判断key是否存在
expire key seconds	设置 key 的生存时间，超过时间，key 自动删除。单位是秒。
ttl key	以秒为单位，返回 key 的剩余生存时间（ttl: time to live）
type key	查看 key 所存储值的数据类型
del key [key…]	删除存在的 key，不存在的 key 忽略。



#### 基本命令

set key value
把value的值赋给key

---

get key
获取key的value

---

incr key
将 key 中储存的数字值加 1，如果 key 不存在，则 key 的值先被初始化为 0 再执行incr 操作（只能对数字类型的数据操作）

---

decr key
将 key 中储存的数字值减1，如果 key 不存在，则么 key 的值先被初始化为 0 再执行 decr 操作（只能对数字类型的数据操作）

---

append key value
如果 key 存在，则将 value 追加到 key 原来旧值的末尾
如果 key 不存在，则将 key 设置值为 value
返回值：追加字符串之后的总长度

---

strlen key
返回key存储的value的总长度，key不存在返回0

---

getrange key start end
作用：获取 key 中字符串值从 start 开始到 end 结束的子字符串,包括 start 和 end, 负数表示从字符串的末尾开始，-1 表示最后一个字符

---

setrange key offset value
说明：用 value 覆盖（替换）key 的存储的值从 offset 开始,不存在的 key 做空白字符串。
返回值：修改后的字符串的长度

---

mset key value [key value…]
说明：同时设置一个或多个 key-value 对

---

mset key value [key value…]
说明：同时设置一个或多个 key-value 对

---

hset hash 表的 key field value
作用：将哈希表 key 中的域 field 的值设为 value，如果 key 不存在，则新建 hash 表，执行赋值，如果有 field ,则覆盖值。

---

hget key field
作用：获取哈希表 key 中给定域 field 的值



https://blog.csdn.net/luna_a/article/details/107292994











# 项目

## 数据库

xzs

password：12345678



### PostgreSQL

brew install postgresql

brew services start postgresql@14

创建一个新角色 createuser -P <username>

创建一个新数据库 createdb -O <username> <database>

密码：root

账号：root

## maven

- 安装

brew install maven

- brew list maven`来查看maven的安装位置

/Users/teresa/Program/DevTools/apache-maven-3.9.5



## 接口

https://www.mindskip.net:999/guide/student.html



## 消息队列

MQ：message queue

不同进程传递消息时耦合性太高，改动一个会影响另一个，所以要隔离就使用消息队列；

一下子接受消息太多，应付不过来，用消息队列处理

应用：当学生提交考试时，系统不需要同步处理所有的评分和反馈逻辑，而是将提交的考试信息发送到RabbitMQ队列。后台服务（消费者）异步从队列中获取信息，进行评分、反馈生成等操作，然后更新数据库。这减少了学生等待的时间，并提高了系统的响应性。

考试成绩处理完成后，可以通过RabbitMQ发送消息给相关的通知服务，该服务负责将成绩通知发送给学生，例如通过电子邮件、短信或应用内通知。这样做可以解耦成绩计算和用户通知的逻辑，提高系统的可维护性和扩展性。

## spring-boot-security 用户登录验证





## 消息队列

什么是消息队列：用队列作为底层数据结构，解决进程与应用之间的通讯工具，（消息中间件）

### 应用场景

##### 优化异步处理

##### 应用解耦

##### 流量太大

```
import queue
import threading
import time

# 创建一个消息队列
message_queue = queue.Queue()

def post_message(user, message):
    """将用户消息发送到队列中"""
    timestamp = time.strftime('%Y-%m-%d %H:%M:%S', time.localtime())
    message_queue.put((timestamp, user, message))

def read_messages():
    """从队列中读取所有消息"""
    while not message_queue.empty():
        message = message_queue.get()
        print(f"[{message[0]}] {message[1]}: {message[2]}")

def user_interface():
    """简单的用户界面来发送和读取消息"""
    while True:
        action = input("Do you want to post or read messages? (post/read/exit): ").lower()
        if action == "post":
            user = input("Enter your username: ")
            message = input("Enter your message: ")
            post_message(user, message)
        elif action == "read":
            print("Reading messages...")
            read_messages()
        elif action == "exit":
            print("Exiting...")
            break
        else:
            print("Invalid action. Please choose 'post', 'read', or 'exit'.")

if __name__ == "__main__":
    user_interface_thread = threading.Thread(target=user_interface)
    user_interface_thread.start()

```

###### java版

### 步骤1: 定义Message类

```
javaCopy code
public class Message {
    private String message;
    private String sender;

    public Message(String sender, String message) {
        this.sender = sender;
        this.message = message;
    }

    @Override
    public String toString() {
        return sender + ": " + message;
    }
}
```

### 步骤2: 创建Producer类

```
javaCopy code
import java.util.concurrent.BlockingQueue;

public class Producer implements Runnable {
    private BlockingQueue<Message> queue;

    public Producer(BlockingQueue<Message> q){
        this.queue = q;
    }

    @Override
    public void run() {
        // 模拟发送消息
        Message msg = new Message("User1", "Hello from User1!");
        try {
            queue.put(msg);
            Thread.sleep(1000); // 模拟延迟
            queue.put(new Message("User2", "Hello from User2!"));
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### 步骤3: 创建Consumer类

```
javaCopy code
import java.util.concurrent.BlockingQueue;

public class Consumer implements Runnable{
    private BlockingQueue<Message> queue;

    public Consumer(BlockingQueue<Message> q){
        this.queue = q;
    }

    @Override
    public void run() {
        try{
            Message msg;
            // 消费消息直到接收到“exit”消息
            while(!(msg = queue.take()).toString().equals("exit")){
                System.out.println("Received: " + msg);
            }
        }catch(InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### 步骤4: 主程序

```
javaCopy code
import java.util.concurrent.ArrayBlockingQueue;
import java.util.concurrent.BlockingQueue;

public class ChatApplication {
    public static void main(String[] args) {
        // 创建大小为10的队列
        BlockingQueue<Message> queue = new ArrayBlockingQueue<>(10);

        // 创建生产者和消费者
        Producer producer = new Producer(queue);
        Consumer consumer = new Consumer(queue);

        // 启动生产者和消费者线程
        new Thread(producer).start();
        new Thread(consumer).start();

        System.out.println("Chat Application is running...");
    }
}
```



# 微服务架构





# springboot

起步依赖 springbootstartweb

自动配置 bean

bean扫描

@bean  



@value的用法

![image-20240724170530976](/Users/teresa/Library/Application Support/typora-user-images/image-20240724170530976.png)



自动配置原理

在boot程序启动后，起步依赖中的一部分bean对象会自动注入到ioc容器



restcontoller&controller

@RestController 是 @Controller 和 @ResponseBody 的结合体。

​	•	@Controller 适用于传统的Web应用程序，通常需要返回视图进行页面渲染。

​	•	@RestController 适用于RESTful Web服务，默认返回JSON或XML数据，不需要返回视图进行页面渲染。



使用@validation参数校验

![image-20240726133043954](/Users/teresa/Library/Application Support/typora-user-images/image-20240726133043954.png)

全局异常处理器





![image-20240727162916703](/Users/teresa/Library/Application Support/typora-user-images/image-20240727162916703.png)

分组校验（用得少）

比如id设为not null，但是id一般是自增的，id设为not null会报错。由此规则分组

![image-20240728124116056](/Users/teresa/Library/Application Support/typora-user-images/image-20240728124116056.png)
