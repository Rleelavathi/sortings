#include <stdio.h>
void merging(int a[],int low,int mid,int high);
void mergesort(int a[],int low,int high);

void main()
{
    int a[20],n,i;
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        scanf("%d",&a[i]);
    }
    for(i=0;i<n;i++)
    {
        printf("%5d",a[i]);
    }
    mergesort(a,0,n-1);
    printf("after sort");
    for(i=0;i<n;i++)
    {
        printf("%d",a[i]);
        printf("\n");
    }
}
void mergesort(int a[],int low,int high)
{
    int mid;
    if(low<high)
    {
        mid=(low+high)/2;
        mergesort(a,low,mid);
        mergesort(a,mid+1,high);
        merging(a,low,mid,high);
        
    }
}
void merging(int a[],int low,int mid,int high)
{
    int i,j,k;
    int c[10];
    i=low;
    j=mid+1;
    k=low;
    while((i<=mid)&&(j<=high))
    {
        if(a[i]<=a[j])
        {
            c[k++]=a[i++];
        }
        else
        {
            c[k++]=a[j++];
        }
    }
    while(i<=mid)
    {
        c[k++]=a[i++];
    }
    while(j<=high)
    {
        c[k++]=a[j++];
    }
    for(i=low;i<=high;i++)
    {
        a[i]=c[i];
    }
    
}
