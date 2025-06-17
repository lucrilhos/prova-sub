#include <stdio.h>

float calcularMedia(float notas[], int quantidade) {
    float soma = 0;
    for (int i = 0; i < quantidade; i++) {
        soma += notas[i];
    }

    if (quantidade > 0) {
        return soma / quantidade;
    } else {
        return 0;
    }
}

float encontrarMaior(float notas[], int quantidade) {
    float maior = notas[0];
    for (int i = 1; i < quantidade; i++) {
        if (notas[i] > maior) {
            maior = notas[i];
        }
    }
    return maior;
}
// antes do main foram declaradas as funções para encontrar a maior nota e a média entre as notas
int main() {
    float notas[10];
    int quantidade = 0;
    char continuar;

    printf("Bem vindo ao sistema de gerenciamento de notas.\n");
    printf("Insira até 10 notas\n");

    do {
        if (quantidade >= 10) {
            printf("Limite de notas.\n");
            break; // se passar de 10 iterações, o loop sofre um break
        }

        printf("Insira a nota %d: ", quantidade + 1);
        scanf("%f", &notas[quantidade]);
        quantidade++; // cada nota acrescenta na "lista" chamada de quantidade

        if (quantidade < 10) {
            printf("Deseja inserir outra nota? (s/n): ");
            scanf(" %c", &continuar);
        } else {
            continuar = 'n';
        }

    } while (continuar == 's' || continuar == 'S'); // mais fácil fazer o loop com s/n do que "Sim" ou "Não"

    if (quantidade > 0) {
        float media = calcularMedia(notas, quantidade);
        float maior = encontrarMaior(notas, quantidade);
        // atribuição dos valores nas variáveis

        printf("\nTotal de notas inseridas: %d\n", quantidade);
        printf("Media: %.2f\n", media);
        printf("Maior nota: %.2f\n", maior);
    } else {
        printf("Nenhuma nota foi inserida.\n");
    }

    return 0;
}
