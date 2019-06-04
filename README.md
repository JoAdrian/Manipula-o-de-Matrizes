# Manipula-o-de-Matrizes


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct matriz{
    int linhas;
    int colunas;
    float x[10][10];
};
struct matriz A, B, C;
int a = 0, b = 0, c = 0, prcA = 0, prcB = 0;

void tamanhoMatrizA(){
    int i, j;
    printf("Digite o numero de linhas da matriz A (limite de 10 linhas!):\n");
    scanf("%d", &A.linhas);
    if(A.linhas < 1 || A.linhas > 10){
        printf("Numero de linhas invalido!\n");
    } else {
        printf("Digite o numero de colunas da matriz A (limite de 10 colunas!):\n");
        scanf("%d", &A.colunas);
        if(A.colunas < 1 || A.colunas > 10){
            printf("Numero de colunas invalido!\n");
        } else {
            printf("Sua matriz A tem %d linhas e %d colunas.\n", A.linhas, A.colunas);
            a = 1;
        }
    }
}

void tamanhoMatrizB(){
    printf("Digite o numero de linhas da matriz B (limite de 10 linhas!):\n");
    scanf("%d", &B.linhas);
    if(B.linhas < 1 || B.linhas > 10){
        printf("Numero de linhas invalido!\n");
    } else {
        printf("Digite o numero de colunas da matriz B (limite de 10 colunas!):\n");
        scanf("%d", &B.colunas);
        if(B.colunas < 1 || B.colunas > 10){
            printf("ERRO! Numero de colunas invalido!\n");
        } else {
            printf("Sua matriz B tem %d linhas e %d colunas.\n", B.linhas, B.colunas);
            b = 1;
        }
    }
}

void preenchimentoAleatorioMatrizA(){
    int i, j;
    if(a == 0){
        printf("ERRO! Defina primeiro as dimesoes da matriz A!\n");
    } else {
        for(i = 0; i < A.linhas; i++){
            for(j = 0; j < A.colunas; j++){
                A.x[i][j] = rand() % 90;
            }
        }
        printf("Preenchimento da matriz A realizado com sucesso!\n");
        prcA = 1;
    }
}

void preenchimentoAleatorioMatrizB(){
    int i, j;
    if(b == 0){
        printf("ERRO! Defina primeiro as dimensoes da matriz B!\n");
    } else {
        for(i = 0; i < B.linhas; i++){
            for(j = 0; j < B.colunas; j++){
                B.x[i][j] = rand() % 90;
            }
        }
        printf("Preenchimento da matriz B realizado com sucesso!\n");
        prcB = 1;
    }
}

void preenchimentoManualMatrizA(){
    int i, j;
    if(a == 0){
        printf("ERRO! Defina primeiro as dimesoes da matriz!\n");
    } else {
        for(i = 0; i < A.linhas; i++){
            for(j = 0; j < A.colunas; j++){
                printf("Digite um valor para a posicao %d-%d da matriz A:\n", i, j);
                scanf("%f", &A.x[i][j]);
            }
        }
        printf("Operacao realizada com sucesso!\n");
        prcA = 1;
    }
}

void preenchimentoManualMatrizB(){
    int i, j;
    if(b == 0){
        printf("ERRO! Defina primeiro as dimensoes da matriz B!\n");
    } else {
        for(i = 0; i < B.linhas; i++){
            for(j = 0; j < B.colunas; j++){
                printf("Digite um valor para a posicao %d-%d da matriz B:\n", i, j);
                scanf("%f", &B.x[i][j]);
            }
        }
        printf("Operacao realizada com sucesso!\n");
        prcB = 1;
    }
}

void soma(){
    int i, j;
    if((prcA == 0 && prcB == 1) || (prcA == 1 && prcB == 0) || (prcA == 0 && prcB == 0)){
        printf("ERRO! Falta preencher pelo menos uma das matrizes!\n");
    } else {
        if(A.linhas == B.linhas && A.colunas == B.colunas){
            for(i = 0; i < A.linhas; i++){
                for(j = 0; j < A.colunas; j++){
                    C.x[i][j] = A.x[i][j] + B.x[i][j];
                }
            }
            printf("Operação realizada com sucesso!\n");
            c = 1;
        } else {
            printf("ERRO! Dimensoes diferentes.");
        }
    }
}

