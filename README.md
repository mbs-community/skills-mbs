# MBS Skills Hub 🚀

Repositório central de **skills** (Agent Skills) da comunidade **MBS / COMUNYTTI**.

Uma _skill_ é uma pasta com instruções que ensinam o Claude a executar uma tarefa específica de um jeito consistente — um framework de consultoria, um checklist, um fluxo repetível. O Claude carrega a skill sozinho quando a conversa combina com a `description` dela.

---

## 📚 Catálogo de Skills

| Skill | Categoria | Descrição | Link |
| :--- | :--- | :--- | :--- |
| `value-proposition-canvas` | Estratégia / Negócios | Conduz o preenchimento guiado de um **Value Proposition Canvas** (Canvas da Proposta de Valor) bloco a bloco — contexto → Perfil do Cliente (Tarefas, Dores, Ganhos) → Mapa de Valor (Produtos, Analgésicos, Criadores de Ganho) → teste de fit → checklist de erros comuns → artefato visual final em HTML. Exemplos voltados ao universo de saúde/founders. | [Ver skill](./value-proposition-canvas) |

---

## 🧩 Como uma skill é organizada

```
nome-da-skill/
├── SKILL.md            # obrigatório: frontmatter + instruções principais
└── references/         # opcional: material de apoio, carregado só quando necessário
    ├── framework.md
    ├── exemplos.md
    └── template.html
```

O `SKILL.md` sempre começa com um frontmatter YAML:

```yaml
---
name: nome-da-skill          # kebab-case, idêntico ao nome da pasta
description: Quando o Claude deve usar esta skill e o que ela faz. Seja específico — é isso que dispara o carregamento automático.
---

# Instruções da skill em Markdown...
```

Arquivos dentro de `references/` não são lidos de cara: o `SKILL.md` aponta para eles (ex: _"ver `references/framework.md`"_) e o Claude só abre quando precisa. Isso mantém o contexto enxuto.

---

## ⚙️ Como instalar

### Claude Code (CLI)

Copie a pasta da skill para um dos diretórios que o Claude Code reconhece:

```bash
# 1. clone este repositório
git clone https://github.com/mbs-community/skills-mbs.git
cd skills-mbs

# 2a. instalar só no projeto atual (fica versionada junto com o seu repo)
mkdir -p .claude/skills
cp -R value-proposition-canvas .claude/skills/

# 2b. OU instalar para todas as suas sessões (perfil do usuário)
mkdir -p ~/.claude/skills
cp -R value-proposition-canvas ~/.claude/skills/
```

Reinicie a sessão do Claude Code. Confirme que a skill apareceu com:

```
/skills
```

A partir daí é automático: quando você pedir algo que bata com a `description` (ex: _"me ajuda a montar a proposta de valor da minha healthtech"_), o Claude carrega a skill sozinho. Dá pra chamar manualmente também: `/value-proposition-canvas`.

### Claude.ai / App (Desktop e Web)

1. Compacte a pasta da skill em um arquivo `.skill` (que é só um `.zip`):

   ```bash
   cd value-proposition-canvas
   zip -r ../value-proposition-canvas.skill .
   cd ..
   ```

2. No Claude.ai, vá em **Settings → Capabilities → Skills → Upload skill** e selecione o `.skill`.

> É preciso ter o recurso de Skills habilitado no seu plano (Pro / Team / Enterprise).

### Claude Agent SDK

Aponte o `settingSources` / diretório de skills do seu agente para a pasta da skill, ou copie para `~/.claude/skills/`. Detalhes na [documentação do SDK](https://docs.claude.com/en/api/agent-sdk/overview).

---

## 🤝 Como contribuir

Leia o guia completo em [CONTRIBUTING.md](./CONTRIBUTING.md). Em resumo:

1. Crie uma pasta `sua-skill/` na raiz do repositório com um `SKILL.md`.
2. `name` no frontmatter tem que ser **igual** ao nome da pasta (kebab-case, sem espaços).
3. Escreva uma `description` específica — ela é o que faz o Claude decidir usar (ou não) a skill.
4. Coloque exemplos longos, templates e tabelas de referência em `references/`, não no `SKILL.md`.
5. Adicione uma linha no catálogo acima.
6. Abra um Pull Request.

---

## 📄 Licença

Salvo indicação em contrário na própria skill, o conteúdo deste repositório é disponibilizado para uso livre pela comunidade MBS.
