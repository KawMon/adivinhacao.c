# adivinhacao.c

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
	//imprime cabecalho do jogo
	printf("\n\n");
	printf("  --------*----------*----------*--------\n");
	printf("  Bem-vindo ao nosso Jogo de Adivinhacao!\n");
	printf("  --------*----------*----------*--------\n");

	int segundos =time(0);
	srand(segundos);

	int numerogrande = rand();


	int numerosecreto = numerogrande % 100;
	int chute;
	int tentativas = 1;
	double pontos = 100;

	int acertou = 0;

	int nivel;
	printf("Qual o nivel de dificuldade voce quer jogar?\n");
	printf("(1) FACIL (2) MEDIO (3) DIFICIL\n\n");
	printf("Escolha:  ");
	scanf("%d", &nivel);

	int numerodetentativas;

	switch(nivel) {
		case 1:
			numerodetentativas = 20;
			break;

		case 2:
			numerodetentativas = 12;
			break;

		default:
			numerodetentativas = 6;
			break;
		}


	for(int i = 1; i <= numerodetentativas; i++){

		printf("Tentativa %d\n", tentativas);
		printf("Qual o seu chute?");

		scanf("%d", &chute);
		printf("Seu chute foi %d.\n", chute);

		if(chute <0) {
			printf("Voce nao pode chutar numeros negativos!\n");
			continue;
			}

			acertou = (chute == numerosecreto);
			int maior = chute > numerosecreto;

			if(acertou) {
				break;
			}

			else if(maior){
				printf("Seu chute foi maior que o numero secreto\n");
			}
			else {
				printf("Seu chute foi menor que o numero secreto\n");
			}
			
			tentativas++;

			double pontosperdidos = abs (chute - numerosecreto) / (double)2;
			pontosperdidos = pontosperdidos -1;

			pontos = pontos - pontosperdidos;
	        }


	 printf("--------------Fim de jogo!--------------\n\n");
	  
	if (acertou){
		printf("Voce ganhou! :3 \n");
		printf("Voce acertou em %d tentativas. Parabens ^-^ ", tentativas);
		printf ("Total de pontos: %.1f\n", pontos);

	} else{
		printf("Voce perdeu! :c ..Tente novamente! \n\n");
	}

	printf("----------------------------------------\n");

}
