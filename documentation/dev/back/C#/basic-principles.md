# Dicas Para o Desenvolvimento

## **C#**

### Declaração de variáveis

Como não fazer ❌

Para declarar variáveis, evite usar nomes genéricos como

``` C#
string x = "valor";
int op1;
double rtnCt;
bool success;
```


Como fazer ✔

Para declarar variáveis, evite usar nomes genéricos como, seguindo o padrão
 **camelCase**

```C#
 string filtroDeNome = "valor";
 int opcaoInicial;
 double retornoCalculo;
```

E para variáveis booleanas, o ideal é que recebam o prefixo **"is"**

```C#
 bool isSuccess = false;
```

Quando ou não usar **`var`**

Usar a keyword **var** para a criação das varíveis é algo muito prático e útil, porem em determinados casos, onde não é tão fácil identificar o tipo pelo nome ou pelo valor que dara inicializaçào a variável, pode confundir um pouco, então é recomendado seguir dessa maneira

Quando não usar ❌

```C#
var resultadoOperacao = GetFooMethod(); //não sabemos o que o método retorna
var ordens = GetOrdens().Where(ordem => ordem.Ativa); //nesse caso estamos apenas atribuindo as ordens com valor de Ativo = true 
```

Quando usar ✔

```C#
var numerosAceitos = new [] {3, 4, 5, 7, 9};
var cliente = new Cliente();
```

### Convenção para nomear Classes, métodos, interfaces.

- Classes

Como não fazer ❌

```C#
Public class mainClass {};
```

Como fazer ✔

Devem seguir o padrão **PascalCase**, o mesmo vale para os métodos, como mostrado abaixo

```C#
Public class MainClass {}
```

- Métodos

Como não fazer ❌

```C#
Public class createEmployee()
{
}
```

Como fazer ✔ 

Devem seguir o padrão **PascalCase** 

```C#
Public class CadastrarPessoa() 
{
}
```

- Interfaces

Como não fazer ❌

```C#
Public interface players
{
}
```

Como fazer ✔ 

Devem seguir o padrão **PascalCase** e adicionando **"I"** como prefixo

```C#
Public interface IPlayers 
{
}
