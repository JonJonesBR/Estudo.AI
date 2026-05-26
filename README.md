# Estudo.AI: Gerador Inteligente de QuestÃµes e Resumos

## ðŸ“– Sobre o Projeto

O Estudo.AI Ã© uma ferramenta de estudo interativa, de pÃ¡gina Ãºnica (Single Page Application), projetada para ajudar estudantes e educadores a transformar materiais de estudo brutos em conteÃºdo de aprendizado dinÃ¢mico. Utilizando a API do Google Gemini, este aplicativo pode ler textos, PDFs e documentos Word para gerar automaticamente questÃµes de mÃºltipla escolha, verdadeiro/falso, perguntas abertas e resumos inteligentes.

Esta versÃ£o do projeto utiliza um tema em tons pastÃ©is, focado em uma experiÃªncia de usuÃ¡rio limpa, suave e acessÃ­vel, sem a complexidade de mÃºltiplos temas.

## âœ¨ Funcionalidades Principais

- GeraÃ§Ã£o com IA: Cria quizzes e resumos usando o poder da API do Google Gemini.
- MÃºltiplos tipos de questÃ£o: Gera questÃµes de mÃºltipla escolha, verdadeiro/falso e discursivas.
- Resumos inteligentes: Condensa textos longos em resumos estruturados em formato Markdown.
- Carregamento de arquivos: Aceita entrada de texto via cÃ³pia e cola ou carregamento de arquivos .txt, .pdf e .docx.
- Quiz interativo: Permite que o usuÃ¡rio responda as questÃµes geradas e verifique seu desempenho.
- Timer de estudo: Inclui um cronÃ´metro para gerenciamento do tempo de estudo.
- ExportaÃ§Ã£o de conteÃºdo: Permite exportar os resultados gerados para .pdf, .json ou .txt.
- Design responsivo: Interface limpa e adaptÃ¡vel a desktops, tablets e celulares, com um tema pastel agradÃ¡vel.
- Portabilidade: Todo o aplicativo estÃ¡ contido em um Ãºnico arquivo index.html, facilitando a distribuiÃ§Ã£o e o uso local.

## ðŸ› ï¸ Tecnologias Utilizadas

