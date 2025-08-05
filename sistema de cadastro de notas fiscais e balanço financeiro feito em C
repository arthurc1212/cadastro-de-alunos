#include <stdio.h>
#include <string.h>

#define MAX 100

// Estrutura para a nota fiscal
struct NotaFiscal {
    int numero;
    char cliente[50];
    float valor;
    char data[11]; // formato: dd/mm/aaaa
    char tipo[10]; // "compra" ou "venda"
};

// Protótipos
void telaInicial();
void cadastrarNota(struct NotaFiscal nf[], int *total);
void listarNotas(struct NotaFiscal nf[], int total);
void calcularBalanco(struct NotaFiscal nf[], int total);

int main() {
    struct NotaFiscal notas[MAX];
    int totalNotas = 0;
    int opcao;

    telaInicial();

    do {
        printf("\n========== MENU ==========\n");
        printf("1. Cadastrar Nota Fiscal\n");
        printf("2. Listar Notas Fiscais\n");
        printf("3. Ver Balanço Financeiro\n");
        printf("0. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);
        getchar(); // limpar buffer

        switch (opcao) {
            case 1:
                cadastrarNota(notas, &totalNotas);
                break;
            case 2:
                listarNotas(notas, totalNotas);
                break;
            case 3:
                calcularBalanco(notas, totalNotas);
                break;
            case 0:
                printf("Saindo...\n");
                break;
            default:
                printf("Opção inválida!\n");
        }

    } while (opcao != 0);

    return 0;
}

// Tela inicial com formatação
void telaInicial() {
    printf("*****************************\n");
    printf("*  SISTEMA DE NOTAS FISCAIS  *\n");
    printf("*        Bem-vindo!         *\n");
    printf("*****************************\n");
}

// Cadastro de nota fiscal
void cadastrarNota(struct NotaFiscal nf[], int *total) {
    if (*total >= MAX) {
        printf("Limite de notas fiscais atingido!\n");
        return;
    }

    printf("\n== Cadastro de Nota Fiscal ==\n");
    printf("Número da nota: ");
    scanf("%d", &nf[*total].numero);
    getchar();

    printf("Nome do cliente/fornecedor: ");
    fgets(nf[*total].cliente, 50, stdin);
    nf[*total].cliente[strcspn(nf[*total].cliente, "\n")] = '\0';

    printf("Valor da nota: ");
    scanf("%f", &nf[*total].valor);
    getchar();

    printf("Data (dd/mm/aaaa): ");
    fgets(nf[*total].data, 11, stdin);
    nf[*total].data[strcspn(nf[*total].data, "\n")] = '\0';

    do {
        printf("Tipo (compra/venda): ");
        fgets(nf[*total].tipo, 10, stdin);
        nf[*total].tipo[strcspn(nf[*total].tipo, "\n")] = '\0';
        if (strcmp(nf[*total].tipo, "compra") != 0 && strcmp(nf[*total].tipo, "venda") != 0) {
            printf("Tipo inválido. Digite 'compra' ou 'venda'.\n");
        }
    } while (strcmp(nf[*total].tipo, "compra") != 0 && strcmp(nf[*total].tipo, "venda") != 0);

    (*total)++;
    printf("Nota fiscal cadastrada com sucesso!\n");
}

// Lista as notas fiscais cadastradas
void listarNotas(struct NotaFiscal nf[], int total) {
    printf("\n== Lista de Notas Fiscais ==\n");
    for (int i = 0; i < total; i++) {
        printf("Nota %d:\n", i + 1);
        printf("  Número: %d\n", nf[i].numero);
        printf("  Cliente/Fornecedor: %s\n", nf[i].cliente);
        printf("  Valor: R$ %.2f\n", nf[i].valor);
        printf("  Data: %s\n", nf[i].data);
        printf("  Tipo: %s\n", nf[i].tipo);
        printf("-----------------------------\n");
    }

    if (total == 0) {
        printf("Nenhuma nota fiscal cadastrada.\n");
    }
}

// Cálculo do balanço financeiro
void calcularBalanco(struct NotaFiscal nf[], int total) {
    float totalCompras = 0.0, totalVendas = 0.0;
    for (int i = 0; i < total; i++) {
        if (strcmp(nf[i].tipo, "compra") == 0) {
            totalCompras += nf[i].valor;
        } else if (strcmp(nf[i].tipo, "venda") == 0) {
            totalVendas += nf[i].valor;
        }
    }

    float lucro = totalVendas - totalCompras;

    printf("\n== Balanço Financeiro ==\n");
    printf("Total de Compras: R$ %.2f\n", totalCompras);
    printf("Total de Vendas: R$ %.2f\n", totalVendas);
    if (lucro > 0)
        printf("Lucro: R$ %.2f\n", lucro);
    else if (lucro < 0)
        printf("Prejuízo: R$ %.2f\n", -lucro);
    else
        printf("Zerado: R$ 0.00\n");
}
