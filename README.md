**Quiz Game em Vue.js**

---

## Visão Geral

Este aplicativo Vue.js é um jogo de trívia onde os usuários podem responder perguntas relacionadas a uma categoria específica. O jogo obtém perguntas da API Open Trivia Database e permite que os jogadores testem seus conhecimentos. A interface do usuário é projetada para ser simples e envolvente, proporcionando uma experiência de jogo fluida.

---

## Funcionalidades

- **Placar:** Acompanhe suas vitórias e derrotas contra o computador.
- **Perguntas Aleatórias:** Receba uma pergunta de trívia aleatória cada vez que jogar.
- **Interface Interativa:** Interface fácil de usar com botões de opção para selecionar respostas.
- **Feedback em Tempo Real:** Receba feedback instantâneo sobre se sua resposta está correta ou não.
- **Próxima Pergunta:** Avance para a próxima pergunta após enviar uma resposta.

---

## Como Jogar

1. **Responder Perguntas:** Escolha uma resposta para cada pergunta de trívia apresentada.
2. **Enviar:** Clique no botão "Enviar" para enviar sua resposta.
3. **Feedback:** Receba feedback sobre se sua resposta está correta ou incorreta.
4. **Próxima Pergunta:** Clique no botão "Próxima pergunta" para passar para a próxima pergunta.
5. **Placar:** Fique de olho no placar para acompanhar suas vitórias e derrotas.

---

## Tecnologias Utilizadas

- **Vue.js:** Framework front-end JavaScript para construir interfaces de usuário interativas.
- **Axios:** Cliente HTTP para fazer requisições à API.
- **Open Trivia Database API:** Fonte de perguntas de trívia para o jogo.
- **HTML, CSS, JavaScript:** Tecnologias web fundamentais para marcação, estilização e script.

---

## Configuração

1. Clone o repositório.
2. Execute `npm install` para instalar as dependências do projeto.
3. Atualize o endpoint da API Open Trivia Database no hook `created` de `App.vue` com sua categoria desejada.
4. Execute `npm run serve` para iniciar o servidor de desenvolvimento.
5. Abra o aplicativo em seu navegador da web.

---

## Créditos

- **Autor:** [Felipe Rodolfo]
- **Open Trivia Database:** [Link para a Open Trivia Database](https://opentdb.com/)

---

## Licença

Este projeto é licenciado sob a [Licença MIT](LICENSE).
