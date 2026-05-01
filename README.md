# C语言的学习
  以下是本人在学习C语言写的一些代码和个人见解，主要用于记录学习历程。
## 一· 回调函数
可以把回调函数看作是贴标签。
以下是代码呈现：
```c
#include <stdio.h>

typedef void (*Task)(int) ;
void printSquare(int x) {printf("%d ",x*x) ; }
int arr[] = {1,2,3,4} ;
int len = sizeof(arr)/sizeof(int) ;

void proccessArrary(int arr[],int len,Task task)
{
    for(int i=0 ;i<=len-1 ;i++)
    {
        task(arr[i]) ;
    }
}

int main()
{
    proccessArrary(arr ,4 ,printSquare) ;
    return 0 ;
}
```
```c
#include <stdio.h>
#include <stdbool.h>
typedef int(*Task)(int,int) ;
int max(int a,int b) {return (a>b)?a:b ;}

int compare(int a ,int b ,Task task)
{
    int c = task(a,b) ;
    return c ;
}

int main()
{
    bool a = compare(5,10,max) ;
    printf("%d",a) ;
    return 0 ;
}
```
## 二· 结构体
以下是代码呈现：

```c
#include<stdio.h>

struct Robot{
    int health ;
    int a ;
    int b ;
} ;

struct Robot r1 ;

void damage(struct Robot *r){
    r -> health -= 10 ;
}

int main()
{
    r1.health = 100 ;
    damage(&r1) ;
    printf("%d",r1.health) ;
    return 0 ;
}
```

```c
#include <stdio.h>

struct Motor{
    int id ;
    float speed ;
    float angle ;
};

void setAngle(struct Motor *m,float s){
    m ->angle = s ;
}

void setSpeed(struct Motor *m,float s){
    m->speed = s ;
}

int main()
{
    struct Motor m1 = {1 , 0.0, 90} ;
    setSpeed(&m1,100.0) ;
    setAngle(&m1,80.0) ;
    printf("电机%d 转速；%.1f 角度：%.1f",m1.id , m1.speed,m1.angle) ;
    return 0 ;
}
```
## 三· 二分查找
```c
#include <stdio.h>

int erfenfa(int arr[],int len,int target)
{
    int left = 0 ;
    int right = len - 1 ;

    while(left <= right){
        int mid = left + (right - left)/2 ;

        if (arr[mid] == target)
            return mid ;
        else if (arr[mid] < target)
            left = mid + 1 ;
        else 
            right = mid - 1 ;
    }
    return -1 ;
}

int main()
{
    int arr[] = {1,2,3,4,5,6};
    int len = sizeof(arr)/sizeof(int) ;
    int a = 0 ;
    a = erfenfa(arr,len,5) ;
    printf("%d\n",a) ;
    return 0 ;
}
```
