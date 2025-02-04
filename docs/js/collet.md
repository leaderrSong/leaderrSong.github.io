# 3. 集合面试总集

## 02.ArrayList和Vector的联系和区别
 相同点： *
底层都使用数组实现 
功能相同，实现增删改查等操作的方法相似 
长度可变的数组结构 
** 不同点：  **
Vector是早期JDK版本提供，ArrayList是新版本替代Vector的 
Vector 的方法都是同步的，线程安全；ArrayList 非线程安全，但性能比Vector好 
默认初始化容量都是10，Vector 扩容默认会翻倍，可指定扩容的大小；ArrayList只增加 50%
## 03.Collection和Collections有什么区别
**Collection**是JDK中集合层次结构中的最根本的接口。定义了集合类的基本方法
**Collections**是一个包装类。它包含有各种有关集合操作的静态多态方法,不能实例化，像一个Collection集合框架中的工具类。 
## 04.List、Set、Map之间的区别是什么
List：有序集合，元素可重复 
Set：不重复集合，LinkedHashSet按照插入排序，SortedSet可排序，HashSet无序 
Map：键值对集合，存储键、值和之间的映射；Key无序，唯一；value 不要求有序，允许重复 
## 05.HashMap和Hashtable有什么区别
JDK 1.8 中 HashMap 和 Hashtable 主要区别如下： 
**1.线程安全性不同 **
HashMap线程不安全；Hashtable 中的方法是Synchronize的。 
**2.key、value是否允许null。**
HashMap的key和value都是可以是null，key只允许一个null； 
Hashtable的key和value都不可为null。 
** 3.迭代器不同  **
HashMap的Iterator是fail-fast迭代器；Hashtable还使用了enumerator迭代器。 
** 4.hash的计算方式不同  **
HashMap计算了hash值；Hashtable使用了key的hashCode方法。 
** 5.默认初始大小和扩容方式不同  **
HashMap默认初始大小16，容量必须是2的整数次幂，扩容时将容量变为原来的2倍；Hashtable默认 
初始大小11，扩容时将容量变为原来的2倍加1。 
** 6.是否有contains方法  **
HashMap没有contains方法；Hashtable包含contains方法，类似于containsValue。 
 7.父类不同。HashMap继承自AbstractMap；Hashtable继承自Dictionary。  
