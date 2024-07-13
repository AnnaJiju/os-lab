# os-lab
//to implement first come first serve CPU scheduling

#include<stdio.h>

void main()
{
    int i,temp,j,n;
    //Inputing the processes
    printf("Enter the no of processes:");
    scanf("%d",&n);
    int at[n],bt[n],tat[n],ct[n],wt[n],p[n];
    printf("Enter the process no:s in order:");
    for(i=0;i<n;i++)
    {
        scanf("%d",&p[i]);
    }
    //inputing the arrival time
    printf("Enter the arrival times in order:");
    for(i=0;i<n;i++)
    {
        scanf("%d",&at[i]);
    }
    //inputing the burst time
    printf("Enter the burst times in order:");
    for(i=0;i<n;i++)
    {
        scanf("%d",&bt[i]);
    }
    //sorting with respect to the arrival time
    for(i=0;i<n-1;i++)
    {
        for(j=0;j<n-i-1;j++)
        {
            if(at[j]>at[j+1])
            {
                temp=bt[j];
                bt[j]=bt[j+1];
                bt[j+1]=temp;
                
                temp=at[j];
                at[j]=at[j+1];
                at[j+1]=temp;
                
                temp=p[j];
                p[j]=p[j+1];
                p[j+1]=temp;
            }
        }
    }
    //checking for the order of the execution
    int t=0,completed=0,complete[n];
    for(i=0;i<n;i++)
    {
        complete[i]=-1;
    }
    while(completed<n)
    {
        int flag=0;
        for(i=0;i<n;i++)
        {
            if(at[i]<=t && complete[i]!=1)
            {
                t+=bt[i];
                ct[i]=t;
                tat[i]=t-at[i];
                wt[i]=tat[i]-bt[i];
                flag=1;
                completed++;
                complete[i]=1;
                break;
            }
        }
        if(flag==0)
        {
            t++;
        }
    }
    //printing the ganrt chart
    int totaltat=0,totalwt=0;
    printf("\nPNO\tAT\tBT\tCT\tTAT\tWT");
    for(i=0;i<n;i++)
    {
        printf("\n%d\t%d\t%d\t%d\t%d\t%d",p[i],at[i],bt[i],ct[i],tat[i],wt[i]);
        totaltat+=tat[i];
        totalwt+=wt[i];
    }
    printf("\nAvg TAT=%2f",(float)totaltat/n);
    printf("\nAvg WT=%2f",(float)totalwt/n);
}
