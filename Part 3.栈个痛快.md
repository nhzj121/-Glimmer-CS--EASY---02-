# Part 3.栈个痛快
## 解密过程
<p>基本思路：通过数组来实现栈的特性，即后进先出。</p>
<p>首先是通过数组来存储所需的数据，即Josephus.out中的数链和CS-EASY-02-2.txt中的字符串，分别存储在不同的数组中（程序中采用提取字符串的方式，所以数字还需要由字符变回数字）。</p>
<p>然后建立奇数偶数的判断，建立以数字数目建立外循环。</p>
<p>主体部分还引入了一个用于存放数据的数组（array[]），大致操作过程为将字母数组(sc[])中的数据对应赋值给array[]。<br>输出时输出时先计算插入过的数据数目，从最后一位开始操作，模拟后进先出的效果，同时将输出位赋值为1，保证可以计算数目的同时，在输出时可以略过<br></p>

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    char sr[36],sc[27],array[27]={0};
    int count=0,i=0;
    FILE *fp, *fpp;
    fp=fopen("C:\\Users\\19522\\Desktop\\Josephus.out","r");
    fpp=fopen("C:\\Users\\19522\\Desktop\\CS-EASY-02-2.txt","r");
    fscanf(fp,"%s",sr);
    fscanf(fpp,"%s",sc);
    fclose(fp);
    fclose(fpp);
    for(int f=0;f<35;f++)
    {
        sr[f] = sr[f] - '0';
        if(f%2 == 0)
        {
            for(int p=0;p < sr[f];p++)
            {
                array[count] = sc[count];
                count++;
            }
        }
        else
        {

            while(array[i] != 0) i++;
            for(int q=0;q < sr[f];q++)
            {
                if(array[i-1] != 1 && array[i-1] != 0)
                {
                    printf("%c",array[i-1]);
                    array[i-1] = 1;
                    i--;
                }
                else if(i > 0)
                {
                    i--;
                    q--;
                }
                if(i == 0 )
                {
                    break;
                }
            }
        }
    }
}
```
## 解密结果
```
