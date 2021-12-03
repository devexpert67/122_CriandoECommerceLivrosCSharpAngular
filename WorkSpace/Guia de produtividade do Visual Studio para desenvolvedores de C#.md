# Guia de produtividade do Visual Studio para desenvolvedores de C#



- [![img](https://github.com/olprod.png?size=32)](https://github.com/olprod)

Esta página é útil?

Saiba como o Visual Studio torna os desenvolvedores mais produtivos do que nunca. Aproveite nossas melhorias em desempenho e produtividade como a navegação para assemblies descompilados, sugestões de nomes de variáveis durante a digitação, um modo de exibição de hierarquia no **Gerenciador de Testes**, opção Ir para Todos (**Ctrl**+**T**) para navegar para as declarações de arquivo/tipo/membro/símbolo, um **Auxiliar de Exceção** inteligente, configuração e imposição de estilo de código e muitas correções de código e refatorações.

## Estou acostumado aos atalhos de teclado de um outro editor

Se você estiver vindo de outro IDE ou ambiente de codificação, poderá alterar o esquema do teclado para o *Visual Studio Code* ou *ReSharper (Visual Studio)*:

![Esquemas de teclado no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vs2017guide-keyboard.png?view=vs-2022)

Algumas extensões também oferecem esquemas de teclado:

- [Teclas de acesso para Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulação de Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estes são os atalhos populares do Visual Studio:

| Atalho (todos os perfis)                                     | Comando                                                    | Descrição                                                    |
| :----------------------------------------------------------- | :--------------------------------------------------------- | :----------------------------------------------------------- |
| **Ctrl** + **T**                                             | Ir para Todos                                              | Navegar diretamente para qualquer declaração de símbolo, arquivo, tipo ou membro |
| **F12** (também **Ctrl** + **clique**)                       | Ir para definição                                          | Vá até onde um símbolo estiver definido                      |
| **Ctrl** + **F12**                                           | Ir Para Implementação                                      | Navegue de um membro ou tipo base até suas várias implementações |
| **Shift** + **F12**                                          | Localizar Todas as Referências                             | Veja todas as referências de símbolo ou de literal           |
| **ALT** + **Casa**                                           | Ir Para a Base                                             | Navegue até a cadeia de herança                              |
| **Ctrl** + **.** (também **ALT** + **Inserir** no perfil C#) | Ações e Refatorações Rápidas                               | Veja quais correções de código, ações de geração de código, refatorações ou outras ações rápidas estão disponíveis na posição do cursor ou na seleção do código |
| **Ctrl** + **D**                                             | Duplicar linha                                             | Duplica a linha de código onde o cursor está posicionado (disponível no **Visual Studio 2017 versão 15.6** e posterior) |
| **Shift** + **ALT**+**+**/**-**                              | Expandir/Reduzir seleção                                   | Expande ou reduz a seleção atual no editor (disponível no **Visual Studio 2017 versão 15.5** e posteriores) |
| **Shift** + **ALT** + **.**                                  | Inserir próximo sinal de interpolação correspondente       | Adiciona uma seleção e um sinal de interpolação no próximo local que corresponde à seleção atual (disponível no **Visual Studio 2017 versão 15.8** e posterior) |
| **Ctrl** + **P**                                             | Pesquisar                                                  | Pesquise todas as configurações do Visual Studio             |
| **F5**                                                       | Iniciar Depuração                                          | Inicie a depuração do aplicativo                             |
| **Ctrl** + **F5**                                            | Executar sem Depurar                                       | Execute o aplicativo localmente sem depuração                |
| **Ctrl** + **K**,**D** (perfil padrão) ou **Ctrl** + **E**,**d** (perfil C#) | Formatar Documento                                         | Limpe as violações de formatação de um arquivo com base nas configurações de nova linha, de espaçamento e de recuo |
| **Ctrl** + **\** ,**Ctrl** + **e** (perfil padrão) ou **Ctrl** + **W**,**e** (perfil C#) | Exibir Lista de Erros                                      | Veja todos os erros no documento, no projeto ou na solução   |
| **ALT** + **PgUp/PgDn**                                      | Ir para o problema seguinte/anterior                       | Vá para o erro, aviso ou sugestão seguinte/anterior no documento (disponível no **Visual Studio 2017 versão 15.8** e posterior) |
| **Ctrl** + **K**,**/**                                       | Alternar linha de único comentário/cancelar os comentários | Esse comando adiciona ou remove um comentário de linha única, dependendo do fato de sua seleção já estar comentada |
| **Ctrl** + **Shift**+**/**                                   | Alternar bloquear comentário/cancelar os comentários       | Este comando adiciona ou remove os comentários de bloco, dependendo do que você selecionou |

 Observação

Algumas extensões desassociam as associações de teclas padrão do Visual Studio. para usar os comandos acima, restaure as associações de teclas para os padrões de Visual Studio acessando **ferramentas** > **importar e exportar Configurações** > **redefinir todas as configurações** ou **ferramentas** > **opções** > > **redefinição** de teclado.

Para saber mais sobre os comandos e atalhos de teclado, confira [Atalhos de produtividade](https://docs.microsoft.com/pt-br/visualstudio/ide/productivity-shortcuts?view=vs-2022) e [Atalhos comuns de teclado](https://docs.microsoft.com/pt-br/visualstudio/ide/default-keyboard-shortcuts-in-visual-studio?view=vs-2022).

## Navegar rapidamente para arquivos ou tipos

O Visual Studio tem um recurso chamado **Ir para Todos** (**Ctrl**+**T**). **Ir para todos** permite que você vá rapidamente para qualquer declaração de arquivo, tipo, membro ou símbolo.

- Altere a localização desta barra de pesquisa ou desative a visualização de navegação dinâmica usando o ícone de **engrenagem**.
- Filtre os resultados usando uma sintaxe, como `t mytype`.
- Defina o escopo da pesquisa somente para o documento atual.
- Há suporte para a correspondência de minúsculas concatenadas.

![Ir para todos no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vs2017guide-go-to-all.png?view=vs-2022)

## Impor regras de estilo de código

Use um arquivo EditorConfig para codificar as convenções de codificação e aplicá-las à fonte.

![Imposição de estilo de código no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vsguide_codestyle.png?view=vs-2022)

- Adicione um padrão ou. Arquivo de EditorConfig de estilo net para seu projeto escolhendo **Adicionar** > **novo item**. Na caixa de diálogo **Adicionar Novo Item**, pesquise por "editorconfig". Selecione qualquer um dos modelos de item de **Arquivo editorconfig** e escolha **Adicionar**.

  ![Modelos de item do EditorConfig no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/editorconfig-item-templates.png?view=vs-2022)

- Crie automaticamente um arquivo *. editorconfig* com base em suas configurações de estilo de código em **ferramentas** > **Opções** > **Editor de texto** > estilo de > **código** C#.

  ![Gerar o arquivo .editorconfig a partir das configurações no VS 2019](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vs-2019/generate-editorconfig-file.png?view=vs-2022)

- O [recurso de inferência de código](https://docs.microsoft.com/pt-br/visualstudio/intellicode/code-style-inference) do IntelliCode para Visual Studio infere seus estilos de código com base no código existente. Ele cria um arquivo EditorConfig não vazio com suas preferências de estilo de código já definidas.

- Configure o nível de severidade de uma regra de estilo de código diretamente por meio do editor. Se, no momento, você não tiver um arquivo. editorconfig, será gerado um para você. Coloque o cursor sobre o erro, aviso ou sugestão e digite **Ctrl** + **.** para abrir o menu Ações Rápidas e Refatorações. Selecione **Configurar ou suprimir problemas**. Em seguida, selecione a regra e escolha o nível de gravidade que deseja configurar para essa regra. Isso atualizará o EditorConfig existente com a nova gravidade da regra.

  ![Configurar o nível de severidade de uma regra de estilo de código diretamente no editor](https://docs.microsoft.com/pt-br/visualstudio/ide/media/configure-severity-level.png?view=vs-2022)

Confira a documentação de [opções de convenção de codificação .NET](https://docs.microsoft.com/pt-br/dotnet/fundamentals/code-analysis/code-style-rule-options) que também contém um exemplo de um arquivo EditorConfig completo.

## Limpeza de código

O Visual Studio oferece a formatação sob demanda de seu arquivo de código, incluindo preferências de estilo de código com o recurso de **Limpeza de Código**. Para executar a Limpeza de Código, clique no ícone de vassoura na parte inferior do editor ou pressione **Ctrl** + **K,** **Ctrl** + **E**.

![Botão de Limpeza de código no Visual Studio 2019](https://docs.microsoft.com/pt-br/visualstudio/ide/media/execute-code-cleanup.png?view=vs-2022)

Você também pode fazer a limpeza de código em todo o projeto ou em toda a solução. Clique com o botão direito do mouse no nome do projeto ou da solução no **Gerenciador de Soluções**, selecione **Análise e Limpeza de Código** e selecione **Executar Limpeza de Código**.

![Fazer Limpeza de Código Em Todo Projeto ou Em Toda Solução](https://docs.microsoft.com/pt-br/visualstudio/ide/media/run-code-cleanup-project-solution.png?view=vs-2022)

Além de formatar seu arquivo em relação a espaços, recuos etc, a **Limpeza de Código** também se aplica aos estilos de código selecionados. Suas preferências para cada estilo de código são lidas no [arquivo EditorConfig](https://docs.microsoft.com/pt-br/visualstudio/ide/code-styles-and-code-cleanup?view=vs-2022#code-styles-in-editorconfig-files), caso tenha um para o projeto ou das [configurações de estilo de código](https://docs.microsoft.com/pt-br/visualstudio/ide/code-styles-and-code-cleanup?view=vs-2022#code-styles-in-the-options-dialog-box) na caixa de diálogo **Opções**.

## Refatorações e correções de código

O Visual Studio vem com muitas refatorações, ações de geração de códigos e correções de códigos. As linhas onduladas vermelhas representam erros, as linhas onduladas verdes representam avisos e os três pontos cinzas representam sugestões de código. Você pode acessar correções de código clicando na lâmpada ou no ícone de chave de fenda ou pressionando **Ctrl** + **.** ou **Alt** + **Insira**. Cada correção vem com uma janela de visualização que mostra a diferença do código em tempo real de como a correção funciona.

As correções rápidas e refatorações comuns incluem:

- Renomear
- Extrair Método
- Alterar Assinatura do Método
- Gerar Construtor
- Gerar Método
- Mover Tipo para Arquivo
- Adicionar Null-Check
- Adicionar parâmetro
- Remover usos desnecessários
- Loop Foreach para uma consulta LINQ ou um método LINQ
- Subir os membros

Para obter mais informações, consulte [recursos de geração de código](https://docs.microsoft.com/pt-br/visualstudio/ide/code-generation-in-visual-studio?view=vs-2022).

Você pode [instalar analisadores FxCop](https://docs.microsoft.com/pt-br/visualstudio/code-quality/install-net-analyzers?view=vs-2022) para sinalizar problemas de códigos. Ou escrever sua própria refatoração ou correção de código com [analisadores Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md).

Vários membros da comunidade escreveram extensões gratuitas que adicionam outras inspeções de código:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint para Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Refatorações no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vsguide_codeanalysis.png?view=vs-2022)

## Localizar Usos, Ir Para Implementação e Navegar para Assemblies Descompiladas

O Visual Studio tem muitos recursos para ajudar você a pesquisar e [navegar em seu código](https://docs.microsoft.com/pt-br/visualstudio/ide/navigating-code?view=vs-2022).

| Recurso                                 | Atalho                                 | Detalhes/melhorias                                           |
| :-------------------------------------- | :------------------------------------- | :----------------------------------------------------------- |
| Localizar Todas as Referências          | **Shift** + **F12**                    | Os resultados são coloridos e podem ser agrupados por projeto, definição e tipo de referência, como leitura ou escrita. Também é possível "bloquear" resultados. |
| Ir Para Implementação                   | **Ctrl** + **F12**                     | É possível usar “Ir para definição” na palavra-chave `override` para navegar até o membro substituído |
| Ir para definição                       | **F12** ou **Ctrl** + **Clique**       | Pressione **Ctrl** enquanto clica para navegar até a definição |
| Inspecionar Definição                   | **Alt** + **F12**                      | Exibição embutida de uma definição                           |
| Visualizador de Estrutura               | Linhas cinzas pontilhadas entre chaves | Passe o mouse para ver a estrutura do código                 |
| Navegação para assemblies descompilados | **F12** ou **Ctrl** + **Clique**       | Navegue até fonte externa (descompilada com ILSpy) habilitando o **recurso:** Ferramentas Opções Editor de Texto C# Habilita a navegação avançada para fontes > > > > > **descompiladas.** |

![Ir para Todos e Localizar Todas as Referências](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vside_productivity_navigation.png?view=vs-2022)

## IntelliSense aprimorado

Use o IntelliCode para Visual Studio para obter [conclusões de código de reconhecimento de contexto](https://docs.microsoft.com/pt-br/visualstudio/intellicode/intellicode-visual-studio) em vez de apenas uma lista em ordem alfabética. É possível também treinar um [modelo personalizado do IntelliSense](https://docs.microsoft.com/pt-br/visualstudio/intellicode/custom-model-faq) com base em suas próprias bibliotecas específicas de domínio.

## Teste de unidade

A partir do Visual Studio 2017, há vários aprimoramentos na experiência de teste. Você pode realizar testes com as estruturas de teste MSTest v1, MSTest v2, NUnit ou XUnit.

- A detecção de testes do **Gerenciador de Testes** é rápida.

- Organize seus testes no **Gerenciador de Testes** com a *classificação hierárquica*.

  ![Exibição de hierarquia do Gerenciador de Testes no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vsguide_testing.png?view=vs-2022)

- [O live unit testing](https://docs.microsoft.com/pt-br/visualstudio/test/live-unit-testing?view=vs-2022) executa continuamente testes afetados pelas alterações de código e atualiza os ícones do editor em linha para que você saiba o status dos testes. Inclua ou exclua testes específicos ou projetos de teste pelo Live Test Set (conjunto de teste de modo real). (somente na edição Visual Studio Enterprise.)

## Depuração

Alguns dos recursos de depuração do Visual Studio incluem:

- A capacidade de pesquisar uma cadeia de caracteres dentro das janelas **Inspeção**, **Autos** e **Locais**.
- *Clique para executar*, que permite focalizar uma linha de código, pressionar o ícone verde 'executar' que é exibido e executar o programa até atingir essa linha.
- O **Auxiliar de Exceção**, que coloca as informações mais importantes no nível superior na caixa de diálogo, por exemplo, qual variável `null` está em uma `NullReferenceException`.
- [Depuração para retroceder novamente](https://docs.microsoft.com/pt-br/visualstudio/debugger/view-historical-application-state?view=vs-2022), que permite voltar a pontos de interrupção ou etapas anteriores e exibir o estado do aplicativo no passado.
- [Depuração de instantâneo](https://docs.microsoft.com/pt-br/azure/application-insights/app-insights-snapshot-debugger), que permite investigar o estado de um aplicativo Web online no momento em que uma exceção foi lançada (é necessário estar no Azure).

![Auxiliar de Exceção no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vsguide_debugging.png?view=vs-2022)

## Controle de versão

Você pode usar o Git ou o TFVC para armazenar e atualizar seu código no Visual Studio.

- Instalar as [solicitações de pull para o Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) para criar, examinar, fazer check-out e executar solicitações de pull sem sair do Visual Studio.

- Organize as alterações locais no [Team Explorer](https://docs.microsoft.com/pt-br/visualstudio/ide/reference/team-explorer-reference?view=vs-2022) e use a barra de status para acompanhar confirmações e alterações pendentes.
- Configure a integração e a entrega contínuas de seus projetos de ASP.NET dentro do Visual Studio com a extensão [Ferramentas de entrega contínua do Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Controle do código-fonte no Visual Studio](https://docs.microsoft.com/pt-br/visualstudio/ide/media/vside_productivity_sourcecontrol.png?view=vs-2022)

## Que outros recursos eu devo conhecer?

Aqui está uma lista dos recursos do editor e de produtividade para escrever códigos com mais eficiência. Pode ser necessário ativar alguns recursos, pois eles ficam desativados por padrão (eles podem indexar itens em seu computador, são controversos ou atualmente são experimentais).

| Recurso                                                      | Detalhes                                                     | Como habilitar                                               |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| Arquivo local no Gerenciador de Soluções                     | Realça o arquivo ativo no **Gerenciador de Soluções**        | **Ferramentas** > do **Opções** > **Projetos e soluções** > **Acompanhar item ativo no Gerenciador de soluções** |
| Adicionar usos para tipos em assemblies de referência e pacotes do NuGet | Mostra uma lâmpada de erro com uma correção de código para instalar um pacote do NuGet para um tipo não referenciado | **Ferramentas** > do **Opções** > **Editor** > de texto **C#** > **Avançado** > **sugira o uso de tipos em assemblies de referência** e **sugira o uso de tipos em pacotes de NuGet** |
| Habilitar análise de solução completa                        | Ver todos os erros na solução na **Lista de Erros**          | **Ferramentas** > do **Opções** > **Editor** > de texto **C#** > **Avançado** > **Habilitar análise de solução completa** |
| Habilitar a navegação para origens descompiladas             | Habilite Ir Para a Definição em tipos/membros de fontes externas e usar o descompilador ILSpy para mostrar os corpos de método | **Ferramentas** > do **Opções** > **Editor** > de texto **C#** > **Avançado** > **Habilitar a navegação para fontes descompiladas** |
| Modo de conclusão/sugestão                                   | Altera o comportamento de conclusão no IntelliSense. Os desenvolvedores com experiência em IntelliJ tendem a usar uma configuração diferente da configuração padrão aqui. | **Menu** > **Editar** > **IntelliSense** > **Alternar modo de conclusão** |
| [CodeLens](https://docs.microsoft.com/pt-br/visualstudio/ide/find-code-changes-and-other-history-with-codelens?view=vs-2022) | Exibe informações de referência de código e o histórico de alterações no editor. (Os indicadores do CodeLens de controle do código-fonte não estão disponíveis na edição do Visual Studio Community.) | **Ferramentas** > do **Opções** > **Editor** > de texto **Todos os idiomas** > **CodeLens** |
| [Snippets de código](https://docs.microsoft.com/pt-br/visualstudio/ide/visual-csharp-code-snippets?view=vs-2022) | Ajudar a apagar um código clichê comum                       | Digite um nome de snippet e pressione **Tab** duas vezes.    |