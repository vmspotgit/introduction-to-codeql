## Passo 1: Habilitar o CodeQL

_Bem-vindo ao "Habilitar a verificação de código"! :wave:_

Neste primeiro passo, aprenderemos mais sobre o CodeQL e como usá-lo para proteger seu código-fonte.

**O que é a verificação de código do GitHub**: _[Verificação de código](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)_ é uma capacidade que permite que as equipes de desenvolvimento integrem ferramentas de teste de segurança no processo de desenvolvimento de software. Isso é feito usando GitHub Actions. Com a verificação de código, você pode integrar muitos tipos diferentes de ferramentas, incluindo SAST, segurança de contêiner e segurança de infraestrutura como código.

**O que é o CodeQL**: _[CodeQL](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql)_ é uma ferramenta de teste de análise estática que ajuda a identificar fraquezas de segurança, como injeção de SQL, cross-site scripting e problemas de injeção de código.

### :keyboard: Atividade: Habilitar a verificação de código com o CodeQL

Primeiro, habilitaremos a verificação de código com o CodeQL em nosso repositório.

1. Abra uma nova aba do navegador e siga os passos na segunda aba enquanto lê as instruções nesta aba.
2. Navegue até a aba **Settings** no topo do seu repositório recém-criado.
3. Na seção **Security** à esquerda, selecione **Advanced Security**.
4. Role para baixo até a seção intitulada **CodeQL Analysis**. Para o propósito deste curso, focaremos na análise do CodeQL.
5. Clique no menu **Set up** e escolha **Default**.
![enable-code-scanning-default.png](/images/enable-code-scanning-default.png)

Vamos dar uma olhada nas opções de configuração no modal:

  - **Languages**: Essas são as linguagens que serão verificadas pelo CodeQL. Neste caso, verificaremos em `Python`.
  - **Query suites**: As consultas do CodeQL [queries](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql#about-codeql-queries) são agrupadas em pacotes chamados "suites". Esta seção permite que você escolha qual conjunto de consultas usar. Deixaremos configurado como **Default** para este exercício. Para mais informações, veja "[Sobre as consultas do CodeQL](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql#about-codeql-queries)."
  - **Scan Events**: Esta seção informa ao CodeQL quando verificar. Neste caso, está configurado para verificar qualquer pull request para a branch `main`.

![codeql-default-configuration-box.png](/images/codeql-default-configuration-box.png)

6. Clique em **Enable CodeQL**

Espere cerca de 20 segundos e então atualize esta página (a página onde você está seguindo as instruções). [GitHub Actions](https://docs.github.com/en/actions) será atualizado automaticamente para o próximo passo.
