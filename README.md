# Streams e lambda expressions em Java.

# Lambda Expressions.

O conceito Lambda foi adicionado ao Java na 8 versão com o objetivo principal de adicionar ao Java técnicas de linguagens funcionais.

## Exemplo simples em Haskell:

```Haskell
-- recebe um parâmetro  X e retorna X + 1.
(\X -> X + 1)
```

## As funções Lambda em Java tem a síntaxe:
```Java
// recebe um parâmetro x e retorna a soma de x + x.
(int x) -> {return x + x ;}

// recebe dois parâmetros x,y retorna a subtração x-y.
(int x, int y) -> {return x - y ;}

// não recebe nenhum parâmetro e retorna x.
() -> x
```

## Exemplo de funções lambda com classe de coleção:
Código sem a função Lambda:
```Java
// percorre uma lista e imprimi os valores da lista.
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
for(Integer n: list) {

    System.out.println(n);

}
```
Código com a função Lambda:
```Java
// percorre uma lista e imprimi os valores da lista.
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
list.forEach(n -> System.out.println(n));
```
No corpo de uma função Lambda podemos utilizar diversos comandos, como no caso do if logo abaixo:
```Java
// percorre uma lista e imprimi os valores da lista que forem pares.
System.out.println("Imprime todos os elementos pares da lista!");
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
list.forEach(n -> {
       if (n % 2 == 0) {
             System.out.println(n);
       }
});

// saída.
2
4
6
8
10
```

# Streams

Também adicionado ao Java na versão 8 está a Streams API, com o objetivo de trabalhar com conjuntos de elementos de forma mais simples e com um número menor de linhas de código. Isso corre graças à adição do paradigma funciona combinando com expressões Lambda.

A proposta da Streams API é diminuir a preocupação do desenvolvedor com a forma de implementar controle de fluxo ao lidar com coleçõex, deixando isso a cargdo da API.

Você descreve o que fazer com os dados em vez de iterar sobre eles. 

```Java
// cria uma lista de inteiros.
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// stream que vai imprimir todos os valores da lista,
numeros.stream()
                .forEach(System.out::println); // Imprime cada número filtrado

// faz a soma de todos os números da lista começando de 0, somando o próximo valor até o fim da lista.
int sum = numeros.stream()
        .reduce(0, Integer::sum); 
System.out.println(sum);

// filtra os números pares, então aplica a o dobro nesses números pares, e os imprime na tela.
numeros.stream()
               .filter(n -> n % 2 == 0) 
               .map(n -> n * 2) 
               .forEach(n -> System.out.println(n));

// saída.
4
8
12
16
20
```

# Conclusão

As funções Lambda junto com Stream é uma técnica bastante poderada que vai facilitar a escrita e leitura do código, tornando o código mais legível,  e também evitando que o desenvolvedor seja obrigado a escrever um código muito expansivo para implementações simples.

# Bibliográfia

[Expresssões Lambda](https://pt.wikibooks.org/wiki/Haskell/Lambdas_e_operadores](https://www.devmedia.com.br/java-streams-api-manipulando-colecoes-de-forma-eficiente/37630](https://www.devmedia.com.br/como-usar-funcoes-lambda-em-java/32826)

[Streams API](https://pt.wikibooks.org/wiki/Haskell/Lambdas_e_operadores](https://www.devmedia.com.br/java-streams-api-manipulando-colecoes-de-forma-eficiente/37630)
