# Calculando-estatistica-em-Java

Ir para o conteúdo principal
 
Moodle - IFRS

Programação Básica com Java III - Turma 2022B
Painel Meus cursos  PBJIII2022B 1. Integrando Estruturas de Controle  1.3. Calculando Estatísticas
1.3. Calculando Estatísticas
Um belo dia você vai checar seu e-mail e se depara com a seguinte mensagem:

Sou empresário e possuo um cinema com capacidade para 100 pessoas. Estamos realizando uma pesquisa com nossos clientes essa noite, e preciso de um programa que contabilize estes resultados e nos gere algumas estatísticas. Pode nos ajudar nessa tarefa? Estou lhe enviando um e-mail com mais informações.


Você responde o e-mail perguntando mais detalhes e recebe a seguinte resposta:



Programa para nosso cinema

De: Administração do Cinema

Para: Você

 

Olá,

                Como prometido aí vão mais informações sobre o problema que temos:

 

Nosso cinema possui capacidade para 100 pessoas e está sempre com ocupação total. Certo dia, cada espectador respondeu a um questionário, no qual constava sua idade e sua opinião em relação ao filme, segundo as seguintes notas:

 

                Nota                      Significado

                A                             Ótimo

                B                             Bom

                C                             Regular

                D                             Ruim

                E                             Péssimo

 

Precisamos de um programa que, lendo esses dados, nos mostre:

a quantidade de respostas Ótimo;
a média de idade das pessoas que responderam Ruim;
a porcentagem de respostas Péssimo e a maior idade que utilizou essa opção.


O problema parece complicado, não acha? Mas com as ferramentas que você já aprendeu até aqui pode resolvê-lo.  Vamos começar analisando quais seriam as entradas e saídas desse problema.

Entradas: idade e nota de cada espectador (são 100 pessoas no total).
Saídas: quantidade de respostas “Ótimo” (ou seja, de espectadores que concederam nota A ao cinema); média de idade das pessoas que responderam “Ruim” (nota D); porcentagem de respostas “Péssimo” (nota E) e a maior idade que utilizou essa opção.


Para tratar a entrada de dados podemos desenvolver o pseudocódigo abaixo. Foram três variáveis: uma para servir de contadora na estrutura para...faça, outra para armazenar a idade de cada espectador e outra para a nota de cada um (você verá que apenas uma variável para cada é suficiente).



Algoritmo “Estatísticas do cinema”

var

idade, cont: inteiro

nota: caractere

início

       para cont de 1 até 100 faça

leia idade, nota

fim para


fim


O primeiro resultado que nosso programa deve gerar é a quantidade de respostas Ótimo fornecida pelos espectadores.  O que vamos fazer é um processo similar à contagem manual de votos. Em uma contagem manual de votos, cada cédula é verificada e dependendo do voto contido nela, a quantidade de votos de um determinado candidato é atualizada (é somado mais um voto a ele). Em nosso caso, a cada nota lida, devemos atualizar a quantidade de respostas Ótimo em mais uma unidade.

Como fazer isso em nosso algoritmo? Em primeiro lugar, precisamos armazenar a quantidade de respostas “Ótimo” em algum lugar. E quando falamos em armazenar coisas precisamos de que? Variáveis, claro! A figura abaixo mostra nosso algoritmo alterado com a criação de uma variável para armazenar a quantidade de respostas “Ótimo”. Observe que também inicializamos a variável com o valor zero, já que inicialmente essa é a quantidade de respostas (nenhuma nota foi lida ainda).



Algoritmo “Estatísticas do cinema”

var

idade, cont, resOtimo: inteiro

nota: caractere

início

       resOtimo ← 0 

para cont de 1 até 100 faça

leia idade, nota

fim para


fim


Agora precisamos verificar a resposta de cada espectador.  Como se faz com cada cédula de votação, é preciso analisar cada nota lida e verificar se é Ótimo ou não. Caso seja, contabilizar mais uma resposta (aumentar em um o valor da variável resOtimo). Esse tipo de teste pode ser facilmente realizado utilizando uma estrutura se...então, colocada dentro do para...faça, como mostrado abaixo. No final do algoritmo, já se acrescentou também uma instrução escreva para mostrar a contagem de respostas obtida.



