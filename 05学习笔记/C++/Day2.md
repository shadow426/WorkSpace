1：总结了Day1
2-3：圆类和学生类，已会跳过
4：


### 静态内联函数

在头文件中定义内联函数时，通常会用 `static inline` 来避免链接冲突：



Copy

// myheader.h
static inline int multiply(int a, int b) {
    return a * b;
}


