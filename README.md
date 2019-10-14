4、leetcode686.重复叠加字符串匹配
==
解法一：
--  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/14 19:33
 * @descriptor  686. 重复叠加字符串匹配
 */
public class RepeatedStringMatch_686 {
    /**
     * 如果A的长度大于等于B的长度，这时B是A的重复叠加字符串只有两种情况，第一种就是本身B就是A的子串（比如A = “abcdefg”, B = “bcd”），第二种就是B是两个A的子串(A = “abcdefg”, B = “efgab”, 2 * A == “abcdefgabcdefg”)。
     * 如果A的长度小于B的长度，这时B是A的重复子串，则A的重复次数不超过 Bsize / Asize + 2。其中“Bsize / Asize”代表的B串中间A重复的次数，“+2”代表的首尾各添加一个A串。
     * 如果B是n个A叠加之后的一个子串，那么最极端的情况也就是B的头部是A的后面一部分，B的尾部是A的前面一部分，比如：
     * A = "abc" ； B=  "cabcabca"；
     */
    public static int repeatedStringMatch(String A, String B) {
        StringBuilder builder = new StringBuilder();
        for (int i = 1; i <= B.length()/A.length()+2; i++) {
            builder.append(A);
            if(builder.toString().contains(B))
                return i;
        }
        return -1;
    }
    public static void main(String[] args) {
        String A = "abc",B = "cabcabca";
        int i = repeatedStringMatch2(A, B);
        System.out.println(i);
    }
}
</pre>
==
解法二：
--    
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/14 19:33
 * @descriptor  686. 重复叠加字符串匹配
 */
public class RepeatedStringMatch_686 {
    //先累加到B长度，在添加一次即可。
    public static int repeatedStringMatch2(String A, String B) {
        StringBuilder builder = new StringBuilder();
        int count = 0;
        while(builder.length()<B.length()){
            count++;
            builder.append(A);
        }
        if(A.toString().contains(B))
            return count;
        if(builder.append(A).toString().contains(B))
            return ++count;
        return -1;

    }
    public static void main(String[] args) {
        String A = "abc",B = "cabcabca";
        int i = repeatedStringMatch2(A, B);
        System.out.println(i);
    }
}
</pre>
