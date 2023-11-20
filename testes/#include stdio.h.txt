#include <stdio.h>

int main() {
    // Definir os endereços dos strings SFILE e SLOOK
    char *SFILE = (char *)0xE0;
    char *SLOOK = (char *)0xE1;

    // Inicializar o endereço do resultado em 0xE2 com 0x00
    char *SRES = (char *)0xE2;
    *SRES = 0x00;

    // Iniciar a busca do string SLOOK dentro do string SFILE
    int i = 0; // Índice para percorrer SFILE

    while (SFILE[i] != '\0') {
        int j = 0; // Índice para percorrer SLOOK
        int match = 1; // Variável para indicar se houve correspondência entre os strings

        // Verificar se há correspondência entre os caracteres dos strings
        while (SLOOK[j] != '\0') {
            if (SFILE[i + j] != SLOOK[j]) {
                match = 0; // Não houve correspondência
                break;
            }
            j++;
        }

        // Se houve correspondência, atualizar o resultado e interromper a busca
        if (match) {
            *SRES = i;
            break;
        }

        i++;
    }

    // Imprimir o resultado
    printf("Resultado: %d\n", *SRES);

    return 0;
}