## 06. HashMap**数据结构**
**数据结构：**
**JDK1.7之前：数组+链表**
**JDK1.8之后：数组+链表+红黑树**
## 07.如何决定使用HashMap还是TreeMap
**HashMap基于散列桶（数组和链表）实现**
**TreeMap基于红黑树实现**
HashMap不支持排序； 
TreeMap默认是按照Key值升序排序的，可指定排序的比较器，主要用于存入元素时对元素进行自动排 
序。
HashMap大多数情况下有更好的性能，尤其是读数据。在没有排序要求的情况下，使用HashMap。 
** 都是非线程安全。  **
## 08.ArrayList和LinkedList的区别是什么👌
** ArrayList 基于动态数组实现的非线程安全的集合；  **
** LinkedList 基于双向链表实现的非线程安全的集合。	 **
扩容问题：ArrayList 使用数组实现，无参构造函数默认初始化长度为 10，数组扩容是会将原数组中 的元素重新拷贝到新数组中，长度为原来的 1.5 倍(扩容代价高)； 
LinkedList 不存在扩容问题，新增元素放到集合尾部，修改相应的指针节点即可。 
LinkedList 比 ArrayList 更占内存，因为 LinkedList 为每一个节点存储了两个引用节点，一个指向前一个元素，一个指向下一个元素。 
对于查询方法，一般 ArrayList 的速度要优于 LinkedList。因为 ArrayList 直接通过数组下标直接找到元素；LinkedList 要移动指针遍历每个元素直到找到为止。 
新增和删除元素，一般 LinkedList 的速度要优于 ArrayList。因为 ArrayList 在新增和删除元素时，可能扩容和复制数组；LinkedList 实例化对象需要时间外，只需要修改节点指针即可。 
LinkedList 集合不支持高效的随机访问（RandomAccess） 
ArrayList 的空间浪费主要体现在在list列表的结尾预留一定的容量空间；LinkedList 的空间花费则体现在它的每一个元素都需要消耗存储指针节点对象的空间。 
都是非线程安全，允许存放 null 
## 09.Array和ArrayList有何区别?
定义一个 Array 时，必须指定数组的数据类型及数组长度, 即数组中存放的元素个数固定并且类型相同。
ArrayList 是动态数组，长度动态可变，会自动扩容。不使用泛型的时候，可以添加不同类型元素。
## 10 .如何实现数组和List之间的转换?
List 转数组，使用 List 的 toArray 方法。无参 toArray 方法返回 Object 数组，传入初始化长度的数组对象，返回该对象数组 
## 11.Queue(队列)的add和offer方法有什么区别
Queue 中 add() 和 offer() 都是用来向队列添加一个元素。 
在容量已满的情况下，add() 方法会抛出IllegalStateException异常，offer() 方法只会返回 
false 。 
## 12. Queue的remove和poll方法有什么区别
Queue 中 remove() 和 poll() 都是用来从队列头部删除一个元素。 
在队列元素为空的情况下，remove() 方法会抛出NoSuchElementException异常，poll() 方法只 
会返回 null 。
## 13.Queue的element和peek方法有什么区别
Queue 中 element() 和 peek() 都是用来返回队列的头元素，不删除。 
在队列元素为空的情况下，element() 方法会抛出NoSuchElementException异常，peek() 方法 
只会返回 null。 
## 14.Iterator是什么，怎么使用，有什么特点
首先说一下**迭代器模式**，它是 Java 中常用的设计模式之一。用于顺序访问集合对象的元素，无需知道集合对象的底层实现。 
Iterator 是可以遍历集合的对象，为各种容器提供了公共的操作接口，隔离对容器的遍历操作和底层实现，从而解耦。 
**缺点**是增加新的集合类需要对应增加新的迭代器类，迭代器类与集合类成对增加。 
java.lang.Iterable 接口被 java.util.Collection 接口继承，java.util.Collection 
接口的 iterator() 方法返回一个 Iterator 对象 
next() 方法获得集合中的下一个元素 
hasNext() 检查集合中是否还有元素 
remove() 方法将迭代器新返回的元素删除 
forEachRemaining(Consumer<? super E> action) 方法，遍历所有元素 
## 15.Iterator和ListIterator有什么区别
ListIterator 继承 Iterator 
ListIterator 比 Iterator多方法 
1） add(E e) 将指定的元素插入列表，插入位置为迭代器当前位置之前 
2） set(E e) 迭代器返回的最后一个元素替换参数e 
3） hasPrevious() 迭代器当前位置，反向遍历集合是否含有元素 
4） previous() 迭代器当前位置，反向遍历集合，下一个元素 
5） previousIndex() 迭代器当前位置，反向遍历集合，返回下一个元素的下标 
6） nextIndex() 迭代器当前位置，返回下一个元素的下标 
使用范围不同，Iterator可以迭代所有集合；ListIterator 只能用于List及其子类 
ListIterator 有 add 方法，可以向 List 中添加对象；Iterator 不能 
ListIterator 有 hasPrevious() 和 previous() 方法，可以实现逆向遍历；Iterator不可以 
ListIterator 有 nextIndex() 和previousIndex() 方法，可定位当前索引的位置； Iterator不可以 
ListIterator 有 set()方法，可以实现对 List 的修改；Iterator 仅能遍历，不能修改 
## 16.怎样确保一个集合不能被修改
使用 JDK中java.util.Collections 类，** unmodifiable  **方法赋值原集合。 
当再修改集合时，会报错 java.lang.UnsupportedOperationException。从而确保自己定义的 
集合不被其他人修改
## 17.为什么基本类型不能做为HashMap的键值
Java中是使用泛型来约束 HashMap 中的key和value的类型的，HashMap<K, V> 
泛型在Java的规定中必须是对象Object类型的，基本数据类型不是Object类型，不能作为键值 
map.put(0, "ConstXiong")中编译器已将 key 值 0 进行了自动装箱，变为了 Integer 类型
## 18.HashMap的键值需要注意什么
HashMap 的 key 相等的条件是，条件 1 必须满足，条件2和3必须满足一个。 
key 的 hash 值相等 
内存中是同一个对象，即使用 == 判断 key 相等 
key 不为 null， 且使用 equals 判断 key 相等 
所以自定义类作为 HashMap 的 key，需要注意按照自己的设计逻辑，重写自定义类的 hashCode() 
方法和 equals() 方法。
## 19.Java中已经有数组类型，为什么还要提供集合（集合与数组区别）
** 数组的优点：  **
数组的效率高于集合类 
数组能存放基本数据类型和对象；集合中只能放对象 
** 数组的缺点：  **
不是面向对象的，存在明显的缺陷 
数组长度固定且无法动态改变；集合类容量动态改变 
数组无法判断其中实际存了多少元素，只能通过length属性获取数组的申明的长度 
数组存储的特点是顺序的连续内存；集合的数据结构更丰富 
** JDK 提供集合的意义：  **
集合以类的形式存在，符合面向对象，通过简单的方法和属性调用可实现各种复杂操作 
集合有多种数据结构，不同类型的集合可适用于不同场合 
弥补了数组的一些缺点，比数组更灵活、实用，可提高开发效率 
## 20.TreeSet的原理是什么，使用需要注意什么
TreeSet 基于 TreeMap 实现，TreeMap 基于**红黑树**实现 
特点： 
有序，唯一
添加、删除元素、判断元素是否存在，效率比较高
**使用方式：**
TreeSet 默认构造方法，调用 add() 方法时会调用对象类实现的 Comparable 接口的 compareTo() 方法和集合中的对象比较，根据方法返回的结果有序存储
TreeSet 默认构造方法，存入对象的类未实现 Comparable 接口，抛出 ClassCastException
TreeSet 支持构造方法指定 Comparator 接口，按照 Comparator 实现类的比较逻辑进行有序存储
## 21.HashSet实现原理是什么，有什么特点
HashSet 是基于 HashMap 实现的，查询速度特别快 
HashMap 是支持 key 为 null 值的，所以 HashSet 支持添加 null 值 
HashSet 存放自定义类时，自定义类需要重写 hashCode() 和 equals() 方法，确保集合对自定义 
类的对象的唯一性判断(具体判断逻辑，见 HashMap put() 方法，简单概括就是 key 进行 哈希。判 
断元素 hash 值是否相等、key 是否为同个对象、key 是否 equals。第 1 个条件为 true，2、3 
有一个为 true，HashMap 即认为 key 相同) 
** 无序、不可重复  **
## 22.HashSet和HashMap有什么区别
** HashMap  **
实现 Map 接口 
键值对的方式存储 
新增元素使用 put(K key, V value) 方法 
底层通过对 key 进行 hash，使用数组 + 链表或红黑树对 key、value 存储 
** HashSet  **
实现 Set 接口 
存储元素对象 
新增元素使用 add(E e) 方法 
底层是采用 HashMap 实现，大部分方法都是通过调用 HashMap 的方法来实现 
## 23.ArrayList list=new ArrayList(10)中的list扩容几次
该语句只是申明和实例了一个 ArrayList，指定了容量为 10，** 未扩容  **
## 24.ArrayList与LinkedList哪个插入性能高
LinkedList 插入性能高 
ArrayList 是基于数组实现的，添加元素时，存在扩容问题，扩容时需要复制数组，消耗性能 
LinkedList 是基于链表实现的，只需要将元素添加到链表最后一个元素的下一个即可 
## 25.LinkedHashMap、LinkedHashSet、LinkedList哪个最适合当Stack使用
**LinkedList适合**
Stack 是线性结构，具有先进后出的特点 
LinkedList 天然支持 Stack 的特性，调用 push(E e) 方法放入元素，调用 pop() 方法取出栈顶 
元素，内部实现只需要移动指针即可 
LinkedHashSet 是基于 LinkedHashMap 实现的，记录添加顺序的 Set 集合 
LinkedHashMap 是基于 HashMap 和 链表实现的，记录添加顺序的键值对集合 
如果要删除后进的元素，需要使用迭代器遍历、取出最后一个元素，移除，性能较差 
## 26.Map的实现类中，哪些是有序的，哪些是无序的，如何保证其有序性
Map 的实现类有 HashMap、LinkedHashMap、TreeMap 
HashMap是无序的 
LinkedHashMap 和 TreeMap 是有序的。LinkedHashMap 记录了添加数据的顺序；TreeMap 默认 
是升序 
LinkedHashMap 底层存储结构是哈希表+链表，链表记录了添加数据的顺序 
TreeMap 底层存储结构是二叉树，二叉树的中序遍历保证了数据的有序性 
## 27.TreeMap和TreeSet在排序时如何比较元素
TreeMap 会对 key 进行比较，有两种比较方式，第一种是构造方法指定 Comparator，使用 
Comparator中的compare() 方法进行比较；第二种是构造方法未指定 Comparator 接口，需要 key 
对象的类实现 Comparable 接口，用 Comparable中的compareTo() 方法进行比较 
TreeSet 底层是使用 TreeMap 实现 
## 28.Collections工具类中的sort方法如何比较元素
Collections 工具类的 sort() 方法有两种方式 
第一种要求传入的待排序容器中存放的对象比较实现 Comparable 接口以实现元素的比较 
第二种不强制性的要求容器中的元素必须可比较，但要求传入参数 Comparator 接口的子类，需要重写 
compare() 方法实现元素的比较规则，其实就是通过接口注入比较元素大小的算法，这就是回调模式的 
应用 
## 29.List、Map、Set三个接口，存取元素时，各有什么特点
List 以索引来存取元素，元素可重复 
Set 不能存放重复元素 
Map 保存键值对映射，映射关系可以一对一、多对一 
List 有基于数组和链表实现两种方式 
Set、Map 容器有基于哈希存储和红黑树两种方式实现 
Set 基于 Map 实现，Set 里的元素值就是 Map 里 key
## 30.Map的遍历方式
Map 的 keySet() 方法，单纯拿到所有 Key 的 Set 
Map 的 values() 方法，单纯拿到所有值的 Collection 
keySet() 获取到 key 的 Set，遍历 Set 根据 key 找值（不推荐使用，效率比下面的方式低，原因是多出了根据 key 找值的消耗） 
获取所有的键值对集合，迭代器遍历 
获取所有的键值对集合，for 循环遍历 
## 31.说一下HashMap的实现原理👏
HashMap 基于 Hash 算法实现，通过 put(key,value) 存储，get(key) 来获取 value 
当传入 key 时，HashMap 会根据 key，调用 hash(Object key) 方法，计算出 hash 值，根据hash 值将 value 保存在 Node 对象里，Node 对象保存在数组里 
当计算出的 hash 值相同时，称之为 hash 冲突，（HashMap 的做法是用链表和红黑树存储相同 hash值的 value ）
当 hash 冲突的个数：小于等于 8 使用链表；大于 8 时，使用红黑树解决链表查询慢的问题 
上述是 JDK 1.8 HashMap 的实现原理，并不是每个版本都相同，比如 JDK 1.7 的 HashMap 是基于数组 + 链表实现，所以 hash 冲突时链表的查询效率低 
hash(Object key) 方法的具体算法是 (h = key.hashCode()) ^ (h >>> 16)，经过这样的运算，让计算的hash 值分布更均匀 
## 32.ConcurrentHashMap了解吗，说说实现原理
*_实现原理 *_   **JDK 1.7**：  _**ConcurrentHashMap 是通过数组 + 链表**实现 ,由 Segment 数组和 Segment 元素里对应多个HashEntry 组成 
value 和链表都是 volatile 修饰，保证可见性 
ConcurrentHashMap 采用了*分段锁_*技术，分段指的就是 Segment 数组，其中 Segment 继承于 
ReentrantLock 
理论上 ConcurrentHashMap 支持 CurrencyLevel (Segment 数组数量)的线程并发，每当一个线程占用锁访问一个 Segment 时，不会影响到其他的 Segment 
** JDK 1.8：  ***_**ConcurrentHashMap 是通过**数组+链表+红黑树_*实现 
抛弃了原有的 Segment 分段锁，采用了 CAS + synchronized 来保证并发安全性 
HashEntry 改为 Node，作用相同 
val next 都用了 volatile 修饰
