#include <stdio.h>
#include <string.h>

void firstfit(int bsize[],int psize[],int n,int m)
{
    int allocation[n];
    memset(allocation,-1,sizeof(allocation));
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<m;j++)
        {
            if(bsize[j]>=psize[i])
            {
                allocation[i]=j;
                bsize[j]-=psize[i];
                break;
            }
        }
    }
    
    printf("P NO\tP SIZE\tALLOCATION");
    for(int i=0;i<n;i++)
    {
        printf("\n%d\t%d",i+1,psize[i]);
        if(allocation[i]!=-1)
        {
            printf("\t%d",allocation[i]+1);
        }
        else
        {
            printf("\t-");
        }
    }
    
    printf("\nThe free blocks are->");
    for(int i=0;i<m;i++)
    {
        printf("%d ",bsize[i]);
    }
}

void main()
{
    int n,m;
    printf("Enter the size of the block array:");
    scanf("%d",&m);
    printf("Enter the size of the process array:");
    scanf("%d",&n);
    int psize[n],bsize[m];
    printf("Enter the block sizes in order:");
    for(int j=0;j<m;j++)
    {
        scanf("%d",&bsize[j]);
    }
    printf("Enter the process sizes in order:");
    for(int i=0;i<n;i++)
    {
        scanf("%d",&psize[i]);
    }
    
    firstfit(bsize,psize,n,m);
}
