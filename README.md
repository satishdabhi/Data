# Data
#include<stdio.h>
#include<stdlib.h>
void Append(void);
int Length(void);
void Dispaly(void);
int len;
struct node
{
  int data;
  struct node* link;
};
struct node* root=NULL;

void main()
{
  int ch;
  while(1)
  {
      printf("Single Linked List operations:\n");
      printf("1.Append\n");
      printf("2.insert before node value\n");
      printf("3.Length\n");
      printf("4.Display\n");

  printf("Enter a Number:\n");
  scanf("%d",&ch);
  switch(ch)
  {
      case 1: Append();
              break;
      case 2:insertbeforenodevalue();
             break;
      case 3: len=Length();
              printf("Length=%d\n\n",len);
              break;
      case 4: Display();
              break;
      default :exit(1);
  }
  }

}

void Append()
{
  struct node*temp;
  temp=(struct node*)malloc(sizeof(struct node));
  printf("Enter a node data:");
  scanf("%d",&temp->data);
  temp->link=NULL;
  if(root==NULL)
  {
      root=temp;
  }
  else
  {
      struct node* p;
      p=root;
      while(p->link!=NULL)
      {
       p=p->link;
      }
      p->link=temp;
  }
}
void insertbeforenodevalue()
{
 struct node* temp;
 int loc;
 printf("Enter a Add location:");
 scanf("%d",&loc);
 temp=(struct node*)malloc(sizeof(struct node));
 printf("Enter a node data");
 scanf("%d",&temp->data);
 if(loc>Length())
 {
     printf("Invalid Input");
 }
 else
{
  struct node*p;
  p=root;
  int i=1;
  while(i<loc)
  {
      p=p->link;
      i++;
  }
  temp->link=p->link;
  p->link=temp;
}

}
int Length()
{   int count=0;
    struct node*temp;
    temp=root;
    while(temp!=NULL)
    {
     count++;
     temp=temp->link;
    }
  return(count);
}
void Display()
{
    struct node*temp;
    temp=root;
    if(temp==NULL)
    {
        printf("List is empty\n\n");
    }
    else
    {
        while(temp!=NULL)
        {
          printf("%d-->",temp->data);
          temp=temp->link;
        }
        printf("\n\n");
    }
}
