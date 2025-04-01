<header>

# Hello GitHub Actions
Jogo de Perguntas e Respostas, Cobra na Caixa e Gousmas War 

Sobre o Projeto 

Este repositório contém três jogos desenvolvidos em linguagem C: 

Jogo de Perguntas e Respostas: Um jogo de conhecimentos gerais com cinco perguntas de dificuldade crescente. 

Cobra na Caixa: Um jogo de suspense e estratégia onde dois exploradores tentam escapar de uma tumba egípcia escolhendo entre cinco caixas, uma contendo a chave para a saída e outra com uma cobra mortal. 

Gousmas War:
Um jogo de estratégia de dois jogadores onde controlam criaturas chamadas gousmas e elas podem se dividir e acumular fúria ao serem atacadas.

Integrantes da Equipe 

O projeto foi desenvolvido por: 

Brenno Yasuhei Tsuchiya 

Guilherme Mergulhão 

Funcionamento dos Jogos 

1. Jogo de Perguntas e Respostas 

O jogador responderá cinco perguntas de múltipla escolha. 

Cada resposta correta é confirmada com uma mensagem de acerto. 

Respostas erradas são corrigidas automaticamente. 

2. Cobra na Caixa 

Dois jogadores escolhem nomes de uma lista. 

O jogo sorteia aleatoriamente quem começa. 

Cada jogador escolhe uma entre cinco caixas. 

Se encontrar a chave, vence. Se encontrar a cobra, perde. 

O jogo permite repetir a partida após o fim. 

3. Gousmas War 

O jogo começa com 2 jogadores e cada um com duas gousmas.

Cada gousma tem 1 nível de fúria.

Ela pode atacar o inimigo distribuindo a fúria pro inimigo.

A gousma podem dividir a fúria pra sua parceira pra não ficar com um valor alto de fúria.

Se o nível de fúria chegar a 5 a gousma se desintegra.

Se o jogador perder todas suas gousmas(2 no total) ele perde.

Ajudas 

ChatGPT: para aprender como randomizar as caixas no jogo “Cobra na caixa”. 

Deepseek: aprender a colocar dois jogadores no jogo "gousmas war"

Tambem foi utilizado o vídeo https://youtu.be/RFthEp42L1s?si=HIYb7u6JaG5Y82sK para reforçar o entendimento dos comandos rand e srand.

aqui está o código:

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <locale.h>

// Protótipos das funções dos jogos
void perguntaserespostas();
void cobraNaCaixa();
void gousmasWar();

