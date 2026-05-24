# 🐾 Projeto Módulo 3 – Low Code / No Code / Vibecode

> **Disciplina:** Engenharia de Prompt e Aplicações em IA

> **Professor(a):** Kadidja Valéria

> **Data:** 11/05/2026

> **Turma:** ENG. SOFT + S.I – 6ª feira – SEDE UDF

---

## 📌 Desafio Escolhido

O grupo desenvolveu o **PetVizinho**, uma plataforma web de adoção responsável de animais que conecta ONGs, protetores independentes e famílias interessadas em adotar pets.

**Problema resolvido:** Facilitar o processo de adoção de animais, eliminando burocracia e aproximando geograficamente quem quer adotar de quem cuida dos animais.

**Funcionalidades desenvolvidas:**

- 🔍 Busca e filtro de pets por espécie, idade, porte e localização
- 🗺️ Mapa interativo com ONGs e protetores próximos ao usuário
- 💬 Chat em tempo real entre adotantes e protetores
- 🚨 Sistema de alerta para pets perdidos
- ❤️ Lista de favoritos e histórico de visualizações
- 📋 Cadastro de pets para adoção
- 🌙 Tema claro/escuro e suporte a dois idiomas (PT/EN)

---

## 🖥️ Protótipo

### Acesso ao projeto

> O protótipo completo está disponível no arquivo `petvizinho.html` — basta abrir no navegador.

### Prints das telas

> Consulte a pasta [`/docs`](https://github.com/mikeiasribeiro/engenharia-de-prompt-e-aplicacoes-em-IA/blob/main/projeto/docs) para visualizar os prints de cada tela.

| Tela | Descrição |
|---|---|
| `tela-home.png` | Página principal com hero, busca e cards de pets |
| `tela-mapa.png` | Mapa interativo com ONGs próximas |
| `tela-chat.png` | Chat em tempo real com protetor |
| `tela-dark.png` | Interface no modo escuro |
| `tela-detalhe.png` | Modal de detalhes do pet |

### Como o protótipo funciona

1. Abra o arquivo `petvizinho.html` no navegador
2. Permita o acesso à localização para ver ONGs próximas
3. Clique em qualquer card de pet para ver detalhes
4. Use o botão "Conversar" para abrir o chat
5. Experimente o modo escuro pelo ícone ☀️/🌙 na navbar

---

## ⚙️ Plataforma Utilizada

**Claude.ai (Anthropic) — Vibecode / IA Generativa**

### Justificativa da escolha

A ferramenta foi escolhida por permitir gerar uma aplicação web completa em HTML/CSS/JavaScript através de prompts em linguagem natural, sem necessidade de escrever código manualmente. Isso se encaixa perfeitamente na proposta Low Code / No Code / Vibecode da disciplina.

**Características que motivaram a escolha:**

- Geração de código funcional a partir de descrições textuais
- Iteração rápida: cada ajuste é feito via prompt
- Sem necessidade de infraestrutura ou servidor
- Resultado final é um único arquivo `.html` portátil

---

## ✅ Vantagens Identificadas

1. **Velocidade de prototipação** — A aplicação completa foi criada em horas, não semanas. Um projeto desse escopo levaria muito mais tempo com desenvolvimento tradicional.

2. **Sem conhecimento técnico profundo** — Foi possível criar funcionalidades avançadas (mapa Leaflet, chat com BroadcastChannel, tema dark/light, i18n) apenas descrevendo o que se queria em português.

3. **Iteração imediata** — Cada melhoria foi aplicada instantaneamente via prompt, sem ciclos de compilação, deploy ou configuração de ambiente.

4. **Código de qualidade** — O código gerado seguiu boas práticas (CSS variables, acessibilidade, responsividade, animações), algo que seria difícil de alcançar rapidamente no desenvolvimento manual.

5. **Integração com APIs externas** — A IA integrou automaticamente APIs como Dog CEO, The Cat API, Leaflet e Nominatim sem configuração manual.

---

## ⚠️ Limitações Encontradas

1. **Customização visual fina** — Ajustes muito específicos de pixel e comportamento exigiram múltiplos prompts iterativos, pois a IA nem sempre interpretava exatamente o que se queria visualmente.

2. **Sem backend real** — A plataforma usa `localStorage` para persistência, o que significa que os dados não são compartilhados entre dispositivos diferentes. Um projeto real precisaria de banco de dados.

3. **Dependência da plataforma** — O projeto depende do Claude.ai para evoluções futuras. Se a plataforma mudar sua política ou preço, a continuidade fica comprometida (lock-in tecnológico).

4. **Imagens de APIs públicas** — A consistência visual das fotos dos pets depende de APIs externas gratuitas (Dog CEO, The Cat API) que podem estar indisponíveis ou retornar imagens não ideais.

5. **Limite de contexto** — Em projetos muito longos, a IA pode "esquecer" partes anteriores do código, exigindo que o desenvolvedor reenvie o arquivo atualizado a cada sessão.

---

## 📚 Reflexão Crítica

### Como lidamos com as limitações

**Problema do backend:** Utilizamos `localStorage` com uma camada de abstração (`Storage Service`) que simula operações de banco de dados. Isso permite evoluir futuramente para um backend real (ex.: Supabase) com mudanças mínimas no código.

**Problema das imagens:** Criamos um sistema de mapeamento raça→API (`DOG_BREED_MAP`, `CAT_BREED_MAP`) que busca imagens por raça específica em vez de aleatórias, garantindo consistência visual entre as miniaturas de cada pet.

**Problema do lock-in:** O código gerado é HTML/CSS/JS puro, sem dependências proprietárias — pode ser editado por qualquer desenvolvedor sem o Claude.ai.

### Aprendizados sobre Low Code / Vibecode

- A qualidade do resultado depende diretamente da qualidade do prompt (Engenharia de Prompt)
- É essencial revisar o código gerado — a IA pode cometer erros sutis (ex.: formatos de imagem incorretos)
- Vibecode é mais poderoso quando combinado com revisão humana crítica

---

## 👥 Colaboração

| Integrante | Função | Responsabilidades |
|---|---|---|
| **Mikeias** | Desenvolvimento & Prompt Engineering | Elaboração dos prompts, revisão do código, integrações com APIs, correções técnicas |
| **Paloma** | Design & UX | Definição visual, revisão de layout, testes de usabilidade, prints do protótipo |
| **Shira** | Pesquisa & Documentação | Pesquisa de plataformas, redação do README, análise crítica, organização do repositório |

**Organização:** O grupo utilizou sessões colaborativas presenciais para definir os requisitos e dividiu as revisões de forma assíncrona via GitHub.

---

## 📝 Registro da Aula

| Campo | Info |
|---|---|
| **Data** | 11/05/2026 |
| **Atividade** | Discussão crítica + mini-projeto de aplicação |
| **Local** | Laboratório de informática / Quadro branco |
| **Professor(a)** | Kadidja Valéria |
| **Disciplina** | Engenharia de Prompt e Aplicações em IA |

---

## 🚀 Próximos Passos

- [ ] Conectar a um backend real (Supabase) para persistência entre dispositivos
- [ ] Adicionar sistema de autenticação com Google OAuth real
- [ ] Implementar notificações push nativas
- [ ] Criar versão mobile (PWA)
- [ ] Adicionar sistema de avaliação pós-adoção
- [ ] Integrar com WhatsApp Business API para contato direto

---

Feito com ❤️ por Mikeias, Paloma e Shira — UDF 2026
