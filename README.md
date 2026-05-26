# Estudo.AI: Gerador Inteligente de Questões e Resumos

##  Sobre o Projeto

O Estudo.AI é uma ferramenta de estudo interativa, de página única (Single Page Application), projetada para ajudar estudantes e educadores a transformar materiais de estudo brutos em conteúdo de aprendizado dinâmico. Utilizando a API do Google Gemini, este aplicativo pode ler textos, PDFs e documentos Word para gerar automaticamente questões de múltipla escolha, verdadeiro/falso, perguntas abertas e resumos inteligentes.

Esta versão do projeto utiliza um tema em tons pastéis, focado em uma experiência de usuário limpa, suave e acessível, sem a complexidade de múltiplos temas.

## ✨ Funcionalidades Principais

- Geração com IA: Cria quizzes e resumos usando o poder da API do Google Gemini.
- Múltiplos tipos de questão: Gera questões de múltipla escolha, verdadeiro/falso e discursivas.
- Resumos inteligentes: Condensa textos longos em resumos estruturados em formato Markdown.
- Carregamento de arquivos: Aceita entrada de texto via cópia e cola ou carregamento de arquivos .txt, .pdf e .docx.
- Quiz interativo: Permite que o usuário responda as questões geradas e verifique seu desempenho.
- Timer de estudo: Inclui um cronômetro para gerenciamento do tempo de estudo.
- Exportação de conteúdo: Permite exportar os resultados gerados para .pdf, .json ou .txt.
- Design responsivo: Interface limpa e adaptável a desktops, tablets e celulares, com um tema pastel agradável.
- Portabilidade: Todo o aplicativo está contido em um único arquivo index.html, facilitando a distribuição e o uso local.

##  Tecnologias Utilizadas

