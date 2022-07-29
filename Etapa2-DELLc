#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <string.h>

//Região de declaração de funções
void asterisc(int quantidade);
int perguntaOperacao();
void mostraMenu();
void procuraBolsistaZero(int anoDeProcura);
float calculaMediaAnual(int anoDaMedia);   
void listaRankings();
int codificaNomes(char nomeDigitado[100]);
void codificaMesmo(char recebeNomeParaCodificar[100], int tamanhoStringa);
void criptografia(char stringCriptografada[100]);
    


//desenvolvimento da main
int main(){
int operacaoNaMain, ano;
float mediaAnualNaMain;
char *nomeDigitadoNaMain[100];
mostraMenu();

operacaoNaMain = perguntaOperacao();

//menu que controla o fluxo do programa onde cada "case" corresponde à uma função do menu pedido pela DELL
while(operacaoNaMain != 5){
    switch(operacaoNaMain){
        
        case 1:
         asterisc(30);
         printf("Deseja saber informacoes sobre o bolsista 0 de qual ano? ");
         scanf("%d", &ano);
         while(ano>2016 || ano<2013){
           printf("por favor, digite um ano disponivel na planilha");
           scanf("%d", &ano);
         }
         asterisc(30);
         procuraBolsistaZero(ano);
        
         mostraMenu();
         operacaoNaMain = perguntaOperacao();
        break;
        
        case 2: 
        printf("qual o nome da pessoa que tu quer codificar e obter informacoes?");
        getchar();
         fgets(nomeDigitadoNaMain,100,stdin);
         
         codificaNomes(nomeDigitadoNaMain);
         
         mostraMenu();
         operacaoNaMain = perguntaOperacao();
        break;

        case 3:
         asterisc(30);
         printf("Deseja saber informacoes sobre a media anual de que ano? ");
         scanf("%d", &ano);
          while(ano>2016 || ano<2013){
           printf("por favor, digite um ano disponivel na planilha");
           scanf("%d", &ano);
         }
         asterisc(30);
         
         mediaAnualNaMain = calculaMediaAnual(ano);
         asterisc(50);
         printf("\n\nA media anual do ano %d e de %.2f \n \n", ano, mediaAnualNaMain);
         asterisc(50);

         mostraMenu();
         operacaoNaMain = perguntaOperacao();
        break;

        case 4:
         listaRankings();
         mostraMenu();
         operacaoNaMain = perguntaOperacao(); 
        break;
     }
}
//saída do programa
 asterisc(25); 
 printf(" Finalizando programa");
 asterisc(25);
}


//região de desenvolvimento das funções fora a main
//imprime asteriscos
void asterisc(int quantidade){
    int i;
    printf("\n");
    for(i=0;i<quantidade;i++){
        printf("*");
    }
    printf("\n");
}

//pergunta e valida operacao
int perguntaOperacao(){
 int operacao;
 printf("\n");
 printf("Digite a operacao desejada: ");
 scanf("%d", &operacao);

 while(operacao<1 || operacao>5){
     mostraMenu();

     printf("Digite uma operacao valida: ");
     scanf("%d", &operacao);
     }
     return operacao;
}

//mostra o menu 
void mostraMenu(){
    asterisc(105);
    printf(" BEM VINDO AO MENU DE CONSULTORIA PARA BOLSAS FORNECIDAS PELO GOVERNO BRASILEIRO EM PARCERIA COM A CAPES");
    asterisc(105);
    printf(" 1. [Consultar bolsa zero/ano]\n ");
    printf("2. [Codificar nomes]\n ");
    printf("3. [Consultar media anual]\n ");
    printf("4. [Ranking valores de bolsa]\n ");
    printf("5. [Terminar Programa]\n ");
}