- **Front-end:** HTML5, CSS3 (com VariÃ¡veis CSS)
- **EstilizaÃ§Ã£o:** [Tailwind CSS](https://tailwindcss.com/) (carregado via CDN)
- **Interatividade:** JavaScript (ES6+)
- **InteligÃªncia Artificial:** [Google Gemini API](https://aistudio.google.com/app/apikey)

### Bibliotecas Externas

- [Font Awesome](https://fontawesome.com/) (para Ã­cones)
- [pdf.js](https://mozilla.github.io/pdf.js/) (para leitura de arquivos PDF)
- [Mammoth.js](https://github.com/mwilliamson/mammoth.js) (para leitura de arquivos .docx)
- [jsPDF](https://github.com/parallax/jsPDF) (para exportaÃ§Ã£o em PDF)

## ðŸš€ Como Usar

Como este Ã© um projeto de arquivo Ãºnico, basta abrir o arquivo `index.html` em qualquer navegador moderno.

### PrÃ©-requisito: Chave da API do Google Gemini

Para que as funcionalidades de IA funcionem, vocÃª precisa de uma chave de API do Google Gemini.

1. Acesse o [Google AI Studio](https://aistudio.google.com/app/apikey).
2. FaÃ§a login com sua conta do Google.
3. Clique em "Create API key" (Criar chave de API) em um novo projeto.
4. Copie a chave gerada.

### Executando o Aplicativo

1. Abra o arquivo `index.html`.
2. Na seÃ§Ã£o "ConfiguraÃ§Ã£o NecessÃ¡ria", cole sua chave de API do Google Gemini no campo indicado.
3. (Opcional) Clique no Ã­cone de salvar para armazenar a chave localmente no seu navegador.

Adicione seu material de estudo:

- Cole o texto diretamente na Ã¡rea "Material 1".
- Clique em "Selecionar Arquivos" para carregar um arquivo .txt, .pdf ou .docx.
- Escolha o nÃºmero de questÃµes, a dificuldade e clique em um dos botÃµes de geraÃ§Ã£o (ex: "MÃºltipla Escolha").
- Aguarde o processamento e veja o resultado!

## ðŸ”§ Estrutura do CÃ³digo

Todo o cÃ³digo-fonte (HTML, CSS e JavaScript) estÃ¡ contido no arquivo `index.html` de forma intencional.

- `<head>`: ContÃ©m a importaÃ§Ã£o de todas as CDNs (Tailwind, pdf.js, etc.) e o bloco `<style>` com as variÃ¡veis de cor (tema pastel) e estilos customizados.
- `<body>`: Define a estrutura da interface, incluindo os modais e o rodapÃ©.
- `<script>` (no final do `<body>`): ContÃ©m toda a lÃ³gica do aplicativo, incluindo:
  - ManipulaÃ§Ã£o de eventos (cliques, uploads)
  - FunÃ§Ãµes de leitura de arquivos (`processFile`)
  - FunÃ§Ã£o `callGeminiAPI`, que faz a requisiÃ§Ã£o fetch para a API do Google
  - FunÃ§Ãµes de exibiÃ§Ã£o (`displayResult`, `displayQuiz`)
  - LÃ³gica do timer, estatÃ­sticas e exportaÃ§Ã£o

## ðŸ“„ LicenÃ§a

Este projeto Ã© de cÃ³digo aberto e estÃ¡ licenciado sob a [LicenÃ§a MIT](https://gemini.google.com/u/2/app/LICENSE.md).  
Sinta-se Ã  vontade para usar, modificar e distribuir o cÃ³digo.

---

Feito com â¤ï¸ para ajudar nos estudos.
* **Resumos Inteligentes:** Obtenha resumos concisos e objetivos de qualquer material, destacando os pontos mais importantes.
* **MÃºltiplos Materiais de Estudo:** Insira diferentes blocos de texto e defina o nÃºmero de questÃµes para cada um, permitindo uma segmentaÃ§Ã£o eficaz do estudo.
* **Upload de Documentos (em breve):** Preparado para futuras integraÃ§Ãµes com arquivos `.pdf` e `.docx` para extraÃ§Ã£o automÃ¡tica de conteÃºdo.
* **RevisÃ£o e Feedback InstantÃ¢neo:** Para questÃµes de mÃºltipla escolha e verdadeiro/falso, receba feedback imediato sobre suas respostas, com explicaÃ§Ãµes detalhadas.
* **RecomendaÃ§Ãµes de Estudo:** Identifique os tÃ³picos que precisam de mais atenÃ§Ã£o com base no seu desempenho no quiz.

---

## ðŸ‘¨â€ðŸ’» Como Usar

O Estudo.AI Ã© intuitivo e fÃ¡cil de usar. Siga os passos abaixo para comeÃ§ar a gerar seus materiais de estudo:

1.  **Acesse a AplicaÃ§Ã£o:** Visite o Estudo.AI ao vivo atravÃ©s do GitHub Pages:
    * [**Acesse o Estudo.AI AQUI!**](https://jonjonesbr.github.io/Estudo.IA/)

2.  **Obtenha sua Chave API do Google Gemini:**
    * Para que a IA funcione, vocÃª precisarÃ¡ de uma chave da API do Google Gemini.
    * A chave Ã© usada **apenas no seu navegador** e **NÃƒO Ã© armazenada** em nenhum lugar.
    * Obtenha sua chave gratuitamente em: [**Google AI Studio API Key**](https://aistudio.google.com/app/apikey)

3.  **Insira a Chave API:**
    * Cole sua chave API no campo "Sua Chave API do Google Gemini" na aplicaÃ§Ã£o.

4.  **Adicione Seu Material de Estudo:**
    * Cole o texto do seu material de estudo (anotaÃ§Ãµes, artigos, livros) nas caixas de texto.
    * VocÃª pode adicionar **mÃºltiplos blocos de material** clicando em "+ Adicionar Outro Assunto" e definir quantas questÃµes deseja para cada um.
    * **Dica:** Para resumos, utilize apenas o primeiro bloco de material.

5.  **Configure o NÃºmero de QuestÃµes:**
    * No campo "NÃºmero de QuestÃµes a Gerar (Total)", defina quantas questÃµes vocÃª deseja ao todo. Certifique-se de que a soma das questÃµes por assunto corresponda a este total.

6.  **Gere ConteÃºdo:**
    * Clique no botÃ£o correspondente Ã  sua necessidade:
        * `Gerar MÃºltipla Escolha`
        * `Gerar Verdadeiro/Falso`
        * `Gerar QuestÃµes Abertas`
        * `âœ¨ Gerar Resumo`

7.  **Revise e Estude!**
    * Para questÃµes, responda o quiz e clique em "Verificar Respostas" para ver seu desempenho, as respostas corretas e explicaÃ§Ãµes.
    * Para resumos, leia o conteÃºdo gerado e aprofunde seu aprendizado.

---

## ðŸ› ï¸ Tecnologias e Ferramentas

Este projeto Ã© construÃ­do com as seguintes tecnologias e plataformas:

* **Frontend:**
    * `HTML5`: Estrutura da aplicaÃ§Ã£o.
    * `CSS3` (com [Tailwind CSS](https://tailwindcss.com/)): EstilizaÃ§Ã£o moderna e responsiva.
    * `JavaScript`: LÃ³gica de interaÃ§Ã£o e comunicaÃ§Ã£o com a API.
* **InteligÃªncia Artificial:**
    * [**Google Gemini API (Google AI Studio)**](https://aistudio.google.com/): O coraÃ§Ã£o da geraÃ§Ã£o de questÃµes e resumos.
* **Hospedagem & Backend (simplificado):**
    * [**GitHub Pages**](https://pages.github.com/): Hospedagem gratuita da aplicaÃ§Ã£o web.
    * [**Firebase (SDK)**](https://firebase.google.com/): Utilizado para autenticaÃ§Ã£o anÃ´nima e potenciais funcionalidades futuras de persistÃªncia de dados (atualmente, o `appId` e `firebaseConfig` sÃ£o passados via variÃ¡veis de ambiente do Canvas, mas o cÃ³digo jÃ¡ estÃ¡ preparado para uma possÃ­vel integraÃ§Ã£o mais robusta).

---

## ðŸ¤ ContribuiÃ§Ã£o

Sua contribuiÃ§Ã£o Ã© muito bem-vinda! Se vocÃª tiver ideias para melhorias, encontrar bugs ou quiser adicionar novas funcionalidades, por favor:

1.  Abra uma **[Issue](https://github.com/JonJonesBR/Estudo.IA/issues)** para descrever a sua sugestÃ£o ou problema.
2.  Crie um **[Pull Request](https://github.com/JonJonesBR/Estudo.IA/pulls)** com suas alteraÃ§Ãµes.

Sua colaboraÃ§Ã£o ajuda a tornar o Estudo.AI ainda melhor para todos os estudantes!

---

## ðŸ“§ Contato

Tenho prazer em conectar e discutir sobre IA e desenvolvimento web.

* **GitHub:** [JonJonesBR](https://github.com/JonJonesBR)

---

> "O Ãºnico limite para o nosso alcance Ã© a extensÃ£o da nossa visÃ£o." - James Cameron

## Destaques tecnicos

- Codigo organizado para leitura rapida por avaliadores tecnicos.
- Configuracao local documentada sem exposicao de credenciais.
- Separacao entre arquivos versionados e dados sensiveis de ambiente.

## Seguranca e configuracao

Este repositorio nao deve conter credenciais reais. Use .env.example como modelo e mantenha chaves, tokens, senhas e URLs privadas fora do Git.

