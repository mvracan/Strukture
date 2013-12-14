Strukture
=========
#include<iostream>
using namespace std;

struct pacijent{
       char ime[50],prezime[50],datum[15],spol;
       int ai,bi,ci,di,ei;
       };
       
struct r{
       pacijent p;
       r *next;
       };
       
struct red{
       r *front,*rear;
       };

red *InitQ(red *q){
     q = new red;
     r *glava = new r;
     q->front = glava;
     q->rear = glava;
     return q;
     }

bool IsEmptyQ(red *q){
     return q->front==q->rear;
     }
     
pacijent FrontQ(red *q){
        return q->front->next->p;
        }
        
void EnQueueQ(pacijent x,red *q){
     r *novi = new r;
     novi->next = NULL;
     novi->p = x;
     q->rear->next = novi;
     q->rear = novi;
     }

void DeQueueQ(red *q){
     r *erase = q->front;
     q->front = q->front->next;
     delete erase;
     }
