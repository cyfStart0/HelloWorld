#ThoughtWorks作业--陈亚飞
联系方式：18844183109<br>
邮 箱: small__talk@163.com<br>
##题目
    文本处理是非常常见但又非常重要的任务。其中操作纷繁复杂。而今天我们的目标就是制作一个小型的文本预处理器。其主要功能就是对文本进行预处理以便后续进行固定宽度的排版。为了方 便说明，我们定义如下的概念： 
* 空白字符（white space）：指空格 ' '。 
* 文本字符（character）：指大写或者小写的英文字母。
* 节（segment）：指一串（大于或者等于一个）连续的空白字符或者文本字符。 

我们的文本处理器的功能还很朴素，无法处理除 空白字符 和 文本字符 之外的字符。 

我们将会使用一个固定长度作为宽度进行排版。大于这个宽度的字符会被折行。而折行不会显示 任何连字符（例如 “-”），也无需对 空白字符 进行额外处理。例如，假设我们规定最大宽度为 30，则 "The main theme of education in engineering school is learning to teach yourself" 将排版为：<br> 
    
                        The main theme of education in
                        engineering school is learnin 
                        g to teach yourself 
##要求 
    现在请书写一个函数，该函数的输入为两个参数： 
* 需要处理的文本 
* 排版宽度。 

该函数的返回值为预处理后的文本。预处理后的文本为每一节，及其所在的行号。中间以分号隔 开。若一个节跨越了多行，则行号用逗号隔开，并从小到大进行排列。<br> 
    
例如，假设输入为：The main theme of education in engineering school is learning to teach yourself，并且排版宽度指定为 30，则返回： 
    
    
    
    The(1); (1);main(1); (1);theme(1); (1);of(1); (1);education(1); (1);in(1); 
    (2);engineering(2); (2);school(2); (2);is(2); (2);learning(2,3); (3);to(3); 
    (3);teach(3); (3);yourself(3); 

又例如，假设输入为："So   many whitespaces"，而排版宽度为 10，则返回： 
    
    So(1);   (1);many(1); (1);whitespaces(2,3); 
##异常处理 
 * 如果输入文本中包含有异常的字符，则返回 "ERROR: Invalid character detected!"。 
 * 输入的宽度只能为 [10, 80] 之间的整数。如果超出这个范围则返回："ERROR: Width out of range!" 
 
##程序说明
* 工程名为ThoughtWorks,下面有cn.thoughtworks包，包含了TextProcessor类。
* 工程中imgs文件夹下为测试用例和异常处理运行结果的截图。
* 文本处理器的类定义为TextProcessor类
* TextProcessor类中包含如下方法：<br>


```java

/**
 * main函数，程序入口
 * @param args
*/
public static void main(String[] args);
/**
 * 文本处理函数，是程序的核心函数，
 * 返回最终处理的结果
 * @param text
 * @param width
 * @return
 */
public static String process(String text, int width);
/**
 * 对每行的最后一个字符单独处理，返回每行处理后的最终结果。
 * @param stb
 * @param list
 * @param j
 * @return
 */
public static StringBuffer handleLastChar(StringBuffer stb,ArrayList<String> list,int j);
/**
 * 将文本按照给定宽度截取并返回
 * @param text
 * @param width
 * @return
 */
public static ArrayList<String> subText(String text,int width)
```
##程序运行
* 将项目导入到eclipse中，即可运行


##运行结果：
* 测试用例1：
        The main theme of education in engineering school is learning to teach yourself
* 运行结果：
        The(1); (1);main(1); (1);theme(1); (1);of(1); (1);education(1); (1);in(1); 
        (2);engineering(2); (2);school(2); (2);is(2); (2);learning(2,3); (3);to(3); 
        (3);teach(3); (3);yourself(3);
* 运行截图：

    ![用例1](ThoughtWorks/imgs/测试用例1.JPG "用例1")

* 测试用例2：
        So   many whitespaces
* 运行结果：
        So(1);   (1);many(1); (1);whitespaces(2,3);
* 运行截图：

    ![用例2](ThoughtWorks/imgs/测试用例2.JPG "用例2")
    
* 结论：
    运行结果与预期一致。
##异常处理：
* 异常1：输入文本中包含有异常的字符：
* 返回结果：
        ERROR: Invalid character detected!
* 运行截图：

    ![异常1](ThoughtWorks/imgs/异常处理1.JPG "异常1")


* 异常2：输入的宽度只能为 [10, 80] 之间的整数。不能超出这个范围：
* 返回结果：
        ERROR: Width out of range!
* 运行截图：

    ![异常2](ThoughtWorks/imgs/异常处理2.JPG "异常2")

* 结论：
    能够处理所要求的异常。

