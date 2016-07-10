linear-linked-list
#include<stdio.h>
#include<stdlib.h>
struct node
{ int data;
  struct node *next;
}*start;
struct node *getnode()
     {  struct node *x=(struct node*)malloc(sizeof(struct node));
	return x;
     }
void insert_after(struct node*p,int num)
{  struct node *q;
   if(p==NULL)
	{  printf("the previous node cant be null");
	   return;
	}
   q=getnode();
   q->data=num;
   q->next=p->next;
   p->next=q;
}
void display()
{  struct node *st;
   st=start;
   while(st!=NULL)
     {  printf("\n%d",st->data);
	st=st->next;
      }
}
void insert_beg(int num)
{ struct node*t;
  t=getnode();
  t->data=num;
  t->next=start;
  start=t;
}
void delete_after(struct node*p)
{ struct node *t;
  if (p->next==NULL)
     { printf("not possible");
     }
  else
     {  t=p->next;
	p->next=t->next;
	free(t);
	return;
     }
}
void insert_at_specific_position(int c,int num)
{ struct node *st,*t;int i;
  for(i=0,st=start;i<c;i++)
    {  st=st->next;
       if(st==NULL)
	  { printf("there are less than%d elements",c);
	    return;
	  }
    }
 t=getnode();
 t->data=num;
 t->next=st->next;
 st->next=t;
}
int count()
{ struct node *st;
  int cnt=0;
  st=start;
  while(st!=NULL)
    { cnt++;
      st=st->next;
    }
  return(cnt);
}
void main()
{ int ch;
char ch1;
clrscr();
do
{
    printf("1.insert_beg");
    printf("\n");
    printf("2.insert_after");
    printf("\n");
    printf("3.display");
    printf("\n");
    printf("4.insert_at_specific_position");
    printf("\n");
    printf("5.delete_after");
    printf("\n");
    printf("6.count");
    printf("\n");
    printf("7.exit");
    printf("\n");
    printf("enter your choice");
    printf("\n");
    scanf("%d",&ch);
 switch(ch)
  {

   case 1:insert_beg(10);
	  printf("\n");
	  break;
   case 2:insert_after(start,5);
	  break;
   case 3:display();
	  break;
   case 4:insert_at_specific_position(3,100);
	  break;
   case 5:delete_after(start->next);
	   break;
   case 6:count();
	    break;
   case 7: exit(0);
  }
  printf("\ndo u want to continue");
  scanf("%s",&ch1);
  }while(ch1!='N'||ch1!='n');

}