Algoritmo “Estatísticas do cinema”

var

idade, cont, resOtimo: inteiro

nota: caractere

início

       resOtimo ← 0

para cont de 1 até 100 faça

leia idade, nota 

se nota = ‘A’ então

       resOtimo ← resOtimo + 1

fim se

fim para

escreva resOtimo

fim



Como a variável nota é do tipo caractere, só podemos compará-la com valores desse tipo. Por isso, a letra A está entre aspas simples. Lembre-se que valores constantes do tipo caractere devem ser escritos entre aspas simples.

Nosso programa também deve mostrar a média de idade das pessoas que responderam “Ruim”.  Como já vimos, uma média é calculada somando-se os valores considerados e dividindo-se pelo número total de entidades envolvidas. Em nosso caso, devemos somar a idade de todas as pessoas que responderam “Ruim” e dividir a soma obtida pelo número de pessoas que concederam essa resposta. Para contar o número de pessoas que responderam “Ruim” podemos fazer algo similar ao que fizemos antes, para as pessoas que responderam “Ótimo”.  Assim, podemos modificar o algoritmo anterior como mostrado na abaixo. Utilizamos estruturas se...então aninhadas para melhor eficiência do algoritmo.



Algoritmo “Estatísticas do cinema”

var

idade, cont, resOtimo, resRuim : inteiro

nota: caractere

início

       resOtimo ← 0

       resRuim ← 0 

para cont de 1 até 100 faça

leia idade, nota

se nota = ‘A’ então

       resOtimo ← resOtimo + 1

senão

       se nota = ‘D’ então

             resRuim ← resRuim + 1

       fim se

fim se

fim para

escreva resOtimo

fim



Para calcular a média de idades precisamos também somar as idades dessas pessoas que responderam “Ruim”.  Para isso, podemos nos basear no algoritmo mostrado no curso Programação Básica com Java II, onde se calculava a média de notas de uma turma de estudantes. Precisamos adaptar essa solução ao nosso caso, pois aqui só iremos acrescentar a idade à soma total se a nota informada pelo espectador for D (Ruim). Assim, a instrução de soma deve ficar dentro do segundo se...então do algoritmo, como mostrado abaixo. Não se deve esquecer de inicializar a variável somaIdades com zero (como vimos, variáveis para somas como esta precisam de um valor inicial e o zero é um valor neutro para a operação de adição).  Note também que, no final do algoritmo, antes de mostrar os resultados, calculamos a média das idades, dividindo a soma das idades pelo número de espectadores que responderam “Ruim”.



Algoritmo “Estatísticas do cinema”

var

idade, cont, resOtimo, resRuim, somaIdades : inteiro

nota: caractere

mediaIdades: real

início

       resOtimo ← 0

       resRuim ← 0

       somaIdades ← 0 

para cont de 1 até 100 faça

leia idade, nota

se nota = ‘A’ então

       resOtimo ← resOtimo + 1

senão

       se nota = ‘D’ então

             resRuim ← resRuim + 1

             somaIdades ← somaIdades + idade

       fim se

fim se

fim para

mediaIdades ← somaIdades / resRuim

escreva resOtimo, mediaIdades

fim



Os últimos dois resultados que o programa precisa gerar incluem o percentual de respostas “Péssimo” e a maior idade que concedeu essa nota. Para o primeiro resultado precisamos dividir o número de respostas “Péssimo” por 100 e multiplicar por 100. Fazendo uma pequena simplificação matemática, chegamos a conclusão que neste caso específico (onde temos exatamente 100 espectadores), o percentual de respostas “Péssimo” é exatamente igual ao número de espectadores que concederam tal nota. Assim, basta fazer algo similar ao que já fizemos para contar o número de respostas “Ótimo” e o número de respostas “Ruim”.

O caso de verificar a maior idade que concedeu a resposta “Péssimo” constitui um problema similar ao que resolvemos no algoritmo para verificar a maior de 20 notas, mostrado no tópico anterior. Naquele problema, o objetivo era encontrar a maior de 20 notas informadas pelo usuário. Em nosso caso, precisamos apenas levar em consideração as idades de espectadores que concederam nota “Péssimo”. O pseudocódigo resultante é mostrado abaixo.



