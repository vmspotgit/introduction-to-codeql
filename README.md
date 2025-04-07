<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses the MIT license.
-->

# Habilite o CodeQL para proteger seu código-fonte

_Garantir a segurança do código-fonte da aplicação é uma etapa crítica no desenvolvimento de software moderno. Neste curso do GitHub, você aprenderá a usar a varredura de código para identificar, resolver e prevenir padrões de codificação inseguros._

</header>

<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-2-notes.
-->

## Passo 2: Revisar e Tratar Alertas do CodeQL

_Parabéns! Você fez o CodeQL funcionar! :tada:_

Neste exercício, revisaremos os resultados da verificação do CodeQL, trataremos um alerta e criaremos um problema no GitHub para acompanhar um alerta.

**O que é o GitHub Actions**: O GitHub Actions é a plataforma de automação e CI/CD dentro do GitHub. Usamos o GitHub Actions para orquestrar e executar verificações de segurança com a verificação de código. O GitHub Actions é uma plataforma de integração contínua e entrega contínua (CI/CD) que permite automatizar seu pipeline de construção, teste e implantação. Para mais informações sobre o GitHub Actions, veja "[Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)."

**O que é CWE**: Common Weakness Enumeration (CWE) é um sistema de categorização para fraquezas e vulnerabilidades de hardware e software. Pense nisso como uma forma de descrever e categorizar problemas de segurança no código-fonte de uma aplicação. Para mais informações sobre CWEs, veja o artigo da Wikipedia "[Common Weakness Enumeration](https://en.wikipedia.org/wiki/Common_Weakness_Enumeration)."

### :keyboard: Atividade 1: Visualizar o status de uma verificação do CodeQL

Nesta atividade, exploraremos o GitHub Actions para visualizar o status de uma verificação do CodeQL.
1. No seu novo repositório, vá para a página de Ações selecionando **Actions** na barra de navegação superior. Se a execução da ação do CodeQL ainda estiver em andamento, você verá um spinner amarelo indicando que a verificação ainda está em progresso. Isso geralmente leva cerca de 4 minutos para ser concluído.
2. Selecione a execução clicando em **CodeQL Setup**.

![codeql-setup](/images/codeql-setup.png)

Observe que mais informações estão disponíveis dentro da execução das Ações. Sinta-se à vontade para explorar esta seção para visualizar informações como os logs do CodeQL, duração, status e artefatos gerados pelo CodeQL.

Uma vez que a verificação esteja completa, um cheque verde aparecerá ao lado da execução.

### :keyboard: Atividade 2: Visualizar todos os Alertas do CodeQL

Nesta atividade, visualizaremos as descobertas do CodeQL na página de Segurança do seu repositório. A página de Segurança é onde todas as informações relacionadas à segurança são exibidas.

1. Navegue até a aba **Security** na barra de navegação superior do seu repositório.
2. Selecione **Code Scanning** sob o título "Vulnerability alerts" na barra de navegação à esquerda.

Esta tela conterá todas as vulnerabilidades identificadas pelo CodeQL no código deste repositório. Explore os diferentes filtros e capacidades de busca nesta página. Essas capacidades de filtragem tornam-se muito úteis quando você está lidando com muitas descobertas!

### :keyboard: Atividade 3: Revisar um Alerta

Nesta atividade, exploraremos a interface de usuário do alerta. Vamos revisar o fluxo de dados da vulnerabilidade, identificar qual parte do código o alerta impacta e obter mais informações sobre o alerta.

**Alert status**: Esta seção exibe o status atual do alerta (aberto ou fechado), identifica a branch onde a verificação detectou o alerta e mostra o timestamp do alerta.

![alert-status](/images/alert-status.png)

**Location information**: Esta seção descreve qual parte do código é vulnerável.

![location-information](/images/location-information.png)

**Paths**: Clicar em "Show Paths" lhe dará insights adicionais sobre o fluxo de dados do alerta. O modal nos mostra onde a entrada do usuário (chamamos isso de "fonte") flui através da aplicação até ser processada (chamamos isso de "sumidouro"). Isso visualiza o fluxo de dados através da sua aplicação.

**Recommendations**: Esta seção fornece uma visão geral rápida da ferramenta (CodeQL neste caso), ID da Regra, e até permite que você visualize a consulta do CodeQL usada para encontrar esta vulnerabilidade. Você pode visualizar a consulta clicando em **Visualizar fonte**. Além disso, este painel inclui recomendações para corrigir esta vulnerabilidade. Clique em **Mostrar mais** para visualizar a recomendação completa.

![recommendations](/images/recommendations.png)

**Audit trail**: A trilha de auditoria mostra o histórico do alerta. Esta trilha mostrará o status à medida que os usuários marcam um alerta como fechado ou corrigem um alerta no código.

![audit-trail](/images/audit-trail.png)

**Alert triage**: Use os botões no canto superior direito do alerta para triagem ou para criar um novo problema para o alerta. Não faça nada ainda. Vamos entrar nesses botões em um momento. 😄

**Additional info**: Finalmente, o painel do lado direito contém informações como tags, informações CWE e a severidade do alerta.

![additional-information.png](/images/additiona-information.png)

### :keyboard: Atividade 4: Descartar um Alerta

Agora que estamos familiarizados com o layout do alerta, vamos trabalhar no processo de fechar um.

1. Dentro deste mesmo alerta, clique em **Dimiss Alert**, escolha qualquer motivo para o descarte e adicione uma nota curta.
2. Clique em **Dimiss Alert**.
3. Neste ponto, o alerta mudará seu estado para "Dismissed". Você pode agora ver a alteração que fez na trilha de auditoria na parte inferior do alerta.
4. Navegue de volta para **Security** > **Code Scanning**. Você verá que você só tem 1 alerta listado.
5. Clique em **1 closed**. Isso o levará aos alertas fechados onde você pode visualizar o alerta que acabou de fechar.

![one-closed-alert.png](/images/one-closed-alert.png)

7. (Opcional) Você também pode reabrir o alerta abrindo-o e, em seguida, selecionando **Reopen Alert**.

### :keyboard: Atividade 5: Criar um Problema no GitHub para um Alerta

Este último passo mostrará como criar um Problema no GitHub para acompanhar o trabalho que envolve resolver uma vulnerabilidade. Os problemas fornecem um espaço para colaboração para um problema de segurança e podem ser atribuídos a pessoas ou equipes.

1. Abra um dos alertas abertos que o CodeQL identificou na verificação.
2. Clique no botão verde **Create Issue** no canto superior direito do alerta. Se você não vir este botão, verifique o status do alerta para garantir que é um alerta aberto.
3. Adicione quaisquer detalhes que você gostaria de incluir no novo formulário de problema.
4. Clique em **Submit new issue**.
5. Para visualizar seu problema, clique em **Issues** na barra de navegação superior do seu repositório.

Espere cerca de 20 segundos e então atualize esta página (a página onde você está seguindo as instruções). [GitHub Actions](https://docs.github.com/en/actions) será atualizado automaticamente para o próximo passo.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Obter ajuda: [Poste em nosso fórum de discussão](https://github.com/skills/.github/discussions) &bull; [Revise a página de status do GitHub](https://www.githubstatus.com/)

&copy; 2025 GitHub &bull; [Código de Conduta](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
