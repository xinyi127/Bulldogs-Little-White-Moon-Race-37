```c++
/*
int 数组可开的数量远大于 long long 
*/
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<algorithm>
using namespace std;
#define scnaf scanf
#define ll long long
const int N=5e7+5;
int a[N*2],v[N],p[N];
void prime()
{
    int i,j,k=0;//5e7*2==1e8
    for(i=2;i<=N;i++)
    {
        if(!v[i])
            p[++k]=i;
        for(j=1;p[j]*i<=N;j++)
        {
            v[p[j]*i]=1;
            if(i%p[j]==0)
                break;
        }
    }
    p[0]=k;
}
int main()
{
    int t,i,j,k,n,x,y;
    prime();
    for(i=1;p[i]*2<N*2&&i<=p[0];i++)
    {
        for(j=1;p[i]*p[j]<N*2&&j<=p[0];j++)
            a[p[i]*p[j]]=1;
    }
    for(i=2;i<N*2;i++)
        a[i]+=a[i-1];
    scnaf("%d",&t);
    while(t--)
    {
        scnaf("%d%d",&x,&y);
        printf("%d\n",a[y]-a[x-1]);
    }
    return 0;
}
```