Algoritmo “Estatísticas do cinema”

var

idade, cont, resOtimo, resRuim, somaIdades, resPessimo : inteiro

maiorIdade: inteiro

nota: caractere

mediaIdades: real

início

       resOtimo ← 0

       resRuim ← 0

       somaIdades ← 0

       resPessimo ← 0

       maioridade ← -1

para cont de 1 até 100 faça

leia idade, nota

se nota = ‘A’ então

       resOtimo ← resOtimo + 1

senão

       se nota = ‘D’ então

             resRuim ← resRuim + 1

                           somaIdades ← somaIdades + idade

                    senão

                           se nota = ‘E’ então

                                  resPessimo ← resPessimo + 1

                                  se idade > maiorIdade então

                                        maiorIdade ← idade

                                  fim se

                           fim se

       fim se

fim se

fim para

mediaIdades ← somaIdades / resRuim

escreva resOtimo, mediaIdades, resPessimo, maiorIdade

fim



A variável maiorIdade deverá conter  o valor da idade da pessoa mais velha que concedeu nota “Péssimo” ao cinema. Note que inicializamos a variável com -1. Fizemos isto por questões de simplicidade, pois é impossível que exista uma idade negativa! Qualquer que seja a primeira idade informada, será maior que -1. Uma alternativa seria inicializar a variável com a idade do primeiro espectador lido que respondeu nota E (“Péssimo” ).  Essa segunda opção geraria um código maior e mais complexo. Por isso, optamos pela primeira alternativa.

O programa em Java correspondente é mostrado abaixo. 


public class EstatisticasCinema {

public static void main(String[] args) {

int idade, somaIdades = 0, maioridade = -1;

int resOtimo = 0, resRuim = 0, resPessimo = 0;

char nota;

double mediaIdades;

 

for(int cont = 1; cont <= 100; cont++) {

System.out.printf(“--- ESPECTADOR %03d ---”, cont);

System.out.printf(“Idade: ”);

idade = Double.parseDouble(System.console().readLine());

System.out.printf(“Nota: ”);

nota = System.console().readLine().charAt(0);

 

if(nota == ‘A’)

       resOtimo++;

else if(nota == ‘D’) {

       resRuim++;

                     somaIdades += idade;

              } else if(nota == ‘E’) {

              resPessimo++;

              if(idade > maiorIdade)

                                  maiorIdade = idade;

              }

       }

       mediaIdades = somaIdades / resRuim;

 

       System.out.printf(“Notas Ótimo = %d\n”, resOtimo);

       System.out.printf(“Média Idades = %.1f\n”, mediaIdades);

       System.out.printf(“Percentual notas “Péssimo” = %d\n”, resPessimo);

       System.out.printf(“Maior idade a responder “Péssimo” = %d\n”, maiorIdade);

}




}


Note que ao declarar as variáveis já realizamos a inicialização daquelas que a necessitam.  A variável cont, usada como contadora da estrutura para...faça no algoritmo, foi declarada na própria estrutura for no programa Java. Note também como o programa faz a leitura de um valor char. Utilizamos o comando System.console().readLine().charAt(0) que lê uma sequência qualquer de caracteres, mas preenche a variável apenas com o primeiro caractere digitado.  É possível utilizar esse tipo de comando sempre que se precisar ler um valor do tipo char.  Importante não esquecer, é claro, que comparações de igualdade em Java são realizadas com o operador == e não com o operador =.

Última atualização: domingo, 1 nov 2020, 17:13
Seguir para...
Academi
Dúvidas? 
Perguntas frequentes

Fale conosco | Suporte | Contato

Informação
Termos e Condições de Uso
Aviso de Privacidade e Proteção de Dados Pessoais
Contato
Rua Gen. Osório, 348, Bento Gonçalves/RS
Siga-nos
Copyright © 2017 - Desenvolvido por LMSACE.com. Distribuído por Moodle

Português - Brasil ‎(pt_br)‎
English ‎(en)‎
Español - Internacional ‎(es)‎
Français ‎(fr)‎
Italiano ‎(it)‎
Português - Brasil ‎(pt_br)‎
Mudar para o tema padrão
