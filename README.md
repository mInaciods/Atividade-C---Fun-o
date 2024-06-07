# Atividade-C---Função

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    char nome[50];
    float nota1, nota2, nota3, nota4;
    float media;
    char resultado[20];
} Aluno;

void adaluno(Aluno alunos[], int *num_alunos) {
    Aluno novo_aluno;

    printf("Escreva o nome do aluno: ");
    scanf("%s", novo_aluno.nome);
    printf("Escreva as 4 notas do aluno: ");
    scanf("%f %f %f %f", &novo_aluno.nota1, &novo_aluno.nota2, &novo_aluno.nota3, &novo_aluno.nota4);

    novo_aluno.media = (novo_aluno.nota1 + novo_aluno.nota2 + novo_aluno.nota3 + novo_aluno.nota4) / 4;

    if (novo_aluno.media < 4) {
        strcpy(novo_aluno.resultado, "Reprovado");
    } else if (novo_aluno.media >= 4 && novo_aluno.media <= 6) {
        strcpy(novo_aluno.resultado, "Recuperacao");
    } else {
        strcpy(novo_aluno.resultado, "Aprovado");
    }

    alunos[*num_alunos] = novo_aluno;
    (*num_alunos)++;
}

void resultados(Aluno alunos[], int num_alunos) {
    for (int i = 0; i < num_alunos; i++) {
        printf("Nome: %s, Media: %.2f, Resultado: %s\n", alunos[i].nome, alunos[i].media, alunos[i].resultado);
    }
}


void alterar_notas(Aluno alunos[], int num_alunos) {
    char nome[50];
    int encontrado = 0;

    printf("Escreva o nome do aluno para alterar as notas: ");
    scanf("%s", nome);

    for (int i = 0; i < num_alunos; i++) {
        if (strcmp(alunos[i].nome, nome) == 0) {
            printf("Escreva as novas 4 notas do aluno: ");
            scanf("%f %f %f %f", &alunos[i].nota1, &alunos[i].nota2, &alunos[i].nota3, &alunos[i].nota4);

            alunos[i].media = (alunos[i].nota1 + alunos[i].nota2 + alunos[i].nota3 + alunos[i].nota4) / 4;

            if (alunos[i].media < 4) {
                strcpy(alunos[i].resultado, "Reprovado");
            } else if (alunos[i].media >= 4 && alunos[i].media <= 6) {
                strcpy(alunos[i].resultado, "Recuperacao");
            } else {
                strcpy(alunos[i].resultado, "Aprovado");
            }

            encontrado = 1;
            printf("Notas alteradas com sucesso!\n");
            break;
        }
    }

    if (!encontrado) {
        printf("Aluno não encontrado.\n");
    }
}

void menu(int *opcao) {
    printf("Bem vindo ao sistema de notas\n\n");
    printf("Menu\n\n");
    printf("1- Cadastro de Alunos e Notas\n");
    printf("2- Alterar notas de Alunos\n");
    printf("3- Exibir Notas e Alunos\n");
    printf("4- Sair\n");
    printf("Escolha uma opcao: ");
    scanf("%d", opcao);
}

int main() {
    int opcao;
    Aluno alunos[100];
    int num_alunos = 0;

    while (1) {
        menu(&opcao);

        switch (opcao) {
            case 1:
                system("cls");
                adaluno(alunos, &num_alunos);
                break;
            case 2:
                system("cls");
                alterar_notas(alunos, num_alunos);
                break;
            case 3:
                system("cls");
                resultados(alunos, num_alunos);
                break;
            case 4:
                return 0;
            default:
                printf("Opcao invalida! Tente novamente.\n");
        }
    }
}
