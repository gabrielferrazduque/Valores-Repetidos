# Valores-Repetidos
Valores Repetidos 
#include <stdio.h>

#define LINHAS 5
#define COLUNAS 5

// Função para contar números repetidos em uma linha ou coluna
int contarRepetidos(int vetor[], int tamanho) {
    int repetidos = 0;
    for (int i = 0; i < tamanho; i++) {
        for (int j = i + 1; j < tamanho; j++) {
            if (vetor[i] == vetor[j]) {
                repetidos++;
                break; // Para não contar o mesmo número mais de uma vez
            }
        }
    }
    return repetidos;
}

// Função para encontrar a linha ou coluna com mais repetidos
void encontrarMaiorRepeticao(int matriz[LINHAS][COLUNAS]) {
    int maxRepetidos = -1;
    int indiceMaiorRepetidos = -1;
    char tipoMaiorRepetidos = 'L'; // 'L' para linha, 'C' para coluna

    // Verificar as linhas
    for (int i = 0; i < LINHAS; i++) {
        int repetidos = contarRepetidos(matriz[i], COLUNAS);
        if (repetidos > maxRepetidos) {
            maxRepetidos = repetidos;
            indiceMaiorRepetidos = i;
            tipoMaiorRepetidos = 'L';
        }
    }

    // Verificar as colunas
    for (int j = 0; j < COLUNAS; j++) {
        int coluna[LINHAS];
        for (int i = 0; i < LINHAS; i++) {
            coluna[i] = matriz[i][j];
        }
        int repetidos = contarRepetidos(coluna, LINHAS);
        if (repetidos > maxRepetidos) {
            maxRepetidos = repetidos;
            indiceMaiorRepetidos = j;
            tipoMaiorRepetidos = 'C';
        }
    }

    // Exibir o resultado
    if (tipoMaiorRepetidos == 'L') {
        printf("A linha %d tem mais números repetidos (%d).\n", indiceMaiorRepetidos, maxRepetidos);
    } else {
        printf("A coluna %d tem mais números repetidos (%d).\n", indiceMaiorRepetidos, maxRepetidos);
    }
}

int main() {
    // Exemplo de matriz para teste
    int matriz[LINHAS][COLUNAS] = {
        {4, 17, 23, 48, 36},
        {17, 52, 67, 89, 48},
        {29, 14, 75, 83, 38},
        {56, 17, 91, 64, 71},
        {4, 17, 23, 48, 36}
    };

    encontrarMaiorRepeticao(matriz);

    return 0;
}

