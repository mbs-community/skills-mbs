# Skills

Coleção pública de [Agent Skills](https://docs.claude.com/en/docs/claude-code/skills) da comunidade MBS / COMUNYTTI.

Cada skill vive em sua própria pasta, com um `SKILL.md` na raiz e, opcionalmente, uma pasta `references/` com material de apoio.

## Skills disponíveis

| Skill | O que faz |
|-------|-----------|
| [`value-proposition-canvas`](./value-proposition-canvas) | Conduz o preenchimento guiado de um Value Proposition Canvas (Canvas da Proposta de Valor), bloco por bloco, e gera o artefato visual final. Exemplos voltados para founders da área de saúde. |

## Estrutura de uma skill

```
nome-da-skill/
├── SKILL.md            # frontmatter (name + description) + instruções
└── references/         # opcional: arquivos carregados sob demanda
    └── ...
```

O `SKILL.md` começa com um frontmatter YAML:

```yaml
---
name: nome-da-skill          # kebab-case, igual ao nome da pasta
description: Quando usar esta skill e o que ela faz.
---
```

## Como instalar

**Claude Code** — copie a pasta da skill para um dos diretórios de skills:

```bash
# projeto (compartilhada via git no seu repo)
mkdir -p .claude/skills
cp -R value-proposition-canvas .claude/skills/

# ou pessoal (todas as sessões)
cp -R value-proposition-canvas ~/.claude/skills/
```

**Claude.ai / app** — empacote a pasta como `.skill` (um zip) e faça upload em Settings → Capabilities → Skills:

```bash
cd value-proposition-canvas && zip -r ../value-proposition-canvas.skill . && cd ..
```

## Contribuindo

1. Crie uma pasta `sua-skill/` na raiz com um `SKILL.md`.
2. `name` no frontmatter deve ser igual ao nome da pasta (kebab-case).
3. Adicione uma linha na tabela acima.
4. Abra um PR.