int main() {
    setlocale(LC_ALL, "Portuguese");
    int op, bp, cp, dp, ap;
    
    do {
        printf("\nBem vindo ao Trindade Gamer\n");
        printf("1 = Perguntas e repostas\n");
        printf("2 = Cobra na Caixa\n");
        printf("3 = Gousmas War\n");
        printf("4 = Créditos\n");
        printf("5 = Sair\n");
        printf("Sua escolha: ");
        scanf("%d", &op);
        
        switch(op) {
            case 1:
                printf("\nBem-vindo ao Perguntas e respostas\n");
                printf("Deseja jogar? 1 = Sim, 0 = Não, 2 = Regras\n");
                printf("Escolha: ");
                scanf("%d", &bp);
                
                if(bp == 1) {
                    perguntaserespostas();
                } 
                else if(bp == 2) {
                    printf("\n--- REGRAS DO PERGUNTAS E RESPOSTAS ---\n");
                    printf("m jogo de perguntas e respostas inclui 5 perguntas, da mais facil ate a mais dificil, onde apenas uma das quatro alternativas eh a certa.\n");
                    printf("Boa sorte!\n");
                }
                break;
                
            case 2:
                printf("\nBem-vindo ao Cobra na Caixa\n");
                printf("Deseja jogar? 1 = Sim, 0 = Não, 2 = Regras\n");
                printf("Escolha: ");
                scanf("%d", &cp);
                
                if(cp == 1) {
                    cobraNaCaixa();
                } 
                else if(cp == 2) {
                    printf("\n--- REGRAS DO COBRA NA CAIXA ---\n");
                    printf("Dois exploradores estão presos em uma tumba egípcia.\n");
                    printf("Há cinco caixas, uma com o botão da saída e outra com uma cobra mortal.\n");
                    printf("A cada rodada, as posições mudam aleatoriamente.\n");
                    printf("Escolha uma caixa para tentar escapar!\n");
                }
                break;
                
            case 3:
                printf("\nBem-vindo ao Gousmas War\n");
                printf("Deseja jogar? 1 = Sim, 0 = Não, 2 = Regras\n");
                printf("Escolha: ");
                scanf("%d", &dp);
                
                if(dp == 1) {
                    gousmasWar();
                } 
                else if(dp == 2) {
                    printf("\n--- REGRAS DO GOUSMAS WAR ---\n");
                    printf("Cada jogador começa com duas Gousmas (fúria 1).\n");
                    printf("Ao atacar, transfira toda fúria de uma Gousma sua para uma do oponente.\n");
                    printf("Se uma Gousma atingir fúria > 5, ela se desintegra.\n");
                    printf("Você pode dividir uma Gousma para criar outra (máx 2 Gousmas).\n");
                    printf("O objetivo é eliminar todas as Gousmas do oponente.\n");
                }
                break;
                
            case 4:
                printf("\nJogo criado por Brenno e Guilherme\n");
                printf("Deseja sair? 1 = Sim, 0 = Não\n");
                printf("Escolha: ");
                scanf("%d", &ap);
                if(ap == 1) {
                    exit(0);
                }
                break;
                
            case 5:
                printf("\nEncerrando...\n");
                exit(0);
                break;
                
            default:
                printf("\nOpção inválida! Tente novamente.\n");
        }
    } while(1);
    
    return 0;
}

