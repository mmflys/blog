# Base
## Java Base
* 数据类型
    * 基本数据类型
      * 整数类型: byte(1\*8bit), short(2\*8bit), int(4\*8bit), long(8\*8bit)
      * 浮点型: float(4\*8bit), double(8\*8bit)
      * boolean(1bit)
      * char(2\*8bit)
   * 包装类型
      * 整数类型: Byte, Short, Integer, Long
      * 浮点型: Float, Double
      * Boolean
      * Charactor
   * 引用类型
      * 强引用: Object, 所有的类都继承了Object类, 所有的类对象都是一个Object
      * SoftReference: 软引用,内存不足时被回收
      * WeakReference: 弱引用, 第一次gc时被回收
      * PhantomReference: 虚引用, 形同虚设
* 循环语句/条件语句
   ```Java
      do {
         // do something
      }while()
   ```
   ```Java
      for(int i=0;i<10;i++){
         // do something
      }
   ```
   ```Java
      if(){
      
      }else if(){
      
      }else{
      
      }
   ```
* 异常
   * Throwable
   * 运行时异常: RuntimeException
   * 检查时异常: Exception
* IO
   * InputStream -> FileInputStream, ObjectInputStream
   * OutputStream -> FileOutputStream, ObjectOutputStream
   * Reader -> BufferedReader, InputStreamReader -> FileReader
   * Writer -> BufferedWriter, OutputStreamWriter -> FileWriter
* 集合类
   * Array: `int[] nums = new int[5]`
   * List: 有序, 可重复
      * ArrayList: `List<Integer> nums = new ArrayList<>();`
      * LinkedList: `List<Integer> nums = new LinkedList<>();`
   * Set: 无序, 不可重复
      * HashSet: `Set<Integer> nums = new HashSet<>();`
   * Map: key-value映射
      * HashMap: `Map<String, Integer> nums = new HashMap<>();`
      * ConccurrentHashMap: `Map<String, Integer> nums = new ConccurrentHashMap<>();`
   * Queue
      * LinkedBlockingQueue
      * ArrayBlockingQueue
      * PriorityBlockingQueue
      * SynchronousQueue
* 多线程
   * Thread
   * Runable/Executor
   * ThreadPoolExecutor
       * corePoolSize: 保持存活的最小线程数量
       * maximumPoolSize: 最大线程数量
       * keepAliveTime: 线程最大空闲时间
       * workQueue: 工作队列
       * rejectedExecutionHandler: 当线程池满时的拒绝策略
           * AbortPolicy: 直接抛出异常
           * CallerRunsPolicy: 只要线程池没有shutdown就在用户线程执行
           * DiscardPolicy: 丢弃不执行
           * DiscardOldestPolicy: 丢弃线程队列首个任务, 执行新任务
       * threadFactory: 线程生成工厂
* 锁
   * synchronized
   * ReentrantLock
   * AQS
## JVM
* 内存划分
   * PC Register,程序计数器, 保存着每一条线程下一次执行指令位置
   * Heap: 堆, 存放Java对象
   * Method Area: 元空间/永久代/方法区, 常量, 静态变量, 类信息
   * VM Stack: Java虚拟机栈, 存放本地变量表, 操作数栈, 用于方法的执行
   * Native Method Stack: 本地方法栈: 其他语言的栈
* GC算法
   * 引用计数: 对象被引用的次数为0则对象已死, 解决不了对象相互引用的问题
   * 可达性分析: 判断对象是否有到gc root object的路径
       * gc root object
           * Java虚拟机栈中引用的对象
           * 本地方法栈中引用的对象
           * 静态变量引用的对象
           * 常量引用的对象 
           * 被synchronized持有的对象
           * Java虚拟机内部的引用
           * JM XBean, JVM TI中注册的回调, 本地代码缓存
* GC收集器
    * Serial/Serial Old: 单线程, 
    * ParNew: 多线程, 多cpu, 停顿时间比Serial少(ParNew + CMS, ParNew + Serial Old)
    * Parallel Scavenge（ParallerGC）/Parallel Old: 高吞吐量, 适合在后台运行, 不需要太多交互
    * CMS(Concurrent Mark Sweep): 低停顿时间, 适合B/S系统, 重视响应速度
    * G1: 根据region的价值大小依次回收, 新生代和老年代不再物理隔离, 不提供full GC的
* 类加载机制
    * 加载: 获取类的二进制流, 生成Class对象
    * 验证
    * 准备: 为类变量分配内存, 赋默认值
    * 解析: 将常量池内的符号引用替换为直接引用(CONSTANT_Class_info -> 地址/句柄/偏移量)
    * 初始化: 为类变量赋程序员定义的初值
## Data Structure
* 数组: 物理空间连续, 创建时固定大小
* 链表: 逻辑空间连续, 不固定大小
* 队列: 先进先出(first in first out:FIFO)
* 栈: 先进后出
* 树: 二叉树, 平衡二叉树, 红黑树, B树, B+树
## Algorithm
* 贪心算法
* 分治法
* 动态规划: 状态转移方程, 二维数组存放子解答
## Design Model
* 建造者模式
* 单例模式
* 观察者模式
* 策略模式
* 过滤器模式
## Computer Network
* 七层网络模型
* [TCP](https://tools.ietf.org/html/rfc793)
* [UDP](https://tools.ietf.org/html/rfc768)
* [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP#:~:text=Hypertext%20Transfer%20Protocol%20(HTTP)%20is,be%20used%20for%20other%20purposes.)
* [HTTPS](https://www.ssl.com/faqs/what-is-https/)
## Linux
* Move: cd, mkdir, ls, pwd, rm, cp, mv
* Search: grep, find, where, which, locate
* Privilege: chmod, chowm, su, who
* Service: df, free, top, ps, kill, service
* Network: ssh, scp, wget, curl, netstat
* Configuration: uname, ifconfig, yum, echo, history, man, info
* Read: cat, less, more, tail, head, vim

# Advance
## Distribution
* CAP理论
* 分布式存储
* 分布式计算
* 分布式事务
## Micro Service
## Hadoop
* HDFS(大数据文件系统)
* MapReduce(分布式离线计算) -> Spark(分布式批处理, 流处理) -> Flink(分布式流处理)
* Hive(大数据结构化数据仓储), Hbase(大数据非结构化数据库)
* Yarn(大数据资源管理)
* Flume(海量日志采集)
## Middleware
* Redis, Mysql, RocketMQ/Kafka, Zookeeper, Spring/SpringBoot/SpringCloud
## Devops
* Maven(build工具)
* Git(版本控制)
* Jeinks/Teamcity(CICD工具)
* Docker(容器化)
* k8s(容器管理平台)

# Book
* [数据结构](/book/数据结构与算法分析java语言描述原书第3版.pdf)
* [算法](/book/算法第四版.pdf)
* [设计模式](/book/HeadFirst设计模式.pdf)
* [深入理解Java虚拟机](深入理解Java虚拟机.pdf)

# Ide
* [Jet Brains Toolbox App](https://www.jetbrains.com/toolbox/app/)(在toolbox中下载各种ide)
    * [有@edu邮箱](https://www.jetbrains.com/shop/eform/students)
    * 无@edu邮箱: 破解

# Reference
* [Java菜鸟教程](https://www.runoob.com/java/java-tutorial.html)
* [设计模式菜鸟教程](https://www.runoob.com/design-pattern/design-pattern-tutorial.html)
* [数据结构和算法动态可视化](https://visualgo.net/zh)
