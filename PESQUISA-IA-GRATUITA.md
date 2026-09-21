# Pesquisa: IA gratuita como cérebro de SPA estática (GitHub Pages, single-file)

**Data:** 2026-09-21
**Pergunta:** Quais IAs gratuitas podem rodar como "cérebro" do Estudo.AI (index.html único, hospedado no GitHub Pages, sem backend) sem exigir chave digitada pelo usuário (BYOK)?

**Restrição fundamental:** GitHub Pages é estático. Qualquer chave embutida no HTML/JS é pública. Portanto "IA gratuita sem BYOK" só existe em 4 arquiteturas:

1. Serviço cloud com conta do usuário (dev sem chave)
2. Serviço cloud anônimo sem chave
3. Inferência local no navegador (sem rede, sem chave)
4. Backend próprio (queima o single-file — fora do escopo)

## Veredito (atualizado em 2026-09-21)

Nenhum serviço em nuvem mantém API "sem chave + CORS aberto" de forma confiável e rápida em 2026. Testes ao vivo:

| Opção | Resultado do teste ao vivo |
|---|---|
| **Pollinations** (legacy anônimo) | ✅ **Escolhido.** GET sem chave funciona (CORS `*`), anônimo não deprecado. Fila pública: 1 request/IP por vez → 429 "Queue full" em rajada; respostas levam ~1-2 min. Modelos legados (`gpt-4o-mini`, `llama`) mortos → usar prompt sem model (default). Funciona até de `file://`. |
| **Puter.js** | ❌ Rejeitado. Lib oficial exige origem http/https: `Unsupported Protocol` em `file://`. Funcionaria no GitHub Pages, mas quebra o teste local do usuário (que abre o arquivo direto). |
| **AI Horde** | ❌ Removido (pedido do usuário). Fila anônima lenta, JSON pouco confiável, dependenceia de workers voluntários. |
| **Gemini Nano (Chrome local)** | ❌ Removido (pedido do usuário). Somente Chrome, modelo fraco. |
| **OpenRouter / Groq / demais free tiers** | ❌ Exigem chave do usuário (BYOK) — redundante com Gemini BYOK já presente. |

**Conclusão:** providers finais = `pollinations` (grátis, sem chave, default) + `gemini` (BYOK, opcional). Fila do Pollinations é o custo aceito por "sem chave".

## Candidatos descartados

### Layla AI (layla.ai) — agente de viagem
- API enterprise-gated (sales-led), Bearer partner key, sem self-serve. Domínio específico (viagem), não é LLM genérico. **Não viável.**
- Fontes: https://layla.ai/ · https://layla.ai/llms.txt · https://github.com/api-evangelist/layla-ai/blob/main/apis.yml

### Layla Network.AI (layla-network.ai) — app offline
- LLM roda no device mobile; SDK restrito a WebView do app; sem cloud API. **Não viável.**
- Fontes: https://www.layla-network.ai/ · https://github.com/l3utterfly/layla-sdk · https://github.com/l3utterfly/Layla-Server

### Jev (TypeSafe AI, api.typesafe.ai) — modelo System One
- Modelo de decisão/classificação (noul/choice/score), **não gera texto livre** — não serve pra gerar questões/resumos.
- Pago: $42/B tokens input; chave Bearer obrigatória; CORS não documentado; MCA 2.4 proíbe compartilhar credenciais. **Não viável.**
- Fontes: https://docs.typesafe.ai/introduction · https://docs.typesafe.ai/models.md · https://typesafe.ai/legal/mca

### Pollinations (text.pollinations.ai) — ESCOLHIDO
- Legacy anônimo VIVO: `deprecation_notice` oficial confirma "Anonymous requests to text.pollinations.ai are NOT affected". GET-only (POST → 405), CORS `*`, funciona de `file://` (origin null aceita).
- Limitações verificadas: fila **1 request/IP** (429 "Queue full" em rajada; esperar a anterior terminar), modelos antigos removidos (404 em `openai/gpt-4o-mini`, `llama`), sem controle de modelo/temperatura.
- Mitigação no app: retry automático com espera de 15s até 5x + timeout de 180s.
- Fontes: https://gen.pollinations.ai/docs · https://raw.githubusercontent.com/pollinations/pollinations/main/APIDOCS.md