// Implementação do perguntas e respostas
void perguntaserespostas() {
    int q1, q2, q3, q4, q5, p;
    int pontuacao = 0;
    
    printf("\nBem-vindo ao jogo de Perguntas e Respostas!!!\n");
    printf("Você responderá 5 perguntas de dificuldade crescente.\n");
    printf("Apenas uma alternativa em cada pergunta está correta.\n\n");
    
    // Pergunta 1
    printf("1) (Fácil) Qual é o maior planeta do Sistema Solar?\n");
    printf("1) Marte\n");
    printf("2) Terra\n");
    printf("3) Júpiter\n");
    printf("4) Netuno\n");
    printf("Sua resposta: ");
    scanf("%d", &q1);
    
    if(q1 == 3) {
        printf("Parabéns!!! Resposta correta\n");
        pontuacao++;
    } else {
        printf("Resposta incorreta! A resposta correta era Júpiter (opção 3).\n");
    }
    
    printf("\nPronto para a próxima pergunta? (1 = Sim, 0 = Não): ");
    scanf("%d", &p);
    if(p != 1) {
        printf("Vamos continuar mesmo assim!\n");
    }
    
    // Pergunta 2
    printf("\n2) (Médio) Quem pintou a famosa obra Mona Lisa?\n");
    printf("1) Michelangelo\n");
    printf("2) Leonardo da Vinci\n");
    printf("3) Vincent van Gogh\n");
    printf("4) Pablo Picasso\n");
    printf("Sua resposta: ");
    scanf("%d", &q2);
    
    if(q2 == 2) {
        printf("Parabéns!!! Resposta correta\n");
        pontuacao++;
    } else {
        printf("Resposta incorreta! A resposta correta era Leonardo da Vinci (opção 2).\n");
    }
    
    printf("\nPronto para a próxima pergunta? (1 = Sim, 0 = Não): ");
    scanf("%d", &p);
    if(p != 1) {
        printf("Não tem volta, vamos em frente!\n");
    }
    
    // Pergunta 3
    printf("\n3) (Intermediário) Em que ano aconteceu a Independência do Brasil?\n");
    printf("1) 1492\n");
    printf("2) 1789\n");
    printf("3) 1822\n");
    printf("4) 1889\n");
    printf("Sua resposta: ");
    scanf("%d", &q3);
    
    if(q3 == 3) {
        printf("Parabéns!!! Resposta correta\n");
        pontuacao++;
    } else {
        printf("Resposta incorreta! A resposta correta era 1822 (opção 3).\n");
    }
    
    printf("\nPronto para a próxima pergunta? (1 = Sim, 0 = Não): ");
    scanf("%d", &p);
    if(p != 1) {
        printf("Seguindo para a próxima...\n");
    }
    
    // Pergunta 4
    printf("\n4) (Difícil) Qual é o elemento químico mais abundante na crosta terrestre?\n");
    printf("1) Ferro\n");
    printf("2) Oxigênio\n");
    printf("3) Silício\n");
    printf("4) Hidrogênio\n");
    printf("Sua resposta: ");
    scanf("%d", &q4);
    
    if(q4 == 2) {
        printf("Parabéns!!! Resposta correta\n");
        pontuacao++;
    } else {
        printf("Resposta incorreta! A resposta correta era Oxigênio (opção 2).\n");
    }
    
    printf("\nPronto para a última pergunta? (1 = Sim, 0 = Não): ");
    scanf("%d", &p);
    if(p != 1) {
        printf("Última pergunta, vamos lá!\n");
    }
    
    // Pergunta 5
    printf("\n5) (Muito difícil) Qual cientista formulou a equação da Mecânica Quântica na forma de matrizes?\n");
    printf("1) Niels Bohr\n");
    printf("2) Werner Heisenberg\n");
    printf("3) Erwin Schrödinger\n");
    printf("4) Max Planck\n");
    printf("Sua resposta: ");
    scanf("%d", &q5);
    
    if(q5 == 2) {
        printf("Parabéns!!! Resposta correta\n");
        pontuacao++;
    } else {
        printf("Resposta incorreta! A resposta correta era Werner Heisenberg (opção 2).\n");
    }
    
    // Resultado final
    printf("\n--- RESULTADO FINAL ---\n");
    printf("Você acertou %d de 5 perguntas!\n", pontuacao);
    
    if(pontuacao == 5) {
        printf("Excelente! Você é um verdadeiro sabichão!\n");
    } else if(pontuacao >= 3) {
        printf("Bom trabalho! Você sabe bastante coisa.\n");
    } else if(pontuacao >= 1) {
        printf("Você acertou algumas, mas pode melhorar!\n");
    } else {
        printf("Hmm... talvez seja hora de estudar um pouco mais!\n");
    }
}

// Implementação do Cobra na Caixa
void cobraNaCaixa() {
    printf("\nIniciando Cobra na Caixa...\n");
    
    int caixas[5];
    int escolha, i, chave, cobra;
    int jogando = 1;
    int turno;
    int repetir;

    char *nomes[7] = {"Joãozinho", "Anthony", "Klaus", "Dolores", "Joan", "Robert", "Chester"};
    int jogador1, jogador2;

    srand(time(NULL));

    while (1) {
        printf("\nEscolha um nome:\n");
        for (i = 0; i < 7; i++) {
            printf("%d - %s\n", i + 1, nomes[i]);
        }
        printf("Jogador 1, escolha um número (1-7): ");
        scanf("%d", &jogador1);
        printf("Jogador 2, escolha um número (1-7): ");
        scanf("%d", &jogador2);

        jogador1--;
        jogador2--;

        turno = rand() % 2;
        printf("\n%s começa!\n", (turno == 0) ? nomes[jogador1] : nomes[jogador2]);

        for (; jogando == 1;) {
            for (i = 0; i < 5; i++) {
                caixas[i] = 0;
            }

            chave = rand() % 5;
            do {
                cobra = rand() % 5;
            } while (cobra == chave);

            caixas[chave] = 1;
            caixas[cobra] = -1;

            printf("\n%s, escolha uma caixa (1-5): ", (turno == 0) ? nomes[jogador1] : nomes[jogador2]);
            scanf("%d", &escolha);
            escolha--; // Ajuste para índice 0-4

            if (escolha < 0 || escolha >= 5) {
                printf("Escolha inválida! Tente novamente.\n");
                continue;
            }

            if (caixas[escolha] == 1) {
                printf("\n%s encontrou o botão e escapou da tumba! Vitória!\n", (turno == 0) ? nomes[jogador1] : nomes[jogador2]);
                jogando = 0;
            } else if (caixas[escolha] == -1) {
                printf("\n%s encontrou a cobra mortal e perdeu!\n", (turno == 0) ? nomes[jogador1] : nomes[jogador2]);
                jogando = 0;
            } else {
                printf("A caixa está vazia. O jogo continua...\n");
                turno = 1 - turno;
            }
        }

        printf("\nDeseja jogar novamente? (1 - Sim, 0 - Não): ");
        scanf("%d", &repetir);
        if (repetir == 1) {
            jogando = 1;
        } else {
            printf("Voltando ao menu principal...\n");
            break;
        }
    }
}

