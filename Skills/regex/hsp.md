# Resource
- [hsp](https://www.bilibili.com/video/BV1Eq4y1E79W?spm_id_from=333.999.0.0)
- hsp讲正则表达式的Java实现版本

# Regex
- Java实现的转义字符\都需要用\\来代替
- Java默认贪婪匹配

## 捕获
- (?<name>pattern), 命名捕获, 通过matcher.group(name)来输出
- (?:pattern), industr(?:y|ies)可以匹配industry|industries, 非捕获分组, 不会存到groups里
- (?=pattern), A(?=B|C), 只匹配ABorAC情况下的A, 其他的A不匹配, 非捕获分组
- (?=pattern), A(?!B|C), 不匹配ABorAC下的A, 匹配其他的, 非捕获分组

## frequently-used class
- java.util.regex包中 Pattern类, Matcher类, PatternSyntaxException类
- Pattern类
    - pattern对象是一个正则表达式对象. Pattern类没有公共构造方法, 要创建一个Pattern对象, 调用公共静态方法, 返回一个Pattern对象, 该方法接受一个正则表达式(String)作为它的第一个参数
    - Pattern r = Pattern.compile(str);
    - boolean isMatch = Pattern.matches(patternStr, textStr); 判断textStr是否是patternStr的一个整体匹配, 注意是整体匹配, 用来验证textStr的格式
- Matcher类
    - Matcher对象是对输入字符串进行解释和匹配的引擎. 也没有公共构造方法, 调用Pattern对象的matcher方法获得一个Matcher对象
- PatternSyntaxException类
    - 非强制异常类, 表示正则表达式模式中的语法错误

## Example
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Hello{
    public static void main(String[] args){
        String content = "abc def abc ghijk def lmn opq";
        // 先创建一个Pattern对象, 模式对象, 可以理解成就是一个正则表达式对象
        Pattern pattern = Pattern.compile("[a-zA-Z]+");
        // 再创建一个匹配器对象, 匹配器按照模式到文本中去匹配, 找到就返回true, 否则返回false
        Matcher matcher = pattern.matcher(content);
        while (matcher.find()) {
            System.out.println("find: " + matcher.group(0));
//            public String group(int group) {
//                if (first < 0)
//                    throw new IllegalStateException("No match found");
//                if (group < 0 || group > groupCount())
//                    throw new IndexOutOfBoundsException("No group " + group);
//                if ((groups[group*2] == -1) || (groups[group*2+1] == -1))
//                    return null;
//                return getSubSequence(groups[group * 2], groups[group * 2 + 1]).toString();
//            }
//            可以看出matcher.group()方法是如何获得子串的
        }
//         matcher.find() 做了什么呢
//         1. 根据指定的模式, 定位满足匹配的子串的位置
//         2. 找到后将子串的开始索引记录到matcher对象的一个 int[] groups; 属性中
//              将子串的开始索引记录到groups[0], 结束索引+1记录到groups[1]
//         3. 同时记录oldLast的值为结束索引+1, 下次调用matcher.find()时从这个位置开始找, 找到的下一个子串会覆盖groups[0]和[1]
//         4. groups[2]开始的位置用来保存分组的结果, 两个一组表示一个分组
    }
}
```