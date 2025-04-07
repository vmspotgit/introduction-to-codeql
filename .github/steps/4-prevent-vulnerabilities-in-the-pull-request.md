<!--
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-4-notes.
-->

## Passo 4: Prevenir Vulnerabilidades no Pull Request

_Muito bem! Você concluiu o Passo 3: Corrigir Vulnerabilidades de Segurança! :partying_face:_

Parabéns! Você chegou até aqui. Estamos quase terminando! O último passo é testar a integração do pull request com o CodeQL. Neste passo, adicionaremos uma vulnerabilidade de volta ao arquivo `routes.py` para acionar um alerta de vulnerabilidade de injeção de SQL. Esta será a mesma questão que vimos inicialmente.

Nosso objetivo é entender o que os desenvolvedores experimentam quando encontram uma nova vulnerabilidade.

Neste passo, iremos:
- editar o arquivo `routes.py`.
- alterar a instrução SQL para torná-la insegura.
- cometer essas alterações e mesclar o código inseguro na branch principal.
- experimentar o alerta dentro do pull request.

Vamos começar 👍

**O que é um pull request**: Pull requests são mudanças propostas para um repositório submetidas por um usuário e aceitas ou rejeitadas pelos colaboradores do repositório. Isso permite que várias pessoas trabalhem no mesmo código ao mesmo tempo. Para mais informações, confira o curso de habilidades do GitHub "[Introdução ao GitHub](https://github.com/skills/introduction-to-github)" ou "[Sobre pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)" na documentação do GitHub.

**O que é uma branch**: Uma branch é uma versão paralela do seu repositório. Por padrão, seu repositório tem uma branch chamada main e é considerada a branch definitiva. Criar branches adicionais permite que você copie a branch principal do seu repositório e faça alterações com segurança sem interromper o projeto principal. Para mais informações, veja "[Sobre branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#)" na documentação do GitHub.

### :keyboard: Atividade 1: Editar `routes.py` e criar um novo pull request

Nesta primeira atividade, introduziremos a mesma instrução SQL insegura de antes no arquivo `routes.py`. Uma vez que atualizarmos o arquivo, faremos o commit em uma nova branch e, em seguida, criaremos um pull request.

  1. Clique na aba **Code** no seu repositório.
  2. Selecione a pasta `server`.
  3. Selecione o arquivo `routes.py`.
  4. Clique no botão **Edit** à direita.

![edit-button.png](/images/edit-button.png)

  5. Edite a linha 16 destacando a instrução SQL e substituindo-a por este texto: `"SELECT * FROM books WHERE name LIKE '%" + name + "%'"`.
  6. Clique em **Commit changes...** no canto superior direito. A janela "Propose changes" aparecerá.
  7. Desta vez, selecione o botão de rádio ao lado de **Create a new branch**. Você pode criar um novo nome para esta branch ou deixá-la com a sugestão padrão.
  8. Clique em **Propose changes**. Isso abrirá um novo pull request.
  9. Na janela "Open a pull request", clique em **Create Pull Request**.

### :keyboard: Atividade 2: Revisar pull request

Neste ponto, editamos o arquivo `routes.py` para adicionar nosso código vulnerável, fizemos o commit dessas alterações em nossa nova branch e criamos um pull request para mesclar a nova branch na nossa branch `main`. Estes são os mesmos passos que um desenvolvedor tomaria para introduzir novo código vulnerável em um repositório.

Agora, vamos dar uma olhada no pull request para ver como é a experiência.

1. Na atividade anterior, criamos o pull request. Depois de criar o pull request, você foi levado diretamente para a página do pull request. Na parte inferior do pull request, você verá uma verificação chamada "Code scanning/CodeQL". Este é o trabalho de análise do CodeQL verificando o código introduzido no pull request.

![pr-panel](/images/pr-panel.png)

2. Uma vez que a verificação for concluída, você verá um novo comentário no pull request do CodeQL indicando uma nova vulnerabilidade de segurança; uma consulta SQL construída a partir de dados controlados pelo usuário. Esta é a nossa vulnerabilidade de injeção de SQL.

  <img width="1180" alt="image" src="https://github.com/leftrightleft/enable-code-scanning/assets/4910518/378bd766-ef61-4619-ab3c-bf2c8d9618d7">

3. Revise os caminhos de fluxo de dados clicando em **Show Paths**.

4. Se desejar, adicione um comentário e marque um de seus amigos usando o handle do GitHub deles (exemplo: `@username`). Isso notificará que você fez um comentário sobre o problema e precisa da ajuda deles para resolver o problema. 😄

Se esta fosse uma situação do mundo real, o desenvolvedor corrigiria a instrução SQL em sua branch. Uma vez corrigido, a vulnerabilidade será automaticamente fechada.

Se você quiser saber mais sobre as integrações de pull request para verificação de código, veja "[Triaging code scanning alerts in pull requests](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/triaging-code-scanning-alerts-in-pull-requests)."

Espere cerca de 20 segundos e então atualize esta página (a página onde você está seguindo as instruções). [GitHub Actions](https://docs.github.com/en/actions) será atualizado automaticamente para o próximo passo.