// Implementação do Gousmas War
void gousmasWar() {
    int jogador1[2] = {1, 1};
    int jogador2[2] = {1, 1};
    int turno = 1;
    
    printf("\nIniciando Gousmas War...\n");
    
    while(1) {
        printf("\nJogador %d:\n", turno);
        printf("Suas Gousmas: %d e %d\n", jogador1[0], jogador1[1]);
        printf("Oponente: %d e %d\n", jogador2[0], jogador2[1]);
        
        if((jogador1[0] > 5 || jogador1[0] == 0) && (jogador1[1] > 5 || jogador1[1] == 0)) {
            printf("\nJogador 1 perdeu todas as Gousmas!\n");
            printf("Jogador 2 venceu!\n");
            break;
        }
        if((jogador2[0] > 5 || jogador2[0] == 0) && (jogador2[1] > 5 || jogador2[1] == 0)) {
            printf("\nJogador 2 perdeu todas as Gousmas!\n");
            printf("Jogador 1 venceu!\n");
            break;
        }
        
        printf("\n1. Atacar\n2. Dividir\nEscolha: ");
        int escolha;
        scanf("%d", &escolha);
        
        if(escolha == 1) {
            printf("Sua Gousma (1 ou 2): ");
            int minha;
            scanf("%d", &minha);
            
            printf("Gousma inimiga (1 ou 2): ");
            int inimiga;
            scanf("%d", &inimiga);
            
            if(minha < 1 || minha > 2 || inimiga < 1 || inimiga > 2) {
                printf("Escolha inválida!\n");
                continue;
            }
            
            if(turno == 1) {
                jogador2[inimiga-1] += jogador1[minha-1];
                jogador1[minha-1] = 0;
            } else {
                jogador1[inimiga-1] += jogador2[minha-1];
                jogador2[minha-1] = 0;
            }
        } 
        else if(escolha == 2) {
            printf("Gousma para dividir (1 ou 2): ");
            int g;
            scanf("%d", &g);
            
            printf("Quanto de fúria transferir: ");
            int f;
            scanf("%d", &f);
            
            if(turno == 1) {
                if(jogador1[1] == 0 || jogador1[1] > 5) {
                    jogador1[1] = f;
                    jogador1[g-1] -= f;
                } else {
                    printf("Você já tem 2 Gousmas!\n");
                }
            } else {
                if(jogador2[1] == 0 || jogador2[1] > 5) {
                    jogador2[1] = f;
                    jogador2[g-1] -= f;
                } else {
                    printf("Você já tem 2 Gousmas!\n");
                }
            }
        }
        else {
            printf("Opção inválida!\n");
            continue;
        }
        
        turno = (turno == 1) ? 2 : 1;
    }
}

</footer>
