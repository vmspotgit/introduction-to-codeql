<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-3-notes.
-->

## Passo 3: Corrigir Vulnerabilidades de Segurança

_Bom trabalho concluindo o Passo 2: Revisão e Triagem de Alertas do CodeQL :sparkles:_

Neste passo, trabalharemos para corrigir as vulnerabilidades de segurança já identificadas pelo CodeQL. Lembre-se, neste ponto, introduzimos o CodeQL em nosso repositório e fizemos uma verificação no código existente. As vulnerabilidades encontradas são problemas do mundo real e precisam ser corrigidas! Vamos corrigir esse problema editando o arquivo `/server/routes.py`.

### :keyboard: Atividade 1: Revisar alertas

Primeiro, antes de corrigirmos esses alertas, precisamos garantir que os alertas ainda estão abertos. Também precisaremos reunir informações sobre quais arquivos corrigir e como melhor corrigi-los.

1. Navegue até a página de alertas de verificação de código: **Security** > **Code Scanning**.
2. Você deve ver dois alertas listados como "**Aberto (Open)**". Se algum dos alertas estiver listado como "**Fechado (closed)**", abra a página de alerta e escolha **Reabrir alerta (reopen alert)**.

Agora que ambos os alertas estão abertos, vamos corrigi-los. Se você olhar os alertas, ambos indicam um arquivo específico contendo os problemas: `server/routes.py`. O problema está na criação da consulta SQL para o banco de dados. Essas consultas são vulneráveis a ataques de injeção de SQL. Devemos reescrever essas instruções SQL de forma mais segura.

Se você expandir a seção **Mais informações (Show more)** na parte inferior do alerta, há sugestões muito claras para corrigir esta consulta. Vamos implementar essas sugestões na próxima atividade.

### :keyboard: Atividade 2: Editar routes.py

Agora sabemos onde os problemas existem e como corrigi-los. Começaremos modificando o arquivo `routes.py`. Novamente, você desejará realizar os próximos passos em uma janela ou aba separada do navegador.

1. Clique na aba **Código (Code)** em seu repositório.
2. Selecione a pasta `server`.
3. Selecione o arquivo `routes.py`.
4. Clique no botão **Editar (Edit)** à direita.

  ![edit-button.png](/images/edit-button.png)

5. Edite a linha 16, destacando a instrução SQL e substituindo-a por este texto: `"SELECT * FROM books WHERE name LIKE %s", name`.

6. Edite a linha 22 para substituir a instrução SQL por este texto: `"SELECT * FROM books WHERE author LIKE %s", author`.

7. Clique em **Commit changes...** no canto superior direito. A janela "Propor alterações" aparecerá. Deixe as configurações padrão e clique em **Commit changes** novamente.
8. O CodeQL agora iniciará uma nova verificação. Verifique o status dessa verificação navegando até **Ações (Action) ** e, em seguida, escolhendo a ação **CodeQL**. Quando o trabalho de verificação for concluído, o Actions exibirá um cheque verde ao lado da última execução.
9. Quando a verificação do CodeQL estiver concluída, navegue até **Security** > **Code Scanning** para revisar os alertas. Você deve ter zero alertas abertos e dois alertas fechados 🎉. Sinta-se à vontade para revisar os alertas fechados, especialmente a trilha de auditoria.
10. Espere cerca de 20 segundos e então atualize esta página (a página onde você está seguindo as instruções). [GitHub Actions](https://docs.github.com/en/actions) será atualizado automaticamente para o próximo passo.
