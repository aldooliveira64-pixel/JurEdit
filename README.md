# JurEdit — Ecossistema Jurídico Inteligente

Dashboard único com 6 ferramentas jurídicas integradas, powered by Anthropic Claude.

## 🚀 Deploy em 3 passos

### 1. Clone e instale
```bash
git clone https://github.com/SEU-USUARIO/juredit.git
cd juredit
npm install
```

### 2. Configure a chave da API
```bash
cp .env.example .env.local
# Edite .env.local e adicione sua chave:
# ANTHROPIC_API_KEY=sk-ant-...
```

### 3. Rode localmente
```bash
npm run dev
# Acesse: http://localhost:3000
```

## ☁️ Deploy no Vercel (recomendado)

1. Faça push para o GitHub
2. Acesse [vercel.com](https://vercel.com) → Import Project → selecione o repo
3. Em **Environment Variables**, adicione:
   - `ANTHROPIC_API_KEY` = `sk-ant-...sua-chave...`
4. Clique **Deploy** — pronto em ~2 minutos

## 🌐 Deploy no Netlify

1. Faça push para o GitHub
2. Acesse [netlify.com](https://netlify.com) → Add new site → Import from Git
3. Build command: `npm run build`
4. Publish directory: `.next`
5. Em **Environment variables**, adicione `ANTHROPIC_API_KEY`
6. Deploy!

> **Nota Netlify:** Adicione o plugin `@netlify/plugin-nextjs` no `netlify.toml`

## 🛠️ Ferramentas incluídas

| Ferramenta | Descrição |
|---|---|
| **JurHub** | Dashboard central — bancos de citações/referências, progresso da obra, export completo |
| **JurObra** | Livros, tratados, apostilas, dissertações — gestão de capítulos, sumário com IA |
| **JurPeça** | Petição, parecer, ementa, contrato — análise de PDF/DOCX (4 modos estratégicos) |
| **JurFinanceiro** | Bancário e Mercado de Capitais — escritura, CCB, CRI/CRA, PAS CVM, due diligence |
| **JurBiblioteca** | 28 obras clássicas + busca IA doutrina — auto-save no Hub |
| **JurJurisprudência** | STF, STJ, TST — súmulas + busca IA — auto-save no Hub |

## 🔑 Variáveis de ambiente

| Variável | Obrigatória | Descrição |
|---|---|---|
| `ANTHROPIC_API_KEY` | ✅ Sim | Sua chave da API Anthropic (console.anthropic.com) |

## 📁 Estrutura do projeto

```
juredit/
├── app/
│   ├── layout.jsx          # Layout raiz
│   ├── page.jsx            # Página principal → AppShell
│   ├── globals.css
│   └── api/claude/
│       └── route.js        # Proxy seguro para API Anthropic
├── components/
│   ├── AppShell.jsx        # Dashboard com sidebar + navegação
│   ├── shared/
│   │   └── RichText.jsx    # Renderizador de markdown
│   └── tools/
│       ├── JurHub.jsx
│       ├── JurObra.jsx
│       ├── JurPeca.jsx
│       ├── JurFinanceiro.jsx
│       ├── JurBiblioteca.jsx
│       └── JurJurisprudencia.jsx
├── lib/
│   ├── storage.js          # Adapter localStorage
│   └── docx.js             # Motor DOCX (ZIP + XML Word)
└── package.json
```

## 💡 Como funciona

- **API segura**: todas as chamadas ao Claude passam por `/api/claude` (serverless) — a chave nunca fica exposta no browser
- **Persistência**: dados salvos no `localStorage` do navegador (substituindo o `window.storage` do claude.ai)
- **Auto-save**: citações copiadas no JurJurisprudência e JurBiblioteca são automaticamente salvas no banco do JurHub
- **Export .docx**: motor próprio em JavaScript puro — sem dependências externas para geração de Word

## 🔧 Tecnologias

- **Next.js 14** (App Router)
- **React 18**
- **Anthropic Claude** (claude-sonnet-4-20250514)
- **mammoth.js** (leitura de DOCX)
- **Motor DOCX próprio** (ZIP + XML Word, sem biblioteca externa)

## 📄 Licença

Projeto privado — uso exclusivo do cliente.
