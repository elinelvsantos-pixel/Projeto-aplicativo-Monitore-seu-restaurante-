# Projeto-aplicativo-Monitore-seu-restaurante-
Seja bem-vindo ao aplicativo"Monitore seu restaurante, Nele ficará fácil descobrir o termômetro dos seus negócios, carinhosamente apelidado de"almoçômetro".

Situação problema: Matriz com dados alimentados pelo usuário anteriormente, disponibiliza diversos relatórios gerenciais sobre o periodo dos 7 dias da semana, de três restaurantes de uma mesma franquia.

Segue código fonte em Linguagem C:

#include <stdio.h>

int main() {
    // matriz representando os 7 dias da semana e quantidade de almoços vendidos em 3 lojas
    int Almoçometro[7][3] = {
        {10, 22,  8},   // Segunda
        {12, 26,  5},   // Terça
        {15, 24, 11},   // Quarta
        {9,  21, 15},   // Quinta
        {20, 33, 25},   // Sexta
        {27, 25, 22},   // Sábado
        {35, 32, 26}    // Domingo
    };

    char *dias[7] = {"Segunda", "Terça", "Quarta", "Quinta", "Sexta", "Sábado", "Domingo"};

    int maior = Almoçometro[0][0], menor = Almoçometro[0][0];
    int diaMaior = 0, lojaMaior = 0, diaMenor = 0, lojaMenor = 0;
    int totais[3] = {0,0,0};
    float media = 0;
    int opcao;

    // percorre matriz para calcular maior, menor e totais
    for (int i = 0; i < 7; i++) {
        for (int j = 0; j < 3; j++) {
            if (Almoçometro[i][j] > maior) {
                maior = Almoçometro[i][j];
                diaMaior = i;
                lojaMaior = j;
            }
            if (Almoçometro[i][j] < menor) {
                menor = Almoçometro[i][j];
                diaMenor = i;
                lojaMenor = j;
            }
            totais[j] += Almoçometro[i][j];
            media += Almoçometro[i][j];
        }
    }

    media /= (7 * 3); // média geral de todas as lojas

    // mensagem inicial
    printf("====================================================\n");
    printf("Seja bem-vindo ao aplicativo \"Monitore seu restaurante\"!\n");
    printf("Nele ficará fácil descobrir o termômetro dos seus negócios,\n");
    printf("carinhosamente apelidado de \"almoçômetro\".\n");
    printf("====================================================\n\n");

    // loop do menu
    do {
        printf("\n================ ESCOLHA UMA OPÇÃO DO MENU ================\n");
        printf("1 - Mostrar maior venda\n");
        printf("2 - Mostrar menor venda\n");
        printf("3 - Mostrar total semanal por loja\n");
        printf("4 - Mostrar média geral\n");
        printf("5 - Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);

        switch(opcao) {
            case 1:
                printf("\nO dia da semana com MAIOR número de vendas foi %s\n", dias[diaMaior]);
                printf("Na loja %d, com %d almoços vendidos.\n", lojaMaior + 1, maior);
                break;

            case 2:
                printf("\nO dia da semana com MENOR número de vendas foi %s\n", dias[diaMenor]);
                printf("Na loja %d, com %d almoços vendidos.\n", lojaMenor + 1, menor);
                break;

            case 3:
                printf("\nTotal semanal por loja:\n");
                for (int j = 0; j < 3; j++) {
                    printf("Loja %d: %d almoços\n", j+1, totais[j]);
                }
                break;

            case 4:
                printf("\nA média geral de vendas foi: %.2f almoços por dia/loja\n", media);
                break;

            case 5:
                printf("\nSaindo do programa...\n");
                printf("O aplicativo \"Monitore seu restaurante\" agradece seu contato, até breve!\n");
                break;

            default:
                printf("\nOpção inválida! Tente novamente.\n");
        }

    } while(opcao != 5);

    return 0;
}
