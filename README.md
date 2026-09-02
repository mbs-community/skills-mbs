# MBS Skills Hub 🚀

Repositório central de **skills** (Agent Skills) da comunidade **MBS / COMUNYTTI**.

Uma _skill_ é uma pasta com instruções que ensinam o agente de IA (Claude Code, Cursor, Copilot, etc.) a executar uma tarefa específica de um jeito consistente — um framework de consultoria, um checklist, um fluxo repetível. O agente carrega a skill sozinho quando a conversa combina com a `description` dela.

Este repo segue o padrão do ecossistema [`skills`](https://skills.sh) (`npx skills`), então qualquer pessoa instala uma skill daqui com um comando só.

---

## 📚 Catálogo de Skills

| Skill | Categoria | Descrição | Link |
| :--- | :--- | :--- | :--- |
| `value-proposition-canvas` | Estratégia / Negócios | Conduz o preenchimento guiado de um **Value Proposition Canvas** (Canvas da Proposta de Valor) bloco a bloco — contexto → Perfil do Cliente (Tarefas, Dores, Ganhos) → Mapa de Valor (Produtos, Analgésicos, Criadores de Ganho) → teste de fit → checklist de erros comuns → artefato visual final em HTML. Exemplos voltados ao universo de saúde/founders. | [Ver skill](./skills/value-proposition-canvas) |

---

## ⚡ Instalar via `npx skills` (recomendado)

O ecossistema [`skills`](https://skills.sh) funciona como um "npm para agentes de IA": o próprio GitHub é o registro. O CLI detecta qual agente você usa (Claude Code, Cursor, Copilot…) e injeta os arquivos no diretório de configuração certo.

```bash
# Instala todas as skills deste repo no projeto atual
npx skills add mbs-community/skills-mbs

# Instala uma skill específica
npx skills add mbs-community/skills-mbs@value-proposition-canvas

# Instala globalmente na máquina (todas as sessões)
npx skills add mbs-community/skills-mbs -g
```

Não precisa clonar nada — o comando busca direto do GitHub e coloca os arquivos em `.claude/skills/`, `.cursor/`, etc., conforme o agente detectado.

---

## 🛠️ Instalação manual (alternativa)

### Claude Code (CLI)

```bash
git clone https://github.com/mbs-community/skills-mbs.git

# no projeto atual (versiona junto com o seu repo)
mkdir -p .claude/skills
cp -R skills-mbs/skills/value-proposition-canvas .claude/skills/

# OU para todas as suas sessões (perfil do usuário)
mkdir -p ~/.claude/skills
cp -R skills-mbs/skills/value-proposition-canvas ~/.claude/skills/
```

Reinicie a sessão e rode `/skills` para conferir. A partir daí é automático: quando você pedir algo que bate com a `description` (ex: _"me ajuda a montar a proposta de valor da minha healthtech"_), o agente carrega a skill sozinho. Também dá pra chamar manualmente: `/value-proposition-canvas`.

### Claude.ai / App (Desktop e Web)

1. Compacte a pasta da skill em um arquivo `.skill` (que é só um `.zip`):

   ```bash
   cd skills/value-proposition-canvas
   zip -r ../../value-proposition-canvas.skill .
   ```

2. No Claude.ai: **Settings → Capabilities → Skills → Upload skill** e selecione o `.skill`. (Requer o recurso de Skills no seu plano.)

---

## 🧩 Como uma skill é organizada

```text
skills/
└── nome-da-skill/
    ├── SKILL.md            # obrigatório: frontmatter + instruções principais
    └── references/         # opcional: material de apoio, lido só quando necessário
        ├── framework.md
        ├── exemplos.md
        └── template.html
```

O `SKILL.md` sempre começa com um frontmatter YAML que o `npx skills` (e o agente) leem para saber quando usar a skill:

```yaml
---
name: nome-da-skill          # kebab-case, idêntico ao nome da pasta
description: Quando o agente deve usar esta skill e o que ela faz. Seja específico — é isso que dispara o carregamento automático.
---

# Instruções da skill em Markdown...
```

Arquivos dentro de `references/` não são lidos de cara: o `SKILL.md` aponta para eles (_"ver `references/framework.md`"_) e o agente só abre quando precisa. Isso mantém o contexto enxuto.

---

## 🤝 Como contribuir

Leia o guia completo em [CONTRIBUTING.md](./CONTRIBUTING.md). Em resumo:

1. Gere o esqueleto com `npx skills init nome-da-sua-skill` (ou crie a pasta na mão em `skills/`).
2. `name` no frontmatter tem que ser **igual** ao nome da pasta (kebab-case, sem espaços).
3. Escreva uma `description` específica — ela é o que faz o agente decidir usar (ou não) a skill.
4. Coloque exemplos longos, templates e tabelas de referência em `references/`, não no `SKILL.md`.
5. Adicione uma linha no catálogo acima.
6. Abra um Pull Request contra a `main`. Depois do merge, `npx skills add mbs-community/skills-mbs@sua-skill` já funciona para todo mundo.

---

## 📄 Licença

Salvo indicação em contrário na própria skill, o conteúdo deste repositório é disponibilizado para uso livre pela comunidade MBS.
