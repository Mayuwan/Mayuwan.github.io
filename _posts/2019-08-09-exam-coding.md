---
layout: post
title:  "猿辅导笔试第一题（解压压缩的字符串）"
date:   2018-08-03 22:14:54
categories: 笔试
tags: 编程
---

* content
{:toc}

## 前言

好久没有更新github博客，一直忙着学习，等有时间想把很多知识点跟大家分享一下




### 解压压缩的字符串

####问题描述
一个字符串由字母和数字，（，）组成。数字>=2，表示前面字母/字符串出现的次数。其中括号可以嵌套括号。

A11B解压为AAAAAAAAAAAB

FD(SD)2FD解压为FDSDSDFD

A2B3C4D解压为AABBBCCCCD


#### 解题思路

题目中压缩的字符串我称为原串，解压的串我称为新串

1.先不考虑括号的情况。

如果当前字符为字母，就往新串里添加当前字符。

如果当前字符为数字，因为数字可能出现多位，那就找出
整个数字，比如找A11B中的11，找到11，说明11之前的那个字符出现的次数为11。
11前面的字符为A，那就往新串里加11个A。

2.考虑括号的情况，就是有重复字符串的情况

有括号，就有括号匹配，括号匹配使用的数据结构为栈。

重点是栈里存的是什么？应该存主串里'('的位置，还是什么呢？

因为新串的长度一直在发生变化，那么重复的字符串应该根据新串中的字符串来添加。比如：字符串
(A2B)2，其中A2B会变成AAB放在新串中，那么应该使用新串中的AAB根据重复次数添加到新串中。

#### 代码

```js

import java.util.*;
/**
 * 解压 压缩的字符串
 * */
public class DecodeString {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        for (int i=0;i<=n;i++) {// 注意，如果输入是多个测试用例，请通过while循环处理多个测试用例
            String line = in.nextLine();
            System.out.println(parse(line));
        }
    }
    private static String parse(String str) {
        StringBuilder sb  = new StringBuilder();
        LinkedList<Integer> len = new LinkedList();
        String temp="";
        for(int i=0;i<str.length();i++){
            if(str.charAt(i) ==   '('){
                len.add(sb.length());
                continue;
            }

            if (str.charAt(i) ==   ')') {
                int leftIndexNew = len.remove(len.size()-1);

                temp = sb.substring(leftIndexNew);
                i++;
            }

            int start = i;
            while(i<str.length() && str.charAt(i)<='9' && str.charAt(i)>='0'){
                i++;
            }
            if( i-start >= 1){
                int count = Integer.valueOf(str.substring(start,i));//重复次数
                for(int j=0;j<count-1;j++){
                    if(temp == ""){
                        sb.append(str.charAt(start-1));
                    }
                    else {
                        sb.append(temp);
                    }
                }
                temp = "";
                i--;
            }
            else {
                    sb.append(str.charAt(i));
            }
        }
        return sb.toString();
    }

}
```