- **Front-end:** HTML5, CSS3 (com Variáveis CSS)
- **Estilização:** [Tailwind CSS](https://tailwindcss.com/) (carregado via CDN)
- **Interatividade:** JavaScript (ES6+)
- **Inteligência Artificial:** [Google Gemini API](https://aistudio.google.com/app/apikey)

### Bibliotecas Externas

- [Font Awesome](https://fontawesome.com/) (para ícones)
- [pdf.js](https://mozilla.github.io/pdf.js/) (para leitura de arquivos PDF)
- [Mammoth.js](https://github.com/mwilliamson/mammoth.js) (para leitura de arquivos .docx)
- [jsPDF](https://github.com/parallax/jsPDF) (para exportação em PDF)

##  Como Usar

Como este é um projeto de arquivo único, basta abrir o arquivo `index.html` em qualquer navegador moderno.

### Pré-requisito: Chave da API do Google Gemini

Para que as funcionalidades de IA funcionem, você precisa de uma chave de API do Google Gemini.

1. Acesse o [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Faça login com sua conta do Google.
3. Clique em "Create API key" (Criar chave de API) em um novo projeto.
4. Copie a chave gerada.

### Executando o Aplicativo

1. Abra o arquivo `index.html`.
2. Na seção "Configuração Necessária", cole sua chave de API do Google Gemini no campo indicado.
3. (Opcional) Clique no ícone de salvar para armazenar a chave localmente no seu navegador.

Adicione seu material de estudo:

- Cole o texto diretamente na área "Material 1".
- Clique em "Selecionar Arquivos" para carregar um arquivo .txt, .pdf ou .docx.
- Escolha o número de questões, a dificuldade e clique em um dos botões de geração (ex: "Múltipla Escolha").
- Aguarde o processamento e veja o resultado!

##  Estrutura do Código

Todo o código-fonte (HTML, CSS e JavaScript) está contido no arquivo `index.html` de forma intencional.

- `<head>`: Contém a importação de todas as CDNs (Tailwind, pdf.js, etc.) e o bloco `<style>` com as variáveis de cor (tema pastel) e estilos customizados.
- `<body>`: Define a estrutura da interface, incluindo os modais e o rodapé.
- `<script>` (no final do `<body>`): Contém toda a lógica do aplicativo, incluindo:
  - Manipulação de eventos (cliques, uploads)
  - Funções de leitura de arquivos (`processFile`)
  - Função `callGeminiAPI`, que faz a requisição fetch para a API do Google
  - Funções de exibição (`displayResult`, `displayQuiz`)
  - Lógica do timer, estatísticas e exportação

##  Licença

Este projeto é de código aberto e está licenciado sob a [Licença MIT](https://gemini.google.com/u/2/app/LICENSE.md).  
Sinta-se à vontade para usar, modificar e distribuir o código.

---

Feito com ❤ para ajudar nos estudos.
* **Resumos Inteligentes:** Obtenha resumos concisos e objetivos de qualquer material, destacando os pontos mais importantes.
* **Múltiplos Materiais de Estudo:** Insira diferentes blocos de texto e defina o número de questões para cada um, permitindo uma segmentação eficaz do estudo.
* **Upload de Documentos (em breve):** Preparado para futuras integrações com arquivos `.pdf` e `.docx` para extração automática de conteúdo.
* **Revisão e Feedback Instantâneo:** Para questões de múltipla escolha e verdadeiro/falso, receba feedback imediato sobre suas respostas, com explicações detalhadas.
* **Recomendações de Estudo:** Identifique os tópicos que precisam de mais atenção com base no seu desempenho no quiz.

---

## ‍ Como Usar

O Estudo.AI é intuitivo e fácil de usar. Siga os passos abaixo para começar a gerar seus materiais de estudo:

1.  **Acesse a Aplicação:** Visite o Estudo.AI ao vivo através do GitHub Pages:
    * [**Acesse o Estudo.AI AQUI!**](https://jonjonesbr.github.io/Estudo.IA/)

2.  **Obtenha sua Chave API do Google Gemini:**
    * Para que a IA funcione, você precisará de uma chave da API do Google Gemini.
    * A chave é usada **apenas no seu navegador** e **NÃO é armazenada** em nenhum lugar.
    * Obtenha sua chave gratuitamente em: [**Google AI Studio API Key**](https://aistudio.google.com/app/apikey)

3.  **Insira a Chave API:**
    * Cole sua chave API no campo "Sua Chave API do Google Gemini" na aplicação.

4.  **Adicione Seu Material de Estudo:**
    * Cole o texto do seu material de estudo (anotações, artigos, livros) nas caixas de texto.
    * Você pode adicionar **múltiplos blocos de material** clicando em "+ Adicionar Outro Assunto" e definir quantas questões deseja para cada um.
    * **Dica:** Para resumos, utilize apenas o primeiro bloco de material.

5.  **Configure o Número de Questões:**
    * No campo "Número de Questões a Gerar (Total)", defina quantas questões você deseja ao todo. Certifique-se de que a soma das questões por assunto corresponda a este total.

6.  **Gere Conteúdo:**
    * Clique no botão correspondente à sua necessidade:
        * `Gerar Múltipla Escolha`
        * `Gerar Verdadeiro/Falso`
        * `Gerar Questões Abertas`
        * `✨ Gerar Resumo`

7.  **Revise e Estude!**
    * Para questões, responda o quiz e clique em "Verificar Respostas" para ver seu desempenho, as respostas corretas e explicações.
    * Para resumos, leia o conteúdo gerado e aprofunde seu aprendizado.

---

##  Tecnologias e Ferramentas

Este projeto é construído com as seguintes tecnologias e plataformas:

* **Frontend:**
    * `HTML5`: Estrutura da aplicação.
    * `CSS3` (com [Tailwind CSS](https://tailwindcss.com/)): Estilização moderna e responsiva.
    * `JavaScript`: Lógica de interação e comunicação com a API.
* **Inteligência Artificial:**
    * [**Google Gemini API (Google AI Studio)**](https://aistudio.google.com/): O coração da geração de questões e resumos.
* **Hospedagem & Backend (simplificado):**
    * [**GitHub Pages**](https://pages.github.com/): Hospedagem gratuita da aplicação web.
    * [**Firebase (SDK)**](https://firebase.google.com/): Utilizado para autenticação anônima e potenciais funcionalidades futuras de persistência de dados (atualmente, o `appId` e `firebaseConfig` são passados via variáveis de ambiente do Canvas, mas o código já está preparado para uma possível integração mais robusta).

---

##  Contribuição

Sua contribuição é muito bem-vinda! Se você tiver ideias para melhorias, encontrar bugs ou quiser adicionar novas funcionalidades, por favor:

1.  Abra uma **[Issue](https://github.com/JonJonesBR/Estudo.IA/issues)** para descrever a sua sugestão ou problema.
2.  Crie um **[Pull Request](https://github.com/JonJonesBR/Estudo.IA/pulls)** com suas alterações.

Sua colaboração ajuda a tornar o Estudo.AI ainda melhor para todos os estudantes!

---

##  Contato

Tenho prazer em conectar e discutir sobre IA e desenvolvimento web.

* **GitHub:** [JonJonesBR](https://github.com/JonJonesBR)

---

> "O único limite para o nosso alcance é a extensão da nossa visão." - James Cameron

## Destaques tecnicos

- Codigo organizado para leitura rapida por avaliadores tecnicos.
- Configuracao local documentada sem exposicao de credenciais.
- Separacao entre arquivos versionados e dados sensiveis de ambiente.

## Seguranca e configuracao

Este repositorio nao deve conter credenciais reais. Use .env.example como modelo e mantenha chaves, tokens, senhas e URLs privadas fora do Git.