//procura o bolsista 0 do ano requisitado e imprime o seu nome no console
void procuraBolsistaZero(int anoDeProcura){
 FILE *arquivo;
 char *result, *divisaoDaString[16], Linha[300];  
 int i;

 arquivo = fopen("br-capes-bolsistas-uab.csv", "r");
 if (arquivo == NULL) //verifica se o arquivo abriu corretamente
  {
    printf("Problemas na abertura do arquivo\n");   
    }else{
      printf("Arquivo aberto para leitura sem problemas\n");
  }

 while (!feof(arquivo))
  {
      result = fgets(Linha, 300, arquivo);  // o 'fgets' lê até 299 caracteres ou até o '\n'
      //printf("%s", Linha);
      
      divisaoDaString[0] = strtok(Linha, ";"); //fragmenta a string linha em substrings que são armazenadas em um vetor de ponteiros
    
      for(i=1;i<16;i++){                        //continua fazendo isso mas com um for 
      divisaoDaString[i] = strtok(NULL, ";");   
        }
        //controla se o ano que tem na linha é o que eu to procurando e se for, sai do programa, porque encontrou o bolsista 0 daquele ano
        if(atoi(divisaoDaString[4])==anoDeProcura){
            printf("\nNOME: %s", divisaoDaString[0]);
            printf("\nCPF: %s", divisaoDaString[1]);
            printf("\nEntidade de ensino: %s", divisaoDaString[2]);
            printf("\nValor da Bolsa: R$ %s", divisaoDaString[10]);
            break;
        }
  }     
      
 fclose(arquivo);
 
}

//calcula e retorna a média anual de acordo com o ano informado
float calculaMediaAnual(int anoDaMedia){
int i, somaMedias = 0, count = 0;
FILE *arquivo;
char *result, Linha[300], *DivisaoDaString[15];
float mediaAnual;


arquivo = fopen("br-capes-bolsistas-uab.csv", "r");
 if (arquivo == NULL) //verifica se o arquivo abriu corretamente
  {
     printf("Problemas na abertura do arquivo\n");
     
 }else{
      printf("Arquivo aberto para leitura sem problemas\n");
  }

 while (!feof(arquivo)){
        result = fgets(Linha, 300, arquivo);  // o 'fgets' lê até 299 caracteres ou até o '\n'
        DivisaoDaString[0] = strtok(Linha, ";"); //fragmenta a string linha em substrings que são armazenadas em um vetor de ponteiros
        for(i=0;i<15;i++){
        DivisaoDaString[i] = strtok(NULL, ";"); 
        } 
        //atoi converte uma *string para int, utilizada para poder comparar ou receber coisas de mesmo tipo
       if(atoi(DivisaoDaString[3])==anoDaMedia){
            somaMedias= somaMedias+ atoi(DivisaoDaString[9]); //condiciona pra saber se o ano é o mesmo pra somar e fazer a média daquele ano
            count++;
        }             
 }

 mediaAnual = (float)somaMedias/count;  //calcula e retorna a média

 fclose(arquivo);
 return mediaAnual;
}

