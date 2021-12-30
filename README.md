# operations-on-single-linked-list
#include<stdio.h>
#include<malloc.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node *next;
};
typedef struct node node;
node *concat(node *l1,node *l2)
{
    node *temp;
    if(l1==NULL)
    {
        return l2;
    }
    else if(l2==NULL)
    {
        return l1;
    }
    else
    {
        temp=l1;
        while(temp->next!=NULL)
        {
            temp=temp->next;
        }
        temp->next=l2;
       
    }
    return l1;
   
   
}
node *addnode(node *l1,node *l2)
{  
    node *temp;
    if(l1==NULL)
    {
        l1=l2;
       
    }
    else
    {
        temp=l1;
        while(temp->next!=NULL)
        {
            temp=temp->next;
        }
        temp->next=l2;
    }
    return l1;
}
node *Union(node *l1,node *l2)
{
    node *new,*l3=NULL;
    while(l1!=NULL && l2!=NULL)
 {   if(l1->data>l2->data)
    {
      new=(node *)(malloc(sizeof(node)));
      new->data=l2->data;
      new->next=NULL;
      l3=addnode(l3,new);
      l2=l2->next;
    }
    else if(l1->data<l2->data)
    {
        new=(node*)(malloc(sizeof(node)));
        new->data=l1->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l1=l1->next;
    }
    else
    {
       new=(node*)(malloc(sizeof(node)));
       new->data=l2->data;
       new->next=NULL;
       l3=addnode(l3,new);
       l1=l1->next;
       l2=l2->next;
    }
   
}
if(l1==NULL)
{  
    while(l2!=NULL)
   {    new=(node *)(malloc(sizeof(node)));
        new->data=l2->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l2=l2->next;
   }
}
if(l2==NULL)
{
    while(l1!=NULL)
   {    new=(node *)(malloc(sizeof(node)));
        new->data=l1->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l1=l1->next;
   }
}
return l3;
}

node *create(node *first)
{
    node *new,*prev;
    int c;
    printf("enter data press -1 to stop");
    scanf("%d",&c);
    while(c!=-1)
    {
        new=(node*)(malloc(sizeof(node)));
        new->data=c;
        new->next=NULL;
        if(first==NULL)
        {
            first=new;
            prev=new;
        }
        else
        {
            prev->next=new;
            prev=new;
        }
        printf("enter data press -1 to stop");
        scanf("%d",&c);
    }
    return first;
   
}
void display(node *first)
{
    node *temp=first;
    if(first==NULL)
    {
        printf("No node to display");
       
    }
    else
    {
        while(temp!=NULL)
        {
            printf("|%d|->",temp->data);
            temp=temp->next;
        }
    }
}
node *intersection(node *l1,node *l2)
{
    node *new,*l3=NULL,*temp1=l1,*temp2=l2;
    while(l1!=NULL)
    {
        while(l2!=NULL)
    {    if(l1->data==l2->data)
        {
            new=(node*)(malloc(sizeof(node)));
            new->data=l1->data;
            new->next=NULL;
            l3=addnode(l3,new);
            l2=l2->next;
             
        }
        else
        {
            l2=l2->next;
        }
    }
        l1=l1->next;
        l2=temp2;
    }
   
    return l3;
}
node *merging(node *l1,node *l2)
{
    node *new,*l3=NULL;
    while(l1!=NULL && l2!=NULL)
 {   if(l1->data>l2->data)
    {
      new=(node *)(malloc(sizeof(node)));
      new->data=l2->data;
      new->next=NULL;
      l3=addnode(l3,new);
      l2=l2->next;
    }
    else if(l1->data<l2->data)
    {
        new=(node*)(malloc(sizeof(node)));
        new->data=l1->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l1=l1->next;
    }
    else
    {
       new=(node*)(malloc(sizeof(node)));
       new->data=l2->data;
       new->next=NULL;
       l3=addnode(l3,new);
       l1=l1->next;
       l2=l2->next;
    }
   
}
if(l1==NULL)
{  
    while(l2!=NULL)
   {    new=(node *)(malloc(sizeof(node)));
        new->data=l2->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l3=addnode(l3,new);
        l2=l2->next;
   }
}
if(l2==NULL)
{
    while(l1!=NULL)
   {    new=(node *)(malloc(sizeof(node)));
        new->data=l1->data;
        new->next=NULL;
        l3=addnode(l3,new);
        l1=l1->next;
   }
}
return l3;
}
node *sort(node *first)
{
    node *temp1,*temp2;
    int t;
    for(temp1=first;temp1!=NULL;temp1=temp1->next)
    {
         for(temp2=temp1->next;temp2!=NULL;temp2=temp2->next)
         {
             if(temp1->data>temp2->data)
             {
             t=temp1->data;
             temp1->data=temp2->data;
             temp2->data=t;
             }
         }
    }
    return first;
}
void main()
{
    int ch;
    node *l1=NULL,*l2=NULL,*l,*l3;
    l1=create(l1);
    l2=create(l2);
    while(1)
{    printf("enter choice");
    printf("\n1.concat\n2.Display\n3.exit");
    scanf("%d",&ch);
    switch(ch)
    {
        case 1:
               l3=concat(l1,l2);
               break;
        case 2:
              display(l3);
              break;
        case 3:
              l3=Union(l1,l2);
              //l3=sort(l);
              break;
        case 4:
             l3=intersection(l1,l2);
             break;
        case 5:
              l=merging(l1,l2);
              l3=sort(l);
              break;
        case 6:
              exit(0);
        default:printf("enter correct number");
 
 
 }  
 }
}