### DuckDuckGo AI Chat / HuggingChat
- Sem API pública oficial. Probes ao vivo: DDG 418 challenge sem CORS; HuggingChat 302 sem CORS. **Não viável.**
- Fontes: https://duckduckgo.com/duckduckgo-help-pages/duckai/chat-models · https://huggingface.co/docs/inference-providers/index

### OpenRouter (chave própria) e demais free tiers (Groq, Cerebras, Mistral, Gemini, Cloudflare, HuggingFace)
- Todos exigem chave (free tiers com rate limits). Probes ao vivo: `/api/v1/chat/completions` sem chave → 401. Chave embutida vaza + viola ToS.
- Fontes: https://openrouter.ai/docs/quickstart · https://openrouter.ai/docs/faq · https://console.groq.com/docs/quickstart · https://inference-docs.cerebras.ai/ · https://docs.mistral.ai/ · https://ai.google.dev/gemini-api/docs/api-key · https://developers.cloudflare.com/workers-ai/get-started/rest-api/ · https://huggingface.co/docs/inference-providers/pricing

### GitHub Models
- Aposentado em 30/07/2026. **Morto.**
- Fonte: https://docs.github.com/en/github-models

## Opções viáveis (detalhe)

### Puter.js (cloud, user-pays) — REJEITADO
- Modelo: o **usuário final** tem conta Puter; o custo da IA é coberto pela conta dele. Dev não precisa de chave, não expõe segredo.
- Bloqueio: `Puter.js Error: Unsupported Protocol` ao abrir via `file://`. Exige servidor http/https — incompatível com o fluxo atual do usuário (abre o index.html direto do disco).
- Ficaria como opção se o app fosse servido (GitHub Pages), mas não é o caso de teste.
- Fontes: https://docs.puter.com/ · https://docs.puter.com/user-pays-model/

### AI Horde (cloud anônima) — REMOVIDO
- Crowdsourced, chave anônima `0000000000`, sem conta. Removido a pedido do usuário: fila anônima lenta e respostas JSON pouco confiáveis na prática (workers fracos + cap 512 tokens).
- Fontes: https://aihorde.net/ · https://raw.githubusercontent.com/Haidra-Org/AI-Horde/main/README.md

### WebLLM / Transformers.js (local) — NÃO ADOTADO
- WebLLM: WebGPU, Llama-3.2-3B etc. Transformers.js: WASM/WebGPU, modelos 0.5–3B.
- Grátis, privado, offline após download (~1–2 GB). Não adotado: usuário pediu provider **online**, e download grande + WebGPU não é confiável no i5-3470/HD Graphics.
- Fontes: https://webllm.mlc.ai/docs/ · https://huggingface.co/docs/transformers.js

### Chrome Built-in AI (Prompt API / Gemini Nano) — REMOVIDO
- Gemini Nano local no Chrome, sem chave. Removido a pedido do usuário (Chrome-only, modelo fraco).
- Fonte: https://developer.chrome.com/docs/ai/built-in

## Decisão final (implementada em 2026-09-21)

Providers no `index.html`:
1. **Default: Pollinations** (grátis, sem chave, anônimo, funciona de `file://`). Retry automático de fila (5x, 15s) + timeout 180s.
2. **Opcional: Google Gemini (BYOK)** — chave própria do usuário, manteve como modo potência.

Horde e Gemini Nano completamente removidos (código + UI). Puter.js rejeitado (bloqueia `file://`). WebLLM/Transformers.js descartado (pedido: online).

Backend (Firebase AI Logic) única via de "IA forte gratuita sem chave pro usuário final", mas quebra o caráter single-file.