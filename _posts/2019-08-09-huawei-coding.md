---
layout: post
title:  "华为笔试题第三题"
date:   2019-10-30 15:58:54
categories: ubuntu
tags: 翻墙
---

* content
{:toc}

## 前言

好久没有更新github博客，一直忙着学习，等有时间想把很多知识点跟大家分享一下




### 判断逻辑表达式的结果

#### 问题描述

一个字符串由0，1，&，|，！，（，）组成，表示一个逻辑表达式，输出该表达式的结果。优先级 () > ！> & > |

!(1&0)|(0&1)的结果为1

!!0|1&1的结果为1

!(1&0)|((0&1)|(0|1))的结果为1


#### 解题思路

该题是变相的缩短字符串。

题目中输入字符串我称为原串，得到的串我称为新串

1.先不考虑括号的情况。

根据优先级，1）考虑！。从右边往左遍历字符串（因为!可能出现多次），比如 !!0，先将 !0 变成1，再将 !1 变成0

2）考虑&。从左往右，将三位字符变成一位字符。

3）考虑|。从左往右，将三位字符变成一位字符。

2.考虑括号的情况

有括号，就有括号匹配，括号匹配使用的数据结构为栈。

栈里存的是主串里'('的位置，当pop出栈顶的元素时，那么'('与'）'之间肯定是没有括号了，'('与'）'之间的串
使用情况1处理，将'('与'）'的字符串变成一个字符。

#### 代码

```js

import java.util.Stack;

public class huawei3 {

    public static void main(String[] args) {

        String str1 = "!(1&0)|(0&1)";
        String str2 = "!!0|1&1";
        String str = "!(1&0)|((0&1)|(0|1))";
        StringBuilder sb= new StringBuilder().append(str);
        dfs(sb);
        System.out.println( parse(sb.toString()));
    }

    private static String parse(String substring) {
       
        StringBuilder sb = new StringBuilder().append(substring);
        for(int i=sb.length()-1;i>=0;i--){
            if(sb.charAt(i) == '!'){
                String temp;
                if(sb.charAt(i+1)=='0')
                     temp = "1";
                else
                    temp = "0";
                sb.replace(i,i+2,temp);
            }
        }

        for(int i=0;i<sb.length();i++){
            if(sb.charAt(i) == '&'){
                int leftNum = sb.charAt(i-1) - '0';
                int rightNum = sb.charAt(i+1)-'0';
                String temp  = String.valueOf(leftNum & rightNum );
                sb.replace(i-1,i+2,temp);
            }
        }

//        System.out.println(sb.toString());
        for(int i=0;i<sb.length();i++){
            if(sb.charAt(i) == '|'){
                int leftNum = sb.charAt(i-1)- '0';
                int rightNum = sb.charAt(i+1)- '0';
                String temp  = String.valueOf(leftNum | rightNum );
                sb.replace(i-1,i+2,temp);
            }
        }
//        System.out.println(sb.toString());
        return sb.toString();
    }
    private static void dfs(StringBuilder sb){
        Stack<Integer> stack = new Stack();
        for(int i=0;i<sb.length();i++){
            if(sb.charAt(i)== '('){
                stack.push(i);
            }
            else if(sb.charAt(i)== ')'){
                Integer leftP =stack.pop();
                String res = parse(sb.substring(leftP+1,i));
                sb.replace(leftP,i+1,res);
                dfs(sb);
            }
        }
    }
}


}
```