void diferenca(){
    int i, j;
    if((prcA == 0 && prcB == 1) || (prcA == 1 && prcB == 0) || (prcA == 0 && prcB == 0)){
        printf("ERRO! Falta preencher pelo menos uma das matrizes!\n");
    } else {
        if(A.linhas == B.linhas && A.colunas == B.colunas){
            for(i = 0; i < A.linhas; i++){
                for(j = 0; j < A.colunas; j++){
                    C.x[i][j] = A.x[i][j] - B.x[i][j];
                }
            }
            printf("Operação realizada com sucesso!\n");
            c = 1;
        } else {
            printf("ERRO! Dimensoes diferentes.");
        }
    }
}

void produto(){
    int i, j, k;
    if((prcA == 0 && prcB == 1) || (prcA == 1 && prcB == 0) || (prcA == 0 && prcB == 0)){
        printf("ERRO! Falta preencher pelo menos uma das matrizes!\n");
    } else {
        if(A.colunas == B.linhas){
            for(i = 0; i < A.linhas; i++){
                for(j = 0; j < B.colunas; j++){
                    C.x[i][j] = 0;
                    for(k = 0; k < A.linhas; k++){
                        C.x[i][j] = C.x[i][j] + A.x[i][k]*B.x[k][j];
                    }
                }          
            }
            printf("Operacao realizada com sucesso!\n");
            c = 1;
        } else {
            printf("ERRO! Numero de colunas de A firefente do numero de linhas de B.");
        }
    }
}

void imprimirMatrizA(){
    int i,j;
    if(prcA == 0){
        printf("ERRO! Primeiro preencha a matriz A!\n");
    } else {
        for(i=0; i<A.linhas; i++){
            for(j=0; j<A.colunas; j++){
                printf("%6.2f ", A.x[i][j]);
            }
            printf("\n");
        }
    }
}
void imprimirMatrizB(){
    int i,j;
    if(prcB == 0){
        printf("ERRO! Primeiro preencha a matriz B!\n");
    } else {
        for(i=0; i<B.linhas; i++){
            for(j=0; j<B.colunas; j++){
                printf("%6.2f ", B.x[i][j]);

            }
            printf("\n");
        }
    }
}

void imprimirMatrizC(){
    int i, j;
    if(c == 0){
        printf("ERRO! Nenhuma operacao com as duas matrizes foi realizada! \n");
    } else {
        for(i = 0; i < A.linhas; i++){
            for(j = 0; j < B.colunas; j++){
                printf("%6.2f ", C.x[i][j]);
            }
            printf("\n");
        }
    }
}
int main() {  
    //Declaracao de uma variável utilizada como booleana chamada 'bo'.
    int bo;
    bo = 0;
    do{
        //Declaracao de variavel 'ope' para armazenar o numero da operacao escolhido pelo usuario. Logo após, a lista.
        int ope;
        printf("PROGRAMA DE MANIPULACAO DE MATRIZES\n"
                "(1) Definir o tamanho da matriz A\n"
                "(2) Definir o tamanho da matriz B\n"
                "(3) Preencher a matriz A com valores aleatórios\n"
                "(4) Preencher a matriz B com valores aleatórios\n"
                "(5) Atribuir valores manualmente para os elementos da matriz A\n"
                "(6) Atribuir valores manualmente para os elementos da matriz B\n"
                "(7) Calcular A+B\n"
                "(8) Calcular A-B\n"
                "(9) Calcular A*B\n"
                "(10) Imprimir matriz A\n"
                "(11) Imprimir matriz B\n"
                "(12) Imprimir matriz C\n"
                "(13) Ler a matriz A de um arquivo\n"
                "(14) Ler a matriz B de um arquivo\n"
                "(15) Escrever a matriz C em um arquivo\n"
                "(16) Sair\n"
                "digite sua operacao:");
        scanf("%d", &ope);
        switch(ope){
            case 1:
                tamanhoMatrizA();
                break;
            case 2:
                tamanhoMatrizB();
                break;
            case 3:
                preenchimentoAleatorioMatrizA();
                break;
            case 4:
                preenchimentoAleatorioMatrizB();
                break;
            case 5:
                preenchimentoManualMatrizA();
                break; 
            case 6:
                preenchimentoManualMatrizB();
                break;
            case 7:
                soma();
                break;
            case 8:
                diferenca();
                break;  
            case 9:
                produto();
                break;
            case 10:
                imprimirMatrizA();
                break;
            case 11:
                imprimirMatrizB();
                break;
            case 12:
                imprimirMatrizC();
                break;    
            case 16:
                printf("A operacao foi finalizada!\n");
                bo = 1;
                break;    
            default:
                printf("Operacao INVALIDA!\n");
                break;
        }
    }while(bo == 0);
    return 0;
}