//verifica toda a lista e informa os possuidores das maiores e das menores bolsas do arquivo
void listaRankings(){   
 FILE *arquivo;
 char *resulta, *divisaoDaString[11], Linha[300], *copy1, *copy2, *copy3, *mincopy1, *mincopy2, *mincopy3;
 int i, maioresBolsas[] = {0,0,0,0}, count = 0, menoresBolsas[4] = {1600,1600,1600,1600}; //variáveis inicializadas porque C é horrível pra lidar com sujeira

 arquivo = fopen("br-capes-bolsistas-uab.csv", "r");
 if (arquivo == NULL) //verifica se o arquivo abriu corretamente
  {
    printf("Problemas na abertura do arquivo\n");   
    }else{
      printf("Arquivo aberto para leitura sem problemas\n");
  }
 
 resulta = fgets(Linha, 300, arquivo); //pula a linha 0 do arquivo que tem as categorias9

 while (!feof(arquivo)) 
  {
      resulta = fgets(Linha, 300, arquivo);  // o 'fgets' lê até 299 caracteres do arquivo ou até o '\n'
      
      divisaoDaString[0] = strtok(Linha, ";"); //depois de fragmentar a string em substrings é salvo em um vetor de ponteiros cada substring
      
      for(i=1;i<11;i++){
      divisaoDaString[i] = strtok(NULL, ";"); 
      } 


      //coleta os dados das maiores bolsas
       if(atoi(divisaoDaString[10]) > maioresBolsas[0]){
          maioresBolsas[0] = atoi(divisaoDaString[10]);
          copy1 = malloc(strlen(divisaoDaString[0])+1);   //para atribuir o dado do ponteiro em tempo de execução, eu criei um ponteiro copy na heap
          strcpy(copy1, divisaoDaString[0]);              //copiei a original pro copy pra poder dar print sem perder o valor quando o programa andar
                                                        
       }else if(atoi(divisaoDaString[10]) > maioresBolsas[1]){  
           maioresBolsas[1] = atoi(divisaoDaString[10]);
           copy2 = malloc(strlen(divisaoDaString[0])+1);
          strcpy(copy2, divisaoDaString[0]);
       }else if(atoi(divisaoDaString[10]) > maioresBolsas[2]){
          maioresBolsas[2] = atoi(divisaoDaString[10]);
          copy3 = malloc(strlen(divisaoDaString[0])+1);
          strcpy(copy3, divisaoDaString[0]);      
       }
            
      //coleta os dados das menores bolsas
        if(atoi(divisaoDaString[10]) < menoresBolsas[0]){
          menoresBolsas[0] = atoi(divisaoDaString[10]);
          mincopy1 = malloc(strlen(divisaoDaString[0])+1);
          strcpy(mincopy1, divisaoDaString[0]);
       }else if(atoi(divisaoDaString[10]) < menoresBolsas[1]){
           menoresBolsas[1] = atoi(divisaoDaString[10]);
           mincopy2 = malloc(strlen(divisaoDaString[0])+1);
          strcpy(mincopy2, divisaoDaString[0]);
       }else if(atoi(divisaoDaString[10]) < menoresBolsas[2]){
            menoresBolsas[2] = atoi(divisaoDaString[10]);
            mincopy3 = malloc(strlen(divisaoDaString[0])+1);
            strcpy(mincopy3, divisaoDaString[0]);
       }





  } 
    
    //exibe as bolsas
    asterisc(50);
    printf(" Alunos com as maiores bolsas :\n");
      printf("\n%s", copy1);
      printf("\n%s", copy2);
      printf("\n%s", copy3);

    asterisc(50);
    printf(" Alunos com as menores bolsas :\n");
    printf("\n%s", mincopy1);
    printf("\n%s", mincopy2);
    printf("\n%s", mincopy3);
    asterisc(50);
    
    //libera os ponteiros que tavam ocupando espaço na heap porque não são mais necessários neste programa
    free(copy1);
    free(copy2);
    free(copy3);
    free(mincopy1);
    free(mincopy2);
    free(mincopy3);
    

   fclose(arquivo); //fecha o arquivo 
    
    }

//codifica o nome das pessoas e exibe-o junto com outros dados requisitados 
int codificaNomes(char nomeDigitado[100]){
 FILE *arquivo;
 char *result, *divisaoDaString[16], Linha[300], *copy1, normalString[100];  
 int i, count = 0, tamanhoString = 0;
 
 
 tamanhoString = strlen(nomeDigitado);

 for(i=0;i<tamanhoString;i++){
    nomeDigitado[i] = toupper(nomeDigitado[i]);
 }

 tamanhoString--;

 arquivo = fopen("br-capes-bolsistas-uab.csv", "r");
 if (arquivo == NULL) //verifica se o arquivo abriu corretamente
  {
    printf("Problemas na abertura do arquivo\n");   
    }else{
      printf("Arquivo aberto para leitura sem problemas\n");
  }
     result = fgets(Linha, 300, arquivo);  //pula a linha 0 da tabela, das categorias

 while (!feof(arquivo))
  {
      result = fgets(Linha, 300, arquivo);  // o 'fgets' lê até 299 caracteres ou até o '\n'
      
      divisaoDaString[0] = strtok(Linha, ";"); 

      for(i=1;i<16;i++){
      divisaoDaString[i] = strtok(NULL, ";"); 
        }

            
    
     if(strncmp(nomeDigitado, divisaoDaString[0],tamanhoString) == 0 ){ 
      asterisc(40);
      
      strcpy(normalString,divisaoDaString[0]);

      tamanhoString = strlen(normalString);
      tamanhoString--;
      codificaMesmo(normalString, tamanhoString);
      
      printf("\nano: %s", divisaoDaString[4]);
      printf("\nEntidade de ensino: %s", divisaoDaString[2]);
      printf("\nValor da bolsa: R$ %s", divisaoDaString[10]);
      asterisc(40);
      break;
     }

  }
      

 fclose(arquivo);
    
}

