- 虚方法表：
	-在Java中，每个类都有一个虚方法表，它包含了该类的所有非私有实例方法的地址。当调用一个对象的方法时，JVM会根据该对象所属类的虚方法表来确定要调用的具体方法。
    
- 堆
	- 堆是JVM中用于存储对象实例和数组的内存区域。它被所有线程共享，并且具有运行时数据区域中最大的一块。
    
-   栈上分配对象：
	- 通常情况下，Java对象是在堆上分配内存空间的。但是，在某些情况下，JVM可以通过逃逸分析技术来确定一个对象是否只能在当前线程中访问。如果是这样，那么JVM就可以选择在栈上分配这个对象，从而避免了在堆上分配内存空间并进行垃圾回收。
    
-   逃逸分析：
	- 逃逸分析是一种编译器优化技术，它用于确定一个对象是否只能在当前线程中访问。如果一个对象只能在当前线程中访问，那么它就不会“逃逸”到其他线程中去。通过进行逃逸分析，JVM可以更好地优化内存管理和垃圾回收。
    
-   栈没有垃圾回收：
	- 栈上分配的内存空间不需要进行垃圾回收。当一个方法执行完毕后，它所占用的栈帧就会被弹出栈，并且其中包含的所有局部变量和临时数据都会被自动释放。
    
-   分代垃圾回收算法：
	- 这种算法将堆划分为新生代（Young Generation）和老年代（Old Generation）。新生代主要用于存放新创建的短暂存在时间较短或者经常改变状态的对象；老年代则主要用于存放长期存在时间较长或者状态稳定不变化多次经过Minor GC仍然存活下来并晋升到老年代 的对象。
    
    -   新生区 养老区 元空间: 
	    - 新生区又称为年轻代(Young Generation)，养老区又称为老年代(Old Generation)，元空间(Metaspace)取代了原先版本中永久代(Permanent Generation)。
    -   TLAB: 
	    - Thread Local Allocation Buffer (TLAB) 是每个线程独占一块 Eden 区域以减少竞争。
    -   新生代 老年代比例: 
	    - 默认情况下新生代与老年代比例为1:2
    -   jinfo: 
	    - jinfo 是 JDK 自带工具之一, 可以查看 Java 进程运行时参数信息。
    -   jstat:
	    - jstat 是 JDK 自带工具之一, 可以查看 Java 进程 GC 信息。
    -   XX:-UseAdaptiveSizePolicy: 
	    - 此参数表示关闭自适应 GC 策略。
    -   XX:SurvivorRatio : 
	    - SurvivorRatio 表示 Eden 区与 Survivor 区大小比值，默认值为8。
    -   对象销毁大部分在新生代: 
	    - 大部分情况下, 对象都会很快死亡, 因此大部分销毁操作发生在新生区 Minor GC 中。
    -   XX:NewRatio : 
	    - NewRatio 表示新生区与老年区大小比值，默认值
    
    minor GC: 
		- Minor GC 是指发生在新生代的垃圾回收。由于新生代中对象的生命周期较短，因此 Minor GC 的频率较高。
    
    -   都有哪些gc: 
	    - 常见的垃圾回收器有 Serial、ParNew、Parallel Scavenge、Serial Old、Parallel Old、CMS 和 G1 等。
    -   图解新生代对象的分配与回收过程: 
	    - 新生代中包括 Eden 区和两个 Survivor 区（分别称为 From 和 To）。当对象在 Eden 区创建时，它们会被分配到 Eden 区。当 Eden 区满时，JVM 会触发一次 Minor GC。在 Minor GC 过程中，Eden 区和 From Survivor 区中仍然存活的对象会被复制到 To Survivor 区，并且它们的年龄计数器会加 1。如果一个对象的年龄达到了进入老年代阈值（默认为 15），那么它就会被晋升到老年代。Minor GC 完成后，Eden 区和 From Survivor 区中的对象都会被清空，To Survivor 区则变成了新的 From Survivor 区。
    -   年龄计数器: 
	    - 年龄计数器用于记录一个对象在新生代中经历了多少次 Minor GC。每当一个对象经过一次 Minor GC 后仍然存活下来时，它的年龄计数器就会加 1。
    -   进入老年代阈值: 
	    - 进入老年代阈值是指一个对象在新生代中经历了多少次 Minor GC 后才能够晋升到老年代。这个阈值可以通过 -XX:MaxTenuringThreshold 参数来设置，默认值为 15。