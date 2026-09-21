# Estudo.AI

Gerador inteligente de questões e resumos de estudo — aplicação de página única (SPA), 100% client-side, sem backend, sem chave obrigatória.

Hospedado: <https://jonjonesbr.github.io/Estudo.AI/>

## Sobre

Transforma materiais de estudo (texto colado ou arquivos `.txt`, `.pdf`, `.docx`) em:

- Questões de múltipla escolha
- Questões verdadeiro/falso
- Questões abertas (discursivas)
- Resumos estruturados em Markdown

Tudo em um único arquivo `index.html`, com quiz interativo, exportação para `.pdf`/`.json`/`.txt`, estatísticas de estudo e cronômetro.

## Provedores de IA

| Provedor | Chave | Custo | Observações |
|---|---|---|---|
| **Pollinations** (default) | Nenhuma | Grátis, anônimo | API pública sem login. Fila compartilhada: em horários cheios a resposta leva ~1-2 min. Retry automático embutido (5 tentativas, 15s de espera) + timeout de 180s. Funciona até abrindo o `index.html` direto do disco (`file://`). |
| **Google Gemini** (opcional) | Chave própria (BYOK) | Tier grátis do Google | Modo potência: mais rápido e estável. A chave fica só no navegador do usuário (localStorage), nunca é enviada ao servidor do app. |

### Removidos nesta versão

- **AI Horde** — fila anônima lenta e respostas JSON pouco confiáveis (workers fracos, cap de tokens).
- **Gemini Nano (Chrome local)** — exclusivo do Chrome e modelo limitado.
- **Puter.js** — exigia servidor http/https e quebrava ao abrir o arquivo via `file://`.

Detalhes da pesquisa: [PESQUISA-IA-GRATUITA.md](PESQUISA-IA-GRATUITA.md).

## Como usar

1. Abra o `index.html` (ou o link do GitHub Pages).
2. Selecione o provedor:
   - **Gratuito (Pollinations — sem chave)** — default, nada a configurar.
   - **Google Gemini (chave própria)** — cole sua chave do [Google AI Studio](https://aistudio.google.com/app/apikey). Salvar local é opcional.
3. Cole o material (ou carregue `.txt`/`.pdf`/`.docx`).
4. Defina quantidade e dificuldade e clique em gerar (múltipla escolha, verdadeiro/falso, abertas ou resumo).
5. Responda o quiz, verifique as respostas, exporte se quiser.

> Dica: para resumos, use apenas o primeiro bloco de material.

## Deploy automático (GitHub Pages)

O Pages está configurado no modo **deploy from branch** (`master`, raiz). Todo `git push` na `master` publica o site automaticamente — não há workflow para manter.

## Estrutura

- `index.html` — app inteiro: HTML, CSS (variáveis + Tailwind CDN), JavaScript (leitura de arquivos, chamadas de IA, quiz, timer, exportação).
- `PESQUISA-IA-GRATUITA.md` — pesquisa e veredito sobre alternativas gratuitas de IA sem chave.

## Tecnologias

- HTML5 + CSS3 (variáveis CSS) + [Tailwind CSS](https://tailwindcss.com/) via CDN
- JavaScript (ES6+)
- [pdf.js](https://mozilla.github.io/pdf.js/), [Mammoth.js](https://github.com/mwilliamson/mammoth.js), [jsPDF](https://github.com/parallax/jsPDF), [Font Awesome](https://fontawesome.com/)

## O que pode ser melhorado

- **Fila do Pollinations** — o limite de 1 request por IP torna a espera longa nos horários cheios. Mitigações futuras: alternância entre Pollinations e WebLLM, ou fila com previsão de espera na UI.
- **WebLLM / Transformers.js** — inferência local no navegador (sem rede, sem chave, privado). Custa download inicial de ~1-2 GB e exige WebGPU decente; bom fallback offline quando o hardware acompanhar.
- **Puter.js** — user-pays, sem chave de dev, se o app for servido via https (GitHub Pages já atende); bloqueia `file://`.
- **Backend opcional (ex.: Firebase)** — permitiria IA forte sem chave para o usuário final, mas quebra o caráter single-file.
- **Testes automatizados** — hoje a validação é manual + testes de VM descartáveis; um arquivo de testes versionado daria segurança nas próximas mudanças.
- **Cache de respostas** — guardar gerações iguais (mesmo material) para não pagar fila duas vezes.

## Contribuição

Issues e pull requests são bem-vindos: <https://github.com/JonJonesBR/Estudo.AI>.

## Licença

MIT — use, modifique e distribua livremente.