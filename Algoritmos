#include<stdio.h>
#include<stdlib.h>
#include<time.h>

//limita o tamanho do maior inteiro gerado
#define lim 1000000000
//N tamanho do vetor
#define N 1000


void merge(int inicio, int meio, int fim, int* V) 
{
   int *W;                                
   W = malloc ((fim-inicio) * sizeof (int));      
   int i = inicio, j = meio;                    
   int k = 0;                              

   while (i < meio && j < fim) {                
      if (V[i] <= V[j])  W[k++] = V[i++];  
      else  W[k++] = V[j++];               
   }                                       
   while (i < meio)  W[k++] = V[i++];         
   while (j < fim)  W[k++] = V[j++];         
   for (i = inicio; i < fim; ++i)  V[i] = W[i-inicio]; 
   free (W);                               
}

void mergesort(int* V, int inicio, int fim){
    int meio;
    if(inicio < fim - 1){ //quando se tratar do vetor unitário
        meio = (inicio+fim)/2;
        mergesort(V, inicio, meio);
        mergesort(V, meio, fim);
        merge(inicio, meio, fim, V);
    }
}

int Particao(int A[], int p, int r) // r = tamanho do vetor e final, p = inicio do vetor
{
    int x,j,i, aux; // j é a variavel que percorre o vetor
    x = A[r];
    i = p-1; //?
    
    for(j=p; j<=r-1; j++){ 
        if (A[j]<=x){        
            i++;
            aux = A[i];       //Sempre é preciso fazer as trocas.
            A[i] = A[j];
            A[j] = aux;
        }
    }
    aux = A[i+1];
    A[i+1] = A[r];
    A[r] = aux;
    return i+1;
}

void quicksort(int A[], int p, int r)
{ int q; //q funciona como um vetor auxiliar que guarda a posição do vetor
    if(p<r){
        q = Particao(A,p,r);
        quicksort(A,p,q-1); // momento em que ordena a esquerda do vetor até a posição -1
        quicksort(A,q+1,r); // ordena a posição +1 do vetor até a direita 
    }
    return; 
}

void insertionsort_recursivo(int *V, int n){
    int ultimo, j;

    if(n <=1)
        return;
    
    insertionsort_recursivo(V, n-1);

    ultimo = V[n-1];
    j = n-2;

    while (j >= 0 && V[j] > ultimo){
        V[j+1] = V[j];
        j--;
    }
    V[j+1]=ultimo;
}

void insertionsort_iterativo(int* V, int n){
    int i=0;
    int j=1;
    int aux =0;

    while(j<n){
        aux = V[j];
        i = j-1;
        while((i>=0) && (V[i]>aux)){
            V[i+1] = V[i];
            i = i-1;            
        }
        V[i+1]=aux;
        j=j+1;
    }
}

int main(){
    int i=0,tam=N;
    int V[N];
    float tempof;
    clock_t tempo1, tempo2;

    tempo1 = clock();

    srand(time(NULL));
    for(i=0;i<tam;i++){
       V[i]=rand()%lim;
    }

/*
        printf("\nV:");
    for(int i=0; i<N; i++){
        printf("%d, ", V[i]);

    }*/
   
    quicksort(&V, 0, N);

     /*   printf("\nV:");
    for(int i=0; i<N; i++){
        printf("%d ", V[i]);

    }*/
    tempo2=clock();
    tempof = tempo2 - tempo1;

    printf("\nTempo:%.1000f", tempof / CLOCKS_PER_SEC); // TEMPO MEDIDO EM SEGUNDOS!!!!!!

    return 0;    
  
}