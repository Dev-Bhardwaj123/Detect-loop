# Detect-loop
Given a linked list detect whether there is a loop in the linked list or not
//Detect loop in a linked list
#include<iostream>
using namespace std;

struct Node{
	int data;
	Node* next;
	Node(int d){
		data=d;
		next=NULL;
	}	
};

bool detectLoop(Node* head){
	Node* slow=head,*fast=head;
	while(fast!=NULL || fast->next!=NULL){
		slow=slow->next;
		fast=fast->next->next;
		if(slow==fast){
			return true;
		}
	}
	return false;
}

void printList(Node* head)
{
	if(head==NULL){
		return;
	}
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data<<" ";
		curr=curr->next;
	}	
}

int main(){
	Node* head=new Node(15);
	head->next=new Node(10);
	head->next->next=new Node(12);
	head->next->next->next=new Node(20);
	head->next->next->next->next=head->next;
	cout<<"Loop there: "<<detectLoop(head);
	return 0;
}
