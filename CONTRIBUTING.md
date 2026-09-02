# Contribuindo com uma skill

Obrigado por querer contribuir com o **MBS Skills Hub**. Este guia explica como estruturar e enviar uma skill.

## 1. O que é uma boa skill

Uma skill vale a pena quando:

- Existe um jeito **certo e repetível** de fazer aquilo (um framework, um checklist, um formato de saída padrão).
- Você se pega explicando as mesmas regras para o Claude toda vez.
- O resultado melhora de forma consistente quando essas regras são seguidas.

Não vale a pena para tarefas triviais, que o Claude já faz bem sem instrução, ou que mudam completamente a cada uso.

## 2. Estrutura de pastas

Toda skill vive em `skills/<nome>/`, com o nome em `kebab-case`. Gere o esqueleto com:

```bash
npx skills init minha-skill
```

ou crie na mão:

```
skills/
└── minha-skill/
    ├── SKILL.md            # obrigatório
    └── references/         # opcional
        ├── framework.md
        ├── exemplos.md
        └── template.html
```

- **`SKILL.md`** — frontmatter + as instruções principais. Alvo: menos de ~500 linhas. Se passar muito disso, mova detalhe para `references/`.
- **`references/`** — material consultado sob demanda: explicações longas, bancos de exemplo, templates, checklists extensos. O Claude só abre esses arquivos quando o `SKILL.md` manda.

## 3. O `SKILL.md`

### Frontmatter (obrigatório)

```yaml
---
name: minha-skill
description: Use esta skill quando o usuário quiser [tarefa X], incluindo pedidos como "[exemplo 1]", "[exemplo 2]" ou qualquer menção a [termos-gatilho]. Também dispare proativamente quando [situação].
---
```

Regras:

| Campo | Regra |
| :--- | :--- |
| `name` | `kebab-case`, **idêntico ao nome da pasta**. Só letras minúsculas, números e hífen. É o que vai depois do `@` em `npx skills add mbs-community/skills-mbs@<name>`. |
| `description` | Máx. ~1024 caracteres. Escreva na terceira pessoa. Diga **quando** usar e **o que faz**. Inclua frases-gatilho reais que um usuário diria. É o único texto que o agente vê antes de decidir carregar a skill — capriche. |

### Corpo

Markdown livre. Recomendações:

- Comece com um parágrafo curto do que a skill faz.
- Use passos numerados quando a ordem importa.
- Referencie os arquivos de apoio pelo caminho relativo: _"ver `references/framework.md`"_.
- Deixe explícito o **formato de saída** esperado (texto, tabela, artefato HTML, etc.).
- Evite depender de caminhos ou ferramentas específicas de um único ambiente. Se a skill gera arquivos, descreva o resultado de forma neutra em vez de fixar um diretório de um ambiente só.

## 4. Teste antes de enviar

1. Copie `skills/minha-skill/` para `~/.claude/skills/` (ou `.claude/skills/` de um projeto).
2. Reinicie o Claude Code e rode `/skills` para confirmar que aparece sem erro.
3. Faça um pedido que **deveria** disparar a skill e confirme que ela carrega sozinha.
4. Faça um pedido próximo mas fora do escopo e confirme que ela **não** dispara indevidamente.
5. Rode o fluxo completo pelo menos uma vez e verifique a saída.

## 5. Abrindo o Pull Request

1. Fork + branch: `git checkout -b add-minha-skill`.
2. Adicione a pasta em `skills/minha-skill/`.
3. Adicione uma linha no catálogo do [README.md](./README.md).
4. Commit e PR contra a `main`. Depois do merge, `npx skills add mbs-community/skills-mbs@minha-skill` já funciona para todo mundo.

No PR, descreva:

- O que a skill faz e para quem.
- Um exemplo de pedido que a dispara.
- Como você testou.

## 6. Checklist rápido

- [ ] Pasta em `skills/<nome>/` com nome em `kebab-case`
- [ ] `SKILL.md` com frontmatter `name` + `description`
- [ ] `name` igual ao nome da pasta
- [ ] `description` específica, com frases-gatilho
- [ ] Conteúdo longo movido para `references/`
- [ ] Testada localmente (dispara quando deve, não dispara quando não deve)
- [ ] Linha adicionada no catálogo do README
- [ ] Sem segredos, tokens ou dados de cliente nos arquivos
