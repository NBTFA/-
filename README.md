# java校招学习记录
## java基础
### 一次编写，到处运行
#### JVM
1. JVM是java跨平台的关键
2. java的运行：.java --> .class --> 机器码 运行   
 -----------------编译器-----JVM翻译-------   
3. JVM不同平台需要不同的版本，而java程序是在JVM上运行，所以可以跨平台

### Java类
1. 一个java文件里可以有多个class，但是只能有一个public class
   public class的名称要与.java一致
2. 修饰variable和method
   - private：可以被该class内部访问
   - default：可以被该class内部访问，也可以被同一个package下其他class访问
   - protected：可以被该class内部访问，也可以被同一个package下其他class访问，也可以被子类访问
   - public：可以被任意访问
3. 修饰class
   - default：该class可以被同一package下其他class访问
   - public：可以被任意访问
4. static
   - 被static修饰的变量和方法，每次加载class的时候，只会为其分配一次内存，而没有被static修饰的可以有多个

### Java数据类型
> 除了boolean，其他都为数字类型，可以进行类型转换

1. 整数类型
   - byte：1 byte（8 bits），数据范围```-2^7 ~ 2^7-1```
     - 默认值：0
   - short：2 byte（16 bits），数据范围```-2^15 ~ 2^15-1```
     - 默认值：0
   - int：4 byte（32 bits），数据范围```-2^31 ~ 2^31-1```
     - 默认值：0
   - long：8 byte（64 bits），数据范围```-2^63 ~ 2^63-1```
     - 默认值：0L
2. 浮点类型
   - float：4 byte（32 bits），数据范围```-3.4*10^38 ~ 3.4*10^38```
     - 默认值：0.0F
   - double：8 byte（64 bits），数据范围```-1.8*10^308 ~ 1.8*10^308```
     - 默认值：0.0
3. 字符类型
   - char：2 byte（16 bits），数据范围```\u0000 ~ \uffff```
     - 默认值：\u0000
4. 布尔类型
   - boolean：不同jvm不同
     - 默认值：false

### 包装类（wrapper class）
包装类将基础数据类型封装成对象   
因此可以**将基本数据类型存储到Object[]数组或集合中**
<table>
    <tr>
      <th>基本类型</th>
      <th>包装类</th>
    </tr>
    <tr>
      <td>byte</td>
      <td>Byte</td>
    </tr>
  <tr>
      <td>short</td>
      <td>Short</td>
    </tr>
  <tr>
      <td>int</td>
      <td>Integer</td>
    </tr>
  <tr>
      <td>long</td>
      <td>Long</td>
    </tr>
  <tr>
      <td>float</td>
      <td>Float</td>
    </tr>
  <tr>
      <td>double</td>
      <td>Double</td>
    </tr>
  <tr>
      <td>char</td>
      <td>Character</td>
    </tr>
  <tr>
      <td>boolean</td>
      <td>Boolean</td>
    </tr>
</table>

Integer、Double不能直接进行比较，这包括：
  - 不能用==进行直接比较，因为它们是不同的数据类型；
  - 不能转为字符串进行比较，因为转为字符串后，浮点值带小数点，整数值不带，这样它们永远都不相等；
  - 不能使用compareTo方法进行比较，虽然它们都有compareTo方法，但该方法只能对相同类型进行比较。
  - 解决办法
    - 因为Integer和Double都继承自Number，所以可以将他们都先转换成double
      
    ```
    Integer i = 100;
    Double d = 100.00;
    System.out.println(i.doubleValue() == d.doubleValue());
    ```

### 面向对象
三大特征
1. 封装：使用```private```对object属性进行隐藏，并隐藏具体细节
   - 为了增强安全性和简化编程，并提供对外使用方法
   - 让使用者只能通过事先预定的方法访问数据，限制对成员变量的不合理访问
2. 多态：同一个行为（方法）有不同的表现形式
   - 子类对象可以直接赋给父类变量，但运行时依然表现出子类的行为特征
   - ```
     class Driver {
         void drive(Car car){ ... }
         void drive(Bus bus){ ... }
         void drive(Truck truck){ ... }
     }
     ```
3. 继承：使用```extends```使子类继承父类的特征（属性）和行为（方法）
