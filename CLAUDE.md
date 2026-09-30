# CLAUDE.md — FEA SYSTEM

Este arquivo orienta o Claude Code em todo trabalho neste repositório. Leia antes de qualquer alteração.

## 1. Sobre o projeto

- **Nome:** FEA SYSTEM
- **O que é:** plataforma web interna de Customer Success e Suporte para os cursos online de estética do Dr. João Pithon (full face, toxina, fios, corporal, intercorrência etc.).
- **O que não é:** não é um dashboard de visualização nem um produto para os alunos. É um sistema operacional de CS.
- **Loop central:** health score → risco/oportunidade → ação → follow-up → resultado. Toda funcionalidade nova deve fortalecer algum passo desse loop.
- **Usuários:** somente o time interno (CS, suporte, coordenação e liderança). Não são perfis técnicos.

### Roadmap por fases

1. Arquitetura, banco de dados, autenticação, layout base, cadastro de alunos, perfil 360º, produtos
2. Engajamento, health score, módulo de suporte
3. Portfólio de CS, tarefas, onboarding, alertas
4. Relatórios e integrações
5. Inteligência preditiva

**Fase atual:** Fase 1, ainda não iniciada (o repositório não tem código). Não implemente nada de fases posteriores sem pedido explícito.

## 2. Decisões em aberto

Enquanto um item abaixo estiver em aberto, **não assuma um valor**: pergunte antes de criar código, configuração ou dependência que dependa dele.

| # | Decisão | Situação | Recomendação registrada |
|---|---------|----------|-------------------------|
| 1 | Stack (frontend, backend, banco, auth) | Em aberto | Next.js + Supabase (Postgres) |
| 2 | Hospedagem | Em aberto | Vercel para o app; Hostinger só para o domínio. Se for tudo na Hostinger, precisa ser VPS (hospedagem compartilhada não roda este app) |
| 3 | Cor de destaque e cores de status (crítico, atenção, saudável) | Em aberto | Definir com o time de marca |
| 4 | Fonte | Em aberto | Inter |
| 5 | Idioma dos identificadores de código (tabelas, variáveis) | Em aberto | — |
| 6 | Regras de negócio: fórmula do health score, critérios de risco, status do aluno | Em aberto | Não há recomendação: a regra vem do negócio |
| 7 | Responsável por aprovar regras de negócio | Em aberto | — |

Quando uma decisão for tomada, atualize a linha correspondente e a seção relacionada neste arquivo.

## 3. Regras de trabalho

### Idioma
- Respostas, comentários de código, mensagens de commit, descrição de PR e todo texto da interface: português.

### Regras de negócio
- Nunca invente regra de negócio (fórmula do health score, critério de risco, status de aluno, segmentação etc.). Se não estiver explícita no código ou neste arquivo, pergunte.
- Nunca altere a lógica de cálculo do health score sem confirmar a regra com o usuário.

### Simplicidade
- Prefira a solução direta à abstração prematura. O time de engenharia é pequeno e precisa conseguir manter o que for construído.
- Nada de frameworks extras, microserviços ou camadas novas sem necessidade comprovada.
- Onde já existir tela, fluxo ou componente, siga o padrão implementado em vez de criar um paralelo.

### Critério de priorização
Ao escolher entre alternativas, prefira a que mais melhora:
1. Retenção de aluno
2. Tempo de resposta do CS
3. Escalabilidade do time (menos cliques e menos esforço manual)

## 4. Ações que exigem confirmação explícita

Pergunte antes e só execute após o "sim" do usuário:

- Commit ou push na `main`. Todo trabalho acontece em branch própria e entra via PR.
- Instalar, remover ou atualizar dependência.
- Alterar schema do banco (criar, alterar ou remover tabela, coluna ou índice).
- Qualquer ação destrutiva: apagar ou sobrescrever registro, drop de tabela, reset de dados.
- Mudar a lógica do health score ou de qualquer regra de negócio.

## 5. Dados de alunos (LGPD)

O sistema guarda dados pessoais de alunos. Até que existam regras mais detalhadas:

- Nunca coloque dados reais de alunos em código, seeds, testes, logs, commits ou PRs. Use dados fictícios.
- Nunca faça commit de credenciais, chaves de API ou arquivos `.env`.

## 6. Identidade visual

⚠️ Hipótese inicial baseada no logo FEA (fundo preto, tipografia branca, estética minimalista). Confirmar com o time de marca (decisões 3 e 4).

- Fundo: `#0A0A0A`
- Texto primário: `#FFFFFF`
- Texto secundário / bordas: `#E5E5E5`
- Cor de destaque e cores de status: **em aberto**. Preto e branco não bastam para diferenciar aluno crítico de saudável; não use cores de status até a decisão 3 ser fechada.
- Tom de voz da interface: direto, simples, sem jargão técnico. Escreva para o time de CS, não para desenvolvedores.

## 7. Estrutura e comandos

A preencher quando a stack for definida (decisão 1): estrutura de pastas, como rodar localmente, como rodar testes e lint, como fazer deploy.