//funcao que faz a codificação do nome de acordo com a específicação
void codificaMesmo(char recebeNomeParaCodificar[100], int tamanhoStringa){
    char charAux[tamanhoStringa];
    int i,j;
   

    charAux[0] = recebeNomeParaCodificar[0];

    recebeNomeParaCodificar[0] = recebeNomeParaCodificar[tamanhoStringa];

    recebeNomeParaCodificar[tamanhoStringa] = charAux[0];

   
    for(i=0,j=tamanhoStringa;i<tamanhoStringa+1;i++,j--){
        charAux[i] = recebeNomeParaCodificar[j];
    }
    
    charAux[i] = '\0';

    criptografia(charAux);
}

//funcao que complementa a criptografia
void criptografia(char stringCriptografada[100]){
    int tamString = 0, i=0;
    
    tamString = strlen(stringCriptografada);
    tamString--;

    printf("\ncheguei aq");
    while(i<=tamString){
        switch(stringCriptografada[i]){
            case 'A':

             stringCriptografada[i] = 'B';
             i++;
             break;
            
            case 'B':
            
             stringCriptografada[i] = 'C';
             i++;
             break;
            case 'C':
             
             stringCriptografada[i] = 'D';
             i++;
             break;
            case 'D':

             stringCriptografada[i] = 'E';
             i++;
             break;
            case 'E':

             stringCriptografada[i] = 'F';
             i++;
             break;
            case 'F':

             stringCriptografada[i] = 'G';
             i++;
             break;
            case 'G':

             stringCriptografada[i] = 'H';
             i++;
             break;
            case 'H':

             stringCriptografada[i] = 'I';
             i++;
             break;
            case 'I':

             stringCriptografada[i] = 'J';
             i++;
             break;
            case 'J':

             stringCriptografada[i] = 'K';
             i++;
             break;
            case 'K':

             stringCriptografada[i] = 'L';
             i++;
             break;
            case 'L':

             stringCriptografada[i] = 'M';
             i++;
             break;
            case 'M':

             stringCriptografada[i] = 'N';
             i++;
             break;
            case 'N':

             stringCriptografada[i] = 'O';
             i++;
             break;
            case 'O':

             stringCriptografada[i] = 'P';
             i++;
             break;
            case 'P':

             stringCriptografada[i] = 'Q';
             i++;
             break;
            case 'Q':

             stringCriptografada[i] = 'R';
             i++;
             break;
            case 'R':

             stringCriptografada[i] = 'S';
             i++;
             break;
            case 'S':

             stringCriptografada[i] = 'T';
             i++;
             break;
            case 'T':

             stringCriptografada[i] = 'U';
             i++;
             break;
            case 'U':

             stringCriptografada[i] = 'V';
             i++;
             break;
            case 'V':

             stringCriptografada[i] = 'W';
             i++;
             break;
            case 'W':

             stringCriptografada[i] = 'X';
             i++;
             break;
            case 'X':

             stringCriptografada[i] = 'Y';
             i++;
             break;
            case 'Y':

             stringCriptografada[i] = 'Z';
             i++;
             break;
            case 'Z':

             stringCriptografada[i] = 'A';
             i++;
             break;

            case ' ':
             i++;
             break;

        }
    }

    
    printf("\nnome: %s ", stringCriptografada);

}
