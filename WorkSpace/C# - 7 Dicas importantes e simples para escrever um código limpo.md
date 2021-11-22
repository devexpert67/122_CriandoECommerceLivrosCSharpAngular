**C# - 7 Dicas importantes e simples para escrever um código limpo**

------

| ![img](http://www.macoratti.net/mac3_1.jpg) | Neste artigo vou apresentar 7 dicas importantes e simples que vão tornar o seu código C# mais limpo e fácil de manter. |
| ------------------------------------------- | ------------------------------------------------------------ |
|                                             |                                                              |

Eu creio que todo o programador, independente da linguagem que esteja usando, deseja escrever um código que seja robusto, fácil de entender e fácil de manter.

[![img](http://www.macoratti.net/c_solid1.jpg)](http://www.macoratti.net/curso_capp_solid.htm)

A princípio isso pode parecer uma tarefa para os '*experts*' mas na verdade um código limpo e fácil de entender pode ser feito a partir de regras simples.

A seguir vou apresentar algumas regras básicas de padronização de codificação que podem ser seguidas e usadas por programadores de qualquer nível de conhecimento.

**![img](http://www.macoratti.net/12/10/badsmell.jpg) Code Smell (Um código que fede)**

**Code Smell** *(Um código que cheira, fede*) é uma palavra técnica usada para descrever a qualidade do código - como um programador escreve este código, sendo também utilizada para descrever o código que você não gosta. Nesse sentido, é sinônimo de feio, sujo, repetido, etc.
 
Um código que cheira é um código ruim mas que nem por isso deixa de funcionar e por isso mesmo ele é difícil de entender e de manter. Abaixo temos alguns motivos que fazem com que um código seja definido como um código que fede:

\- Código duplicado
\- Métodos muito grandes
\- Classes com muitas variáveis ​​de instância
\- Classes com muito código

Agora, vamos ver como podemos escrever um código limpo e evitar esses cheiros no programa. A maneira mais fácil e simples e começar pela norma básica de codificação, ou seja, pela convenção da nomenclatura.

Enquanto estamos codificando, vamos nos concentrar em nosso padrão de nomenclatura usada. Existem 2 tipos principais de padrões de nomenclatura que estamos usando nos dias de hoje.

1. **Pascal Casing
   **Uma palavra com a primeira letra maiúscula, e a primeira letra de cada palavra-parte subseqüente capitalizada.
   Ex - CalculaImpostoDeRenda(), ValorDoDesconto**
   ** 
2. **Camel Casing
   **Uma palavra com a primeira letra minúscula e a primeira letra de cada palavra subseqüente-parte capitalizada.
   Ex: valorDoDesconto , nomeCompleto, valorDoImpostoSobreServico

A seguir veremos como aplicar esses padrões de forma correta para ter um código limpo.

**1 - Ao nomear uma classe e seus métodos utilize o padrão Pascal Case**

```
    public class **FuncionariosDetalhes**    {        public void **GetSalarioFuncionario**()        {            //código        }    }
```

**2 - Ao nomear variáveis e parâmetros utilize padrão Camel Case**

```
    public class FuncionariosDetalhes    {        private double **salarioTotal** = 0;        private double **descontoImposto** = 0;``        public void GetSalarioFuncionario()        {            int **valor** = 3000;        }    }
```

**3 - Ao utilizar Interfaces sempre use como prefixo inicial a letra "I" e depois siga o padrão Pascal Case**

```
    interface **ICalculoDescontoSobreSalario**    {        void GetValorAdiamento();        double GetPercentualImposto();    }
```

**4 - Ao nomear classes, métodos, variáveis e interfaces utilize nomes significativos que sejam auto descritivos e pertinentes ao seu propósito**

Vamos comparar dois exemplos de trechos de códigos onde no primeiro temos um código sujo e no segundo um código limpo:

| ![img](http://www.macoratti.net/17/05/negativo.png) public class Funcionario  {   public void GetValor(double s, double he, double d)   {    int t = s + he - d;  } } | ![img](http://www.macoratti.net/17/05/positivo.png) public class CalculoSalarioFuncionario  {    /// <summary>    /// Calcula o valor do salário de um funcionário horista    /// </summary>    /// <param name="salario"></param>             /// <param name="horaExtra"></param>    /// <param name="desconto"></param>   public void GetValorSalario(int salario, int horaExtra, int desconto)    {      int valorTotalSalario = salario + horaExtra - desconto;    } } |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

Qual dos dois trechos de código é mais fácil de entender ?

- Sempre utilize nomes descritivos para as variáveis:  **salario** e não **s**, **horaExtra** e não **he**, **desconto** e não **d** ;
- Ao nomear métodos utilize nomes que descrevam o propósito do método : :  **GetValorSalario**() e não **GetValor**() ;
- Se for necessário comente o método descrevendo o seu propósito e seus parâmetros de forma resumida;

**5 - Não utilize métodos longos, mas, se isso for realmente necessário use o recurso Region para facilitar a leitura do método**

No código abaixo temos um método mais longo que pode se tornar difícil de ler e entender :

​    public class GetCalculoSalarioFuncionario     {        /// <summary>       /// Calcula o valor do salário líquido de um funcionário       /// </summary>       /// <param name="codigoFuncionario"></param>       /// <param name="numeroHorasExtras"></param>       /// <returns></returns>       public float GetValorSalarioLiquido(string codigoFuncionario, int numeroHorasExtras )       {        float salarioBasicoMensal = GetSalario("FUNCI100");        float valorDeducoesINSS = salarioBasicoMensal * (10 * salarioBasicoMensal / 100) ;        float valorImpostoRenda = salarioBasicoMensal * (20 * salarioBasicoMensal / 100);        float valorHorasExtras = numeroHorasExtras * (salarioBasicoMensal / 240);        float valorSalarioLiquido = salarioBasicoMensal + valorHorasExtras - valorImpostoRenda - valorDeducoesINSS;        return valorSalarioLiquido;      }        /// <summary>       /// Retorna o valor do salário mensal básico de um funcionário       /// </summary>       /// <param name="codigoFuncionario"></param>       /// <returns></returns>       public static int GetSalario(string codigoFuncionario)       {         if (codigoFuncionario == "FUNCI100")         {           return 60000;         }         else         {           return 45000;         }       }     }

Aplicando o recurso **Region** ao código podemos recolher o código para ter uma visão geral do método facilitando o entendimento do código:

![img](http://www.macoratti.net/17/05/c_codlimp11.png)

**6 - Remova namespaces desnecessários ao código**

Remover namespaces não utilizados no código limpa o código e facilita a leitura.

Para fazer basta clicar com o botão direito do mouse sobre os namespaces e a seguir clicar em : **Remove and Sort Usings**

![img](http://www.macoratti.net/17/05/c_codlimp12.png)

**7 - Use o recurso de Indentação e espaçamento para tornar o código mais fácil de ler e entender**

\1. Use **TAB** para indentação. Não use espaços. Defina o tamanho do Tab como igual 4.

\2. Comentários devem estar no mesmo nível que o código *(usa o mesmo nível de recuo).*

| ![img](http://www.macoratti.net/17/05/positivo.png)          | ![img](http://www.macoratti.net/17/05/negativo.png)          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `    //Formato de uma mensagem e exibição    string mensagemCompleta = "Olá" + nome;    DateTime dataAtual = DateTime.Now;` | //Formato de uma mensagem e exibição     string mensagemCompleta = "Olá" + nome;      DateTime dataAtual = DateTime.Now; |

Usando Code Metrics do Visual Studio 2017

O Code Metrics é uma ferramenta do Visual Studio que calcula e exibe relatórios relacionados a métricas de código. Podemos usar o recurso **Code Metrics** do VS 2017 para calcular os seguintes itens no código da nossa solução :

- **Maintainability Index** - Um valor que indica quanto o seu código é fácil de manter. Valores altos indicam que o código é mais fácil manter. O valor ideal é 100.
- **Cyclomatic Complexity** - Um valor que indica o número de caminhos diferntes que seu código pode tomar. O valor ideal é 1. *(Números de de ifs, switch/case,do, while)*
- **Depth of Inheritance** - O número de definições de classe acima desta na árvore de herança, sem incluir interfaces. O Valor ideal é 1. *(Quanto mais herança mais difícil manter)*
- **Class Coupling** - Número de outras entidades de que esta entidade depende. Valor ideal 0.

Para executar o **Code Metrics** acione o menu **Analyze -> Calculate Code Metrics -> For Solution**

![img](http://www.macoratti.net/17/05/c_codlimp13.png)

Para o nosso exemplo obtivemos os seguintes resultados:

![img](http://www.macoratti.net/17/05/c_codlimp14.png)

**Usando o StyleCop do Visual Studio 2017**

Podemos utilizar o **StyleCop** para melhorar a manutenibilidade, o estilo e a padronização do código. Se você não tem o StyleCop instalado pode fazer isso via menu **Tools -> Extension and Updates;**

Clique em **Online** e localize **StyleCop** clicando no botão para download:*( A instalação irá ocorre depois...)*

![img](http://www.macoratti.net/17/05/c_codlimp15.png)

Após instalar a ferramenta abra o projeto que deseja verificar e

![img](http://www.macoratti.net/17/05/c_codlimp16.png)

Antes de executar você pode abrir o arquivo de configurações do **StyleCop** que contém todas as regras que você deseja utilizar no seu projeto.

![img](http://www.macoratti.net/17/05/c_codlimp17.png)

Ao executar o StyleCop em seu projeto o VS irá apresentar todos os alertas referentes ao StyleCop.

![img](http://www.macoratti.net/17/05/c_codlimp18.png)

No exemplo eu destaquei dois alertas referente a classe **Program** do projeto; um indicando que a classe não tem uma documentação e outro informando que a mesma não possui um modificador de acesso.

Agora cabe a você avaliar os alertas, fazer as correções e assim melhorar o seu código.

E assim, com apenas essas 7 dicas simples e práticas seu código vai se elevar de nível tornando-se mais fácil de ler, entender e manter.