**C# - Dicas para aumentar melhorar seu código e sua produtividade**

------

Hoje temos 10 dicas práticas para aumentar sua produtividade e tornar o seu código mais legível e enxuto.

![img](http://www.macoratti.net/12/01/c_10dap1.jpg)

**1- O operador de avaliação condicional - ?:**

O operador condicional **(:?)** avalia uma expressão booleana e retorna um dentre dois valores.

O formato do operador **(:?)** é o seguinte:

```
 **condição ? primeira_expressão : segunda_expressão**
```

Se a condição for verdadeira, a primeira expressão é avaliada e se torna o resultado, se falsa, a segunda expressão é avaliada e se torna o resultado. Apenas uma das duas expressões é sempre avaliada.

Abaixo temos um exemplo mostra como podemos usar o operador para reduzir a quantidade de código escrita:

| static void Main(string[] args)     {       int x = 10;       int y = 20;       int maximo;        **if (x > y)         maximo = x;       else         maximo = y;**        Console.WriteLine(" Máximo = " + maximo);       Console.ReadKey();     } | static void Main(string[] args)     {       int x = 10;       int y = 20;       int maximo;        **maximo = (x > y) ? x : y;**        Console.WriteLine(" Máximo = " + maximo);       Console.ReadKey();     } |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

A seguir um exemplo que verifica se uma variável é null : Ex: **Valor == null ? ValorSeForNull : ValorSeNaoForNulll;**

**2- O operador ??**

**Sintaxe: variável ?? valor padrão**

O operador **??** retorna o operando à esquerda da expressão se o valor não for nulo; se o valor for nulo ele retorna o operando à direita da expressão.

| object a = null; object d = new object(); object e;   if (a != null)   e = a; else   e = d; | object a = null; object d = new object(); object e;   **object e = c ?? d;** |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

Abaixo temos um exemplo mais prático:

string mensagem = null; Console.WriteLine(mensagem ?? "Macoratti.net");

Como mensagem possui um valor null será exibida a mensagem **"Macoratti.net"** definida após o operador **??**.

Vamos agora combinar a utilização dos dois operadores:

string conceito = null ; int nota = 5; string resultado = "";  resultado = nota >= 5 ? conceito ?? " Aprovado " : " Reprovado "; Console.WriteLine(resultado);

O que será exibido ???

O operador ? irá verificar se a expressão nota >= 5 é verdadeira, neste caso, a primeira expressão será avaliada:

conceito ?? " Reprovado "

Nesta expressão temos o operador **??** e como o valor da variável conceito é **null** então será exibida a string **" Aprovado "**;

![img](http://www.macoratti.net/12/01/c_10dap2.gif)

**3- Inicializadores de objetos**

Depois de criar um novo objeto muitas vezes você tem que atribuir as suas propriedades. A partir da versão 3.0 da plataforma .NET a linguagem C# torna possível usar os inicializadores de objeto para melhorar a legibilidade e gerar menos código.

Vejamos como utilizar este recurso:

| ` **Cliente mac = new Cliente(); mac.Nome = "Macoratti"; mac.Endereco = "Rua Projetada 100"; Console.WriteLine(mac.Nome + " - " + mac.Endereco);**` | `**Cliente mac = new Cliente { Nome="Macoratti", Endereco = "Rua Projetada , 100" }; Console.WriteLine(mac.Nome + " - " + mac.Endereco);** ` |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Código Padrão                                                | Usando inicializadores de objetos                            |

**4- A instrução Using**

Muitas vezes você terá de alocar um recurso do sistema, como uma fonte, um identificador de arquivo, um recurso de rede, um banco de dados,etc.

Cada vez que você precisar desse recurso há três etapas fundamentais para percorrer:
**1- Você adquire o recurso;
2- Você usa o recurso;
3- Você libera o recurso;**

Se você não liberar o recurso usado de forma correta, você estará ocupando memória desnecessariamente e dependendo do cenário poderá ter problemas com vazamento de memória.

Um exemplo que mostra bem o uso da instrução **Using** é a utilização de um banco de dados relacional como o SQL Server. Veja o exemplo a seguir:

| `SqlConnection connection = new SqlConnection(connectionString); SqlCommand command = connection.CreateCommand(); command.CommandText = "mac_GetValue"; command.CommandType = CommandType.StoredProcedure; object ret = null; try {    connection.Open();    ret = command.ExecuteScalar(); } finally {   //verifica se a conexão esta em uso para liberar    if (connection != null)        connection.Close(); }` | using (SqlConnection connection = new SqlConnection(connectionString)) { SqlCommand command = connection.CreateCommand();  command.CommandText = "mysp_GetValue"; command.CommandType = CommandType.StoredProcedure;  connection.Open(); object ret = command.ExecuteScalar(); } // libera os recursos |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Código padrão                                                | Usando a instrução Using                                     |

No trecho de código com a **instrução Using** a conexão será fechada quando o objeto sai do escopo. Esse processo é feito da maneira orientada a objeto - através da implementação de uma interface. A interface **IDisposable**.

Isto implica que apenas os objetos que implementam **IDisposable** podem ser usado em uma instrução **using**. Também é importante notar que chamar **Dispose** explicitamente *(ou implicitamente através de uma declaração using)* trás benefícios em termos de desempenho.

**5- Usando aliases para tipos e namespaces extensos**

Os nomes de identificadores C# podem ficar muito extensos, e, isso dificulta a digitação e aumenta a chance de erros.

Ao usar uma diretiva alias você introduz um identificador que serve como um alias para um *Namespace* ou tipo dentro da unidade de compilação imediatamente envolvente ou corpo do namespace. Vejamos alguns exemplos:

Se você estiver fazendo a *automação do Microsoft Office* você pode querer fazer algo simples como abrir o MS Word e alterar um documento. Você pode usar a instrução **"using"** para criar um alias para uma classe ou um namespace conforme o exemplo abaixo:

** ****using Outlook = Microsoft.Office.Interop.Outlook; using Word = Microsoft.Office.Interop.Word;****Word****.Application = new Word.Application() { Visible = True; } **

A sintaxe da diretiva usando um pseudônimo exige a utilização da palavra-chave **using** e o do sinal igual ( **=** ). No exemplo a seguir vamos mapear o tipo **'Texto'** para o tipo **System.Text.StringBuilder:**

using System; **using Texto = System.Text.StringBuilder;**class Program {   static void Main()   {     **Texto palavra = new Texto();**     palavra.Append("sparky");     palavra.Append(100);    Console.WriteLine(palavra);   } }

*Obs: Este recurso deve ser usado com atenção e cuidado para não tornar o código confuso e difícil de entender.*

**6- Nullabe Types ou Tipos Anuláveis**

Existem situações, especialmente quando se trabalha com bases de dados, onde você quer indicar que uma variável não detém atualmente um valor válido. Para tipos de referência, você pode fazer isso com facilidade definindo a variável para **null**.

Os **nullabe Types ou Tipos Anuláveis** permitem que você crie um tipo por valor que pode ser marcado como válido ou inválido de forma que você tenha certeza que a variável seja válida antes de ser usada.Tipos de valores regulares são chamados de tipos não anuláveis.

***Obs: Tipos anulável são instâncias da struct System.Nullable*** .

Um tipo anulável é sempre baseado em outro tipo, chamado tipo subjacente, que já foi declarado e sobre os quais temos que:

- Você pode criar um tipo anulável a partir de qualquer tipo de valor, incluindo o pré-definido, tipos simples;
- Você não pode criar um tipo anulável a partir de um tipo de referência ou de outro tipo anulável;
- Você não declara explicitamente um tipo anulável em seu código. Em vez disso, você declara uma variável de um tipo anulável. O compilador cria implicitamente o tipo anulável para você;

Por exemplo, o código a seguir declara uma variável do tipo **int** anulável. Observe que o sufixo é anexado ao nome do tipo, não ao nome da variável.

**int? meuInteiro = 28;**

Com essa instrução de declaração, o compilador cuida de ambas produzindo o tipo anulável e criando uma variável desse tipo.

Veja a seguir mais exemplos de tipos anuláveis:

**int? i = 10;
double? d1 = 3.14;
bool? flag = null;
char? letter = 'a';
int?[] arr = new int?[10];**

**Obs :Os tipos Anuláveis também podem ser declarados da seguinte forma:** **System.Nullable<T> variável** **Exemplo:**System.Nullable<int> x = 9;

***Atenção !!! Usar um tipo anulável é como usar uma variável de qualquer outro tipo.\***

**7- Propriedades Automáticas**

A partira da versão 3.0 a linguagem C# introduziu as **propriedades automáticas**. Uma propriedade é constituída basicamente de variável privada, que é exposta ao mundo exterior através de **getters e setters**. O exemplo a seguir mostra isso:

  public class Pessoa   {     private string _nome;     public string Nome     {       get { return _nome; }       set { _nome = value; }        }     private string _email;     public string Email     {       get { return _email; }       set { _email = value; }        }   }

Usando as propriedades automáticas podemos reduzir o código acima para:

  public class Pessoa   {     public string Nome { get; set; }     public string Email { get; set; }   }

O compilador C # gera automaticamente uma variável de apoio e as propriedades corretas get e set.

E daí ??

E daí que definindo a variável como uma propriedade vai permitir a você adicionar a lógica de validação para sua classe, numa fase posterior. Como assinatura na memória da classe não vai mudar o que significa que quaisquer bibliotecas externas compiladas com o seu código não terão que ser recompiladas.

**8- Inferência de tipos**

Na linguagem C# temos sempre o cuidado de definir nossas definições de variáveis. Ex: **string _meuSite = “www.macoratti.net”;**

Analisando a declaração parece óbvio que o tipo da variável só pode ser uma string.

De forma clara e sem rodeios, a inferência de tipos (*local variable type inferencing*) significa dizer que o compilador é capaz de *'adivinhar'* o tipo de dados de uma variável. É o sonho de todo o programador : *não precisar se preocupar mais em declarar variáveis...* mas como é que isso funciona ??

Para explicar esse recurso vou usar um trecho de código do **LINQ**, veja:

**var numeros = new int[] { 218, 7, 1, 14, 6, 3, 15, 8, 74, 81, 94 }; var numerosImpares = from p in numeros where (p % 2) != 0 select p;  foreach (var valor in numerosImpares) { Console.WriteLine(val + " "); } Console.ReadKey(); **

No IDE do Editor do **Visual C# 2010 Express Edition** podemos identificar as variáveis usadas no código acima. Assim temos que:

1- A primeira variável var do código acima pode ser identifica como sendo do tipo **int32[]**;
2- A segunda variável var do código acima pode ser identifica como sendo do tipo **IEnumerable<out T>**;
2- A variável números usada na sintaxe LINQ é do tipo **int[]**;
3- A variável valor usada no laço **For/Each** é do tipo **int32**;

Agora uma pergunta sutil.

Onde declaramos estas variáveis ?

Em lugar nenhum.

Mas então como é que o danado do compilador consegue *'adivinhar'* o tipo das variáveis ?

Nas versões anteriores do Visual Basic poderíamos até declarar um valor a uma variável sem definir o tipo mas a variável seria considerada do tipo **Object**. Assim, no código abaixo, as variáveis **a e b** seriam identificadas como do tipo **Object**:

**Dim a = 100
Dim b = DateTime.Now()**

**9. Lambda Expressions**

A versão 2.0 da linguagem C# introduziu os métodos anônimos, que são métodos definidos dentro de um método.

Este recurso embora poderoso sendo uma boa maneira de colocar todos os tipos de avaliação lógica dentro do seu código que tinha a desvantagem de não serem muito legíveis. Ex: **Func filtro = delegate(int a) { return a > 35; };**

As expressões lambdas tornam o código mais fácil de ler mantendo a mesma funcionalidade. Para o exemplo acima temos:

As expressões lambda foram incluídas na plataforma .NET para dar suporte a consultas LINQ onde as cláusulas **Where** são assim compiladas como *expressões lambdas.* Elas podem ser consideradas uma forma de delegate que pode passar ou retornar outra função.

**Nota: Delegates permitem que uma classe use métodos de outra classe. Para saber mais sobre delegates leia o meu artigo:** [**Usando Delegates**](http://www.macoratti.net/vbn_dlg.htm)

Assim, as expressões lambdas são funções ou rotinas, sem nome, que calculam e retornam um valor único; elas podem ser usadas em qualquer lugar que um tipo **delegate** for válido.

A seguir veremos alguns cenários, a utilização das *expressões lambdas* , a abordagem tradicional e o resultado:

| **Cenário**                                                  | **Usando Expressões lambdas**                                | **Usando a abordagem tradicional**                           | **Resultado**            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------ |
| **Ordenação Ascendente**                                     | For Each item In **Numeros.OrderByDescending(Function(i) i)**    Console.WriteLine(item) Next | Numeros.Sort(Function(x As Integer, y As Integer) y.CompareTo(x)) | **1,2,3,4,5,6,7,8,9,10** |
| **Verificar um condição \*(verifica os números da  lista são menores que 11)\*** | Dim resultado As Boolean = **Numeros.All(Function(i) i < 11)** | Dim resultado As Boolean = True For Each i As Integer In Numeros   If i >= 100 Then      resultado = False   End If Next | **True**                 |
| **Verificar um condição \*(verifica um número da lista é igual a 5 )\*** | Dim resultado As Boolean = **Numeros.Any(Function(i) i = 5)** | Dim resultado As Boolean = True For Each i As Integer In Numeros   If i = 5 Then      resultado = True   End If Next | **True**                 |
| **Obter os 4 números do topo da Lista **                     | Dim subconjunto = **Numeros.Take(4)**  For Each item In subconjunto    Console.WriteLine(item) Next | Dim subconjunto = New List(Of Integer)() For i As Integer = 0 To 4   If i < Numeros.Count Then     subconjunto.Add(i)    End If Next | **1,9,7,4**              |
| **Fazer a ordenação ascendente, pegar os números menor que 8 e pegar os 5 números da lista ** | Dim resultado = **_ Numeros.OrderByDescending(Function(i) i).Where(Function(i) i < 8).Take(5)**For Each item In resultado   Console.WriteLine(item) Next | Numeros.Sort(Function(x As Integer, y As Integer) y.CompareTo(x))  Dim resultado As New List(Of Integer)() For Each i As Integer In Numeros  If i < 8 Then    If resultado.Count < 5 Then       resultado.Add(i)     End If   End If Next | **7,6,5,4,3**            |
| **Localizando itens**                                        | Dim numero As String = **Numeros.Find(Function(p) p = 6)**   | For Each i As Integer In Numeros  If i = 6 Then       console.Writeline(i)   End If Next | 6                        |

**10. Usando string.IsNullOrEmpty**

Este recurso é um biblioteca de função de grande utilidade.

Quantas vezes você precisa testar se uma string está vazia ? Ou nula ?

O método string.**IsNullOrEmpty** retorna true se este for o caso.

O método **String.IsNullOrEmpty** indica se a **String** especificada é uma referência nula *(Nothing no Visual Basic)* ou uma string **Empty** *(vazia*).

| static void Main(string[] args)     {       string s1 = "abcd";       string s2 = "";       string s3 = null;        Console.WriteLine("String s1 {0}.", Teste(s1));       Console.WriteLine("String s2 {0}.", Teste(s2));       Console.WriteLine("String s3 {0}.", Teste(s3));       Console.ReadKey();     }       public static String Teste(string s)      {       if (String.IsNullOrEmpty(s))         return "é null ou empty";       else         return String.Format("(\"{0}\") é not null ou empty", s);      } | ![img](http://www.macoratti.net/12/01/c_10dap3.gif) |
| ------------------------------------------------------------ | --------------------------------------------------- |
|                                                              |                                                     |

*Uma última dica: Bom senso e boas práticas sempre resultam em um bom trabalho.*