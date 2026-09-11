# 🧪 Higgs - Assistente Pessoal IA Desktop

> Assistente de IA pessoal em desktop com voz neural, memória persistente e suporte a múltiplos provedores de IA em nuvem. Desenvolvido com **Electron** + **React** + **Vite**.

![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=node.js)
![Electron](https://img.shields.io/badge/Electron-43.4+-47848F?logo=electron)
![React](https://img.shields.io/badge/React-19.2+-61DAFB?logo=react)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)

---

## 📋 Sumário

- [O que é Higgs?](#o-que-é-higgs)
- [Características Principais](#características-principais)
- [Requisitos](#requisitos)
- [Instalação](#instalação)
- [Configuração de IA](#configuração-de-ia)
- [Uso](#uso)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Recursos Avançados](#recursos-avançados)
- [Troubleshooting](#troubleshooting)
- [Contribuindo](#contribuindo)

---

## O que é Higgs?

**Higgs** é um assistente pessoal de IA que roda como um aplicativo desktop nativo. Diferente de chatbots web, ele:

- ✅ Funciona **offline** para operações básicas (com failover automático se internet cair)
- ✅ Armazena todas as conversas **localmente** — você controla seus dados
- ✅ Integra-se com sua tela via **captura de screenshot** para análise de conteúdo
- ✅ Reconhece fala em português com **transcrição automática**
- ✅ Fala de volta com **vozes neurais naturais** (sem som robótico)
- ✅ Suporta **atalhos globais** para acesso rápido de qualquer lugar
- ✅ Interface futurista com **visualizador de áudio em tempo real**

---

## Características Principais

### 🎨 Interface Visual Exclusiva
- **Núcleo flutuante animado** que funciona como visualizador de áudio real — as barras reagem ao volume e frequência de sua voz e do microfone
- **Tema grafite escuro** com tipografia moderna (Space Grotesk + Inter + JetBrains Mono)
- **Janela sem moldura** customizada (sem barra de menu padrão do SO)
- **Controles nativos** (minimizar, maximizar, fechar)

### 🤖 IA Multi-Provedor
Alterne entre três provedores sem sair do app:
- **Groq** — Mais rápido, plano gratuito generoso (recomendado)
- **Mistral** — Bom custo-benefício, suporte a imagens
- **DeepSeek** — Modelos especializados (Flash e Pro)

**Failover automático**: se um provedor cair ou atingir limite de uso, o Higgs muda para o próximo sozinho.

### 🎤 Voz e Áudio
- **Reconhecimento de fala** em português (Groq Whisper)
- **Síntese de voz neural** — vozes da Microsoft Edge (natural e fluida)
- **Controle de tom**: ajuste velocidade, altura e volume
- **Fallback automático** para voz do sistema se internet cair
- **Indicador visual** — barras animadas reagem em tempo real

### 💾 Histórico e Memória
- **Conversas persistentes** — salvas automaticamente em JSON local
- **Carregar histórico** — retome qualquer conversa anterior
- **Exportar conversas** — backup em arquivo
- **Apagar histórico** — controle total sobre seus dados
- **Auto-memory** — Higgs lembra de detalhes sobre você (desativável)

### 🔒 Segurança
- **Chaves de API locais** — armazenadas apenas no seu computador (pasta `userData` do Electron)
- **Nunca versionadas** no git ou enviadas para servidores
- **Arquivo de config** (`higgs-config.json`) fora do repositório
- **Contexto isolado** — preload script com sandboxing seguro

### ⚡ Atalhos Globais
- `Ctrl+Shift+J` (Windows/Linux) ou `Cmd+Shift+J` (Mac) — Abre/fecha o app
- `Ctrl+Shift+H` (Windows/Linux) ou `Cmd+Shift+H` (Mac) — Screenshot para análise
- **Configuráveis** em ⚙️ Configurações → Sistema

### 📱 Acesso Mobile (Experimental)
- **Servidor web interno** na porta 4477
- Acesso seguro via PIN
- Controle do Higgs de outros dispositivos na mesma rede

### ⚙️ Personalizável
- Nome do assistente (padrão: "Higgs")
- Personalidade (sarcástica, formal, criativa, etc.)
- Cor de destaque (teal, azul, rosa, etc.)
- Idioma de voz
- Modo "Não Perturbe"
- Sempre acima de outras janelas

---

## Requisitos

| Componente | Versão |
|------------|--------|
| **Node.js** | 18+ |
| **npm** | 8+ (ou yarn/pnpm) |
| **Sistema Operacional** | Windows 10+, macOS 10.13+, Ubuntu 18.04+ |
| **Chave de API** | Groq, Mistral ou DeepSeek (plano gratuito aceitável) |

---

## Instalação

### 1️⃣ Clone o repositório

```bash
git clone https://github.com/KasTilhozk/higgs.git
cd higgs
```

### 2️⃣ Instale dependências

```bash
cd higgs
npm install
```

### 3️⃣ Rode em desenvolvimento

```bash
npm run dev
```

Isso inicia simultaneamente:
- Vite (React dev server na porta 5173)
- Electron (app desktop)

### 4️⃣ Construa para produção

```bash
npm run build
```

Gera executáveis nativos em `release/`

---

## Configuração de IA

### Passo 1: Obtenha uma chave de API

Escolha um (ou mais) provedor e crie uma chave gratuita:

| Provedor | Plano Gratuito | Link |
|----------|----------------|------|
| **Groq** | 7.000 req/mês (recomendado) | https://console.groq.com/keys |
| **Mistral** | 2 milhões tokens/mês | https://console.mistral.ai/api-keys |
| **DeepSeek** | Créditos iniciais | https://platform.deepseek.com/api_keys |

**Dica:** Configure **dois provedores** como fallback. Se o Groq atingir limite, o Higgs muda automaticamente.

### Passo 2: Configure no app

1. Abra o Higgs
2. Clique em **⚙️ Configurações**
3. Vá para a aba **"IA"**
4. Selecione o provedor
5. Cole sua chave de API
6. Clique em **"Testar conexão"** para validar

### Passo 3: Configure modelo e voz (opcional)

- **Modelo**: Deixe o padrão ou escolha um específico
- **Voz**: Selecione em "Aparência" (pt-BR-AntonioNeural é padrão para português)
- **Velocidade/Tom**: Ajuste em "Aparência"

---

## Uso

### Conversando

1. **Digite** sua pergunta no campo de entrada
2. Ou **clique no 🎤** e fale para transcrição automática (requer Groq configurado)
3. Ou **clique no 📷** para perguntar sobre o que está na tela

### Gerenciando conversas

- **➕** — Inicia uma conversa nova (limpa contexto anterior)
- **💾** — Abre histórico
  - Clique em uma conversa para recarregá-la
  - Exporte como JSON
  - Delete conversas antigas
- **⚙️** — Configurações gerais

### Atalhos úteis

| Ação | Windows/Linux | macOS |
|------|---------------|-------|
| Abrir/Fechar Higgs | Ctrl+Shift+J | Cmd+Shift+J |
| Capturar tela | Ctrl+Shift+H | Cmd+Shift+H |
| Foco na barra de entrada | Enter | Enter |

---

## Estrutura do Projeto

```
Higgs/
├── README.md                    ← Documentação (você está aqui)
├── higgs/                       ← Aplicação principal
│   ├── package.json             ← Dependências do projeto
│   ├── main.js                  ← Processo principal Electron
│   ├── preload.js               ← Bridge seguro (contexto isolado)
│   ├── vite.config.mjs          ← Configuração Vite
│   ├── index.html               ← Template HTML
│   ├── QUICK_START.md           ← Guia de início rápido
│   ├── README.md                ← Docs técnicas
│   ├── .gitignore               ← Arquivos ignorados no git
│   │
│   ├── src/                     ← Código React
│   │   ├── main.jsx             ← Entrada React
│   │   ├── App.jsx              ← Componente principal
│   │   ├── components/          ← Componentes reutilizáveis
│   │   ├── hooks/               ← Custom React hooks
│   │   ├── styles/              ← CSS/Tailwind
│   │   └── ...
│   │
│   └── assets/                  ← Recursos estáticos
│       ├── icon.png             ← Ícone do app
│       ├── ...
│       └── ...
│
└── .gitignore                   ← Arquivo de config (local, não versionado)
```

### Arquivos Importantes

| Arquivo | Função |
|---------|--------|
| **main.js** | Processo principal (Electron) — gerencia janela, atalhos, IPC |
| **preload.js** | Bridge seguro entre renderer e main (contexto isolado) |
| **index.html** | Template HTML raiz |
| **vite.config.mjs** | Configuração de build (Vite) |
| **higgs-config.json** | Config do usuário (gerada localmente, não versionada) |

---

## Recursos Avançados

### 🔄 Failover Automático
Se um provedor de IA não responder:
1. Higgs detecta falha após timeout
2. Tenta o próximo provedor configurado
3. Continua conversando transparentemente

### 📸 Análise de Screenshot
1. Clique no 📷 ou use `Ctrl+Shift+H`
2. Selecione a área da tela
3. Faça sua pergunta sobre a imagem
4. Higgs analisa e responde (Groq ou Mistral suportam imagens)

### 🎙️ Fala para Texto
1. Clique no 🎤
2. Fale seu texto em português
3. Groq Whisper transcreve automaticamente

### 💬 Multi-Personalidade
Troque a "personalidade" do Higgs em Configurações:
- **Sarcástica** — Respostas bem-humoradas
- **Formal** — Tom profissional
- **Criativa** — Enfoque em ideias novas
- **Didática** — Explicações detalhadas

### 🌐 Servidor Mobile
Ative "Acesso Mobile" em Configurações e defina um PIN. Outros dispositivos na rede podem acessar via `http://[seu-ip]:4477` + PIN.

---

## Troubleshooting

### ❌ "Configure a chave de API..."

**Solução:**
1. Abra ⚙️ **Configurações**
2. Vá para **IA**
3. Certifique-se de que um provedor está selecionado
4. Cole a chave de API completa
5. Clique **"Testar conexão"**

---

### ❌ Microfone não funciona

**Verificações:**
1. Groq está configurado? (Whisper requer Groq)
2. Permissão de microfone foi concedida?
   - Windows: Configurações → Privacidade → Microfone
   - macOS: Preferências do Sistema → Segurança e Privacidade → Microfone
   - Linux: Verifique com `pactl`
3. Outro app está usando o microfone?

---

### ❌ Atalho de teclado não responde

**Solução:**
1. Verifique se há conflito com outro programa (Higgs avisa)
2. Customize em ⚙️ **Configurações** → **Sistema**
3. Reinicie o app
4. Se ainda não funcionar, tente outro atalho

---

### ❌ App fecha sozinho ou congela

**Verificações:**
1. Você tem uma conexão de internet estável?
2. Teste a chave de API em: ⚙️ **Configurações** → **IA** → **"Testar conexão"**
3. Verifique limite de requisições do provedor
4. Procure por `higgs-config.json` corrompido: delete e reconfigure

---

### ❌ Voz não funciona

**Verificações:**
1. Volume do sistema está ligado?
2. Teste som do PC em outro programa
3. Voz selecionada é compatível? (pt-BR-AntonioNeural é padrão)
4. Internet está estável? (síntese faz requisição)

---

## Tecnologias

| Tecnologia | Uso |
|------------|-----|
| **Electron** | Desktop app nativo |
| **React 19** | UI componentizada |
| **Vite** | Build rápido |
| **Electron-Builder** | Empacotamento e distribuição |
| **msedge-tts** | Síntese de voz (Microsoft Edge) |
| **Lucide React** | Ícones |
| **Groq / Mistral / DeepSeek** | APIs de IA |

---

## Scripts Disponíveis

```bash
# Desenvolvimento
npm run dev                 # Inicia Vite + Electron
npm run dev:react          # Apenas Vite (port 5173)
npm run dev:electron       # Apenas Electron

# Build
npm run build              # Constrói para produção
npm run build:react        # Apenas build React
npm run build:electron     # Apenas electron-builder

# Executar
npm start                  # Inicia app empacotado
```

---

## Segurança e Privacidade

✅ **Seus dados são seus:**
- Conversas salvas **apenas localmente**
- Chaves de API **nunca deixam seu computador**
- Arquivo `higgs-config.json` ignorado no git
- Sem telemetria ou tracking

⚠️ **Notas importantes:**
- Ao usar provedores de IA, suas mensagens vão para os servidores deles (Groq, Mistral, DeepSeek)
- Screenshots analisados são enviados ao provedor escolhido
- Leia as políticas de privacidade de cada provedor

---

## Contribuindo

Encontrou um bug ou tem uma sugestão? Contribuições são bem-vindas!

1. Fork o repositório
2. Crie uma branch: `git checkout -b minha-feature`
3. Commit suas mudanças: `git commit -m "feat: descrição"`
4. Push: `git push origin minha-feature`
5. Abra um Pull Request

---

## Licença

ISC — Veja [LICENSE](LICENSE) para mais detalhes.

---

## Créditos

Desenvolvido por **KasTilhozk** | Status: 🧪 Em Desenvolvimento

---

## Suporte

Dúvidas? Problemas? Abra uma [issue no GitHub](https://github.com/KasTilhozk/higgs/issues) ou consulte [QUICK_START.md](higgs/QUICK_START.md).

**Enjoy your personal AI assistant! 🚀**
