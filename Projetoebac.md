#include <stdio.h> //biblioteca de comunicação com ousuário
#include <stdlib.h> //biblioteca de alocação de espaço em memória
#include <locale.h> // biblioteca de alocação de texto por região
#include <string.h> // biblioteca de strings


int registro()
{
	char arquivo[40]; // Váriaveis do tipo char [] -> valor strings. 
	char cpf[40];
	char nome[40];
	char sobrenome[40];
	char cargo[40];
	
	printf ("Digite o CPF a ser cadastrado: ");
	scanf ("%s",cpf); 
	
	strcpy(arquivo, cpf); // Responsável por copiar os valores da strings.
	
	FILE *file; // Cria o arquivo.
	file = fopen(arquivo,"w"); // Abre o arquivo
	fprintf(file,cpf); // Guarda a variavel no arquivo.
	fclose(file); // Fecha o arquivo.
	
	file = fopen(arquivo, "a"); // Adicionando uma vírgula
	fprintf(file, ",");
	fclose(file);
	
	printf("Digite o NOME a ser cadastrado: ");
	scanf ("%s", nome);
	
	file = fopen(arquivo, "a");
	fprintf(file,nome);
	fclose(file);
	
	file = fopen(arquivo, "a");
	fprintf(file, ",");
	fclose(file);
	
	printf("Digite o SOBRENOME a ser cadastrado: ");
	scanf("%s",sobrenome);
	
	file = fopen(arquivo, "a");
	fprintf(file,sobrenome);
	fclose(file);
	
	file = fopen(arquivo, "a");
	fprintf(file, ",");
	fclose(file);
	
	printf("Digite o CARGO a ser cadastrado: ");
	scanf("%s", cargo);
	
	file = fopen(arquivo, "a");
	fprintf(file,cargo);
	fclose(file);
	
		
		
}

int consulta()
{
	setlocale(LC_ALL, "Portuguese"); // Definindo idioma.
	
	char cpf[40];
	char conteudo[200]; // Onde o sistema guarda o cpf digitado pelo usuário. 
	
	printf("Digite a CPF a ser consultado: ");
	scanf("%s",cpf);
	
	FILE *file;
	file = fopen(cpf, "r"); // "r" pedindo para o program ler o conteudo do arquivo.
	
	if (file == NULL) // Cenário de ERRO.
	{
		printf("Não foi possivel abrir, arquivo não localizado!\n");
	}
	
	while(fgets(conteudo, 200, file) != NULL) // Laço de Repetição e Cenário de ERRO.
	{
		printf("\nEssas são as informações do usuário: ");
		printf("%s", conteudo);
		printf("\n\n");
	}
	system("pause");
}
int deletar()
{
	printf("Você escolheu deletar nomes!\n");
	system("pause");
}

int main ()
{
	int opcao=0; // Determinando um valor inicial para a variável.
	int laco=1; // Determinando o valor inicial para a variável (operação de repetição "laco").
	
	for(laco=1;laco=1;) // Operação de repetição
  {
	
	system("cls");
	
	setlocale(LC_ALL, "Portuguese"); // Definindo o idioma na biblioteca por localidade
	
	printf("### Programa de Usuários EBAC ###\n\n"); // Início do menu.
	printf ("No menu, escolha a opção desejada:\n\n"); 
	printf("\t1 - Registrar nomes\n"); // 
	printf("\t2 - Consultar nomes\n");
	printf("\t3 - Deletar nomes\n\n");
	printf("Opção:"); // Fim do Menu

	
	scanf("%d", &opcao); // Armazenando a escolha do usuário.
	
	system("cls");
	
	switch(opcao) // Estrutura de decisão
	{
	
		case 1:
		  registro();
		  break;
		
		case 2:
		  consulta();
		  break;
		  
		case 3:
		  deletar();
		  break;
			
		default:
		  printf("Essa opção não está disponivel. Tente novamente\n");
		  system("pause");
		  break;
	}

  }
    
}
