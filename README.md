#include <stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node *link;
}*head,*head2;
void createlinklist(int n){
    struct node *newnode,*temp;
    int data,i;
    head=(struct node *)malloc(sizeof(struct node));
    if(head==NULL){
        printf("Failure in node creation");
    }else{
        printf("Enter the data 1 : ");
        scanf("%d",&data);
        head->data=data;
        head->link=NULL;
        temp=head;
        for(i=1;i<n;i++){
            newnode=(struct node *)malloc(sizeof(struct node));
            printf("Enter the data %d : ",i+1);
            scanf("%d",&data);
            newnode->data=data;
            newnode->link=NULL;
            temp->link=newnode;
            temp=temp->link;
        }
    }
}void insertatbeginning(){
    int data;
    printf("\nEnter the data which want you to insert : ");
    scanf("%d",&data);
    struct node *a;
    a=(struct node *)malloc(sizeof(struct node));
    if(a==NULL){
        printf("Failure in node creation");
    }else{
        a->data=data;
        a->link=head;
        head=a;
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\nAFTER INSERTION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void insertatend(){
    int data;
    printf("\nEnter the data which want you to insert : ");
    scanf("%d",&data);
    struct node *a,*b;
    a=(struct node *)malloc(sizeof(struct node));
    if(a==NULL){
        printf("Failure in node creation");
    }else{
        b=head;
        while(b->link!=NULL){
            b=b->link;
        }b->link=a;
        a->data=data;
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\nAFTER INSERTION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void insertatanyposition(int n){
    int data,pos;
    printf("\nEnter the data which want you to insert : ");
    scanf("%d",&data);
    printf("\nEnter the position to insert the data : ");
    scanf("%d",&pos);
    int c=1;
    struct node *a,*b;
    a=(struct node *)malloc(sizeof(struct node));
    if(a==NULL){
        printf("Failure in node creation");
    }else{
        b=head;
        if(pos<=0 || pos>=n+1){
            printf("\nThere is no position to insert your data.");
        }else{
            while(c!=pos-1){
                b=b->link;
                c++;
            }a->link=b->link;
            b->link=a;
            a->data=data;
        }
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER INSERTION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void deleteatfront(){
    struct node *ptr;
    ptr=head;
    head=head->link;
    if(ptr==NULL){
        printf("\nList is empty");
    }else{
        free(ptr);
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER DELETION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void deleteatend(){
    struct node *ptr,*ptr1;
    ptr=head;
    if(ptr==NULL){
        printf("\nList is empty");
    }else{
        while(ptr->link!=NULL){
            ptr1=ptr;
            ptr=ptr->link;
        }ptr1->link=NULL;
        free(ptr);
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER DELETION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void deletebykey(){
    int key;
    printf("Enter the value which want you delete : ");
    scanf("%d",&key);
    struct node *ptr,*ptr1;
    ptr=head->link;
    if(ptr==NULL){
        printf("List is empty");
    }else{
        while(ptr->data!=key && ptr->link!=NULL){
            ptr1=ptr;
            ptr=ptr->link;
        }if(ptr1->link==NULL){
            printf("\nKey element is not found");
        }else{
            ptr1->link=ptr->link;
            free(ptr);
        }
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER DELETION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}void deletebyposition(int n){
    int pos,i;
    printf("\nEnter the position : ");
    scanf("%d",&pos);
    struct node *ptr,*ptr1;
    if(head==NULL){
        printf("\nList is empty");
    }else{
        ptr=head;
        ptr1=head;
        for(i=2;i<=pos;i++){
            ptr1=ptr;
            ptr=ptr->link;
            if(ptr==NULL){
                break;
            }
        }if(ptr!=NULL){
            ptr1->link=ptr->link;
            free(ptr);
        }else{
            printf("\nInvalid position");
        }
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER DELETION YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}
void search(){
    int key;
    printf("\nEnter the key element which want you search : ");
    scanf("%d",&key);
    struct node *ptr;
    ptr=head->link;
    if(ptr==NULL){
        printf("List is empty");
    }else{
        while(ptr->data!=key && ptr->link!=NULL){
            ptr=ptr->link;
        }
    }if(ptr->data==key){
        printf("\nKey element is found");
    }else{
        printf("\nKey element is not found");
    }
}void merge(){
    int a;
    printf("\nEnter the total number of nodes which want you to merge with first linked list : ");
    scanf("%d",&a);
    struct node *newnode2,*temp2;
    int data,i;
    head2=(struct node *)malloc(sizeof(struct node));
    if(head2==NULL){
        printf("\nFailure in node creation");
    }else{
        printf("\nEnter the data 1 of 2nd linked list : ");
        scanf("%d",&data);
        head2->data=data;
        head2->link=NULL;
        temp2=head2;
        for(i=1;i<a;i++){
            newnode2=(struct node *)malloc(sizeof(struct node));
            printf("Enter the data %d of 2nd linked list : ",i+1);
            scanf("%d",&data);
            newnode2->data=data;
            newnode2->link=NULL;
            temp2->link=newnode2;
            temp2=temp2->link;
        }
    }struct node *ptr;
    ptr=head;
    if(ptr==NULL){
        printf("List is empty");
    }else{
        while(ptr->link!=NULL){
            ptr=ptr->link;
        }ptr->link=head2;
    }struct node *t;
    if(head==NULL){
        printf("List is empty");
    }else{
        t=head;
        printf("\n\nAFTER MERGING YOUR LINK LIST BECOMES : ");
        while(t!=NULL){
            printf("%d ",t->data);
            t=t->link;
        }
    }
}
int next(){
    char a;
    printf("\n\n\nDo you want to perform another operation(y/n): ");
    scanf("\n%c",&a);
    if(a=='n' || a=='N'){
        return 0;
    }else if(a=='y' || a=='Y'){
        return 1;
    }
}
int main(){
    int n,choice;
    printf("Enter the number of nodes : ");
    scanf("%d",&n);
    createlinklist(n);
    do{
        printf("\nOperations of link list:\n\n1.Insert at beginning\n2.Insert at end\n3.Insert at any position");
        printf("\n4.Delete at front\n5.Delete at end\n6.Delte by value\n7.Delete by position\n8.Searching");
        printf("\n9.Merging\n\nEnter which operation do you perform : ");
        scanf("%d",&choice);
        switch(choice){
            case 1:
                insertatbeginning();
                break;
            case 2:
                insertatend();
                break;
            case 3:
                insertatanyposition(n);
                break;
            case 4:
                deleteatfront();
                break;
            case 5:
                deleteatend();
                break;
            case 6:
                deletebykey();
                break;
            case 7:
                deletebyposition(n);
                break;
            case 8:
                search();
                break;
            case 9:
                merge();
                break;
            default:
                printf("NO");
                break;
        }
    }while(next());
    printf("\nThank you performing operations on link list:)\n\n");
    return 0;
}

