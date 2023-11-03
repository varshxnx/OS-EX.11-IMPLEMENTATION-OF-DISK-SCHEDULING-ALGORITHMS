# OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS

## DISK SCHEDULING FIRST COME FIRST SERVE
## AIM:
To write a program for the first come first serve method of disc scheduling.
## ALGORITHM:
1. Initialize an array RQ to store disk requests and variables n, TotalHeadMoment, and initial.
2. Prompt the user to input the number of requests (n) and the request sequence (RQ).
3. Prompt the user to input the initial head position (initial).
4. Calculate TotalHeadMoment by iterating through the requests, adding the absolute difference between each request and the current head position to TotalHeadMoment, and updating the head position.
5. Print the TotalHeadMoment as the result of the FCFS disk scheduling.
## PROGRAM:
```C
#include <stdio.h>
#include <stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial;
printf ("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
{
scanf("%d",&RQ[i]);
}
printf("Enter initial head position\n");
scanf("%d",&initial);

for(i=0;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
printf("Total head moment is %d",TotalHeadMoment);
return 0;
}
```
## OUTPUT:
![output1](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/0868dcea-8d32-4ec7-af65-4bad297d4fde)
## RESULT:
Thus, the implementation of the C program for first come first serve disc scheduling has been successfully executed.
## DISK SCHEDULING SHORTEST SEEK TIME FIRST
## AIM:
To write a program for the shortest seek time first method of disc scheduling.
## ALGORITHM:
1. Initialize variables and arrays for requests, total head movement, initial head position, and a counter.
2. Input the number of requests, the request sequence, and the initial head position from the user.
3. Find the nearest request by looping through the requests, calculating the absolute difference from the current head position, and updating the head position based on the closest request.
4. Repeat this process until all requests are processed, marking completed requests with a large number.
5. Print the total head movement as the result of the SSTF disk scheduling.
## PROGRAM:
```C
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial,count=0;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
while(count!=n)
{
int min=1000,d,index;
for(i=0;i<n;i++)
{
d=abs(RQ[i]-initial);
if(min>d)
{
min=d;
index=i;
}
}
TotalHeadMoment=TotalHeadMoment+min;
initial=RQ[index];
RQ[index]=1000;
count++;
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
## OUTPUT:
![output2](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/d1a2b610-b9f8-4769-8d57-444166bda691)
## RESULT:
Thus, the implementation of the C program for shortest seek time first disc scheduling has been successfully executed.
## DISK SCHEDULING SCAN OR ELEVATOR
## AIM:
To write a program for the scan method of disc scheduling.
## ALGORITHM:
1. Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
2. Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
3. Sort the request array in ascending order to facilitate the SCAN algorithm.
4. Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
5. Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the SCAN disk scheduling algorithm.
## PROGRAM:
```C
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
// last movement for max size
TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
initial = size-1;
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);
initial =0;
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
## OUTPUT:
![output3](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/37ad4a9e-53b1-41f0-9d77-a8b7f39fea2a)
## RESULT:
Thus, the implementation of the C program for SCAN disc scheduling has been successfully executed.
## DISK SCHEDULING C-SCAN
## AIM:
To write a program for the c-scan method of disc scheduling.
## ALGORITHM:
1. Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
2. Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
3. Sort the request array in ascending order to facilitate the SCAN algorithm.
4. Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
5. Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the SCAN disk scheduling algorithm.
## PROGRAM:
```C
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
    printf("Enter the number of Requests\n");
    scanf("%d",&n);
    printf("Enter the Requests sequence\n");
    for(i=0;i<n;i++)
     scanf("%d",&RQ[i]);
    printf("Enter initial head position\n");
    scanf("%d",&initial);
    printf("Enter total disk size\n");
    scanf("%d",&size);
    printf("Enter the head movement direction for high 1 and for low 0\n");
    scanf("%d",&move); 
    // logic for C-Scan disk scheduling 
        /*logic for sort the request array */
    for(i=0;i<n;i++)
    {
        for( j=0;j<n-i-1;j++)
        {
            if(RQ[j]>RQ[j+1])
            {
                int temp;
                temp=RQ[j];
                RQ[j]=RQ[j+1];
                RQ[j+1]=temp;
            }
        }
    }
    int index;
    for(i=0;i<n;i++)
    {
        if(initial<RQ[i])
        {
            index=i;
            break;
        }
    } 
    // if movement is towards high value
    if(move==1)
    {
        for(i=index;i<n;i++)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        }
        //  last movement for max size 
        TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
        /*movement max to min disk */
        TotalHeadMoment=TotalHeadMoment+abs(size-1-0);
        initial=0;
        for( i=0;i<index;i++)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    // if movement is towards low value
    else
    {
        for(i=index-1;i>=0;i--)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        }
        //  last movement for min size 
        TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);
        /*movement min to max disk */
        TotalHeadMoment=TotalHeadMoment+abs(size-1-0);
        initial =size-1;
        for(i=n-1;i>=index;i--)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    printf("Total head movement is %d",TotalHeadMoment);
    return 0;
}
```
## OUTPUT:
![output4](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/acb8e952-c04e-49f7-a5fe-314c6f5b8a2b)
## RESULT:
Thus, the implementation of C-SCAN Disk scheduling algorithm in C programming is done successfully.
## DISK SCHEDULING LOOK
## AIM:
To write a program for the look method of disc scheduling.
## ALGORITHM:
1. Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
2. Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
3. Sort the request array in ascending order to facilitate the LOOK algorithm.
4. Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
5. Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the LOOK disk scheduling algorithm.
## PROGRAM:
```C
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
## OUTPUT:
![output5](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/c8511dad-619c-4d84-bb42-228506cd8a3b)
## RESULT:
Thus, the implementation of the C program for LOOK disc scheduling has been successfully executed.
## DISK SCHEDULING C-LOOK
## AIM:
To write a program for the c-look method of disc scheduling.
## ALGORITHM:
1. Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
2. Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
3. Sort the request array in ascending order to facilitate the LOOK algorithm.
4. Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
5. Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the LOOK disk scheduling algorithm.
## PROGRAM:
```C
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
    printf("Enter the number of Requests\n");
    scanf("%d",&n);
    printf("Enter the Requests sequence\n");
    for(i=0;i<n;i++)
     scanf("%d",&RQ[i]);
    printf("Enter initial head position\n");
    scanf("%d",&initial);
    printf("Enter total disk size\n");
    scanf("%d",&size);
    printf("Enter the head movement direction for high 1 and for low 0\n");
    scanf("%d",&move); 
    // logic for C-look disk scheduling 
        /*logic for sort the request array */
    for(i=0;i<n;i++)
    {
        for( j=0;j<n-i-1;j++)
        {
            if(RQ[j]>RQ[j+1])
            {
                int temp;
                temp=RQ[j];
                RQ[j]=RQ[j+1];
                RQ[j+1]=temp;
            }
        }
    }
    int index;
    for(i=0;i<n;i++)
    {
        if(initial<RQ[i])
        {
            index=i;
            break;
        }
    } 
    // if movement is towards high value
    if(move==1)
    {
        for(i=index;i<n;i++)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        } 
        for( i=0;i<index;i++)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    // if movement is towards low value
    else
    {
        for(i=index-1;i>=0;i--)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        } 
        for(i=n-1;i>=index;i--)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    printf("Total head movement is %d",TotalHeadMoment);
    return 0;
}
```
## OUTPUT:
![output6](https://github.com/Shrruthilaya-Gangadaran/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/93427705/e9ee60f6-9dcc-42d8-8d8d-9e3cbaafa0a8)
## RESULT:
Thus, the implementation of C-look Disk scheduling algorithm in C programming is done successfully.
