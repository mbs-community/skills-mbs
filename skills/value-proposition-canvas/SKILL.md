---
name: value-proposition-canvas
description: Use this skill whenever the user wants to build, preencher, revisar, or discutir a Value Proposition Canvas (Canvas da Proposta de Valor) for a project, startup, produto, serviço, or negócio — including requests like "me ajuda a montar a proposta de valor", "quais são nossos diferenciais frente aos concorrentes", "qual a dor que meu produto resolve", "monta o perfil do cliente", or any mention of Jobs-to-be-Done, dores, ganhos, analgésicos, criadores de ganho, ICP + proposta de valor, or "fit" entre produto e cliente. Also trigger this proactively whenever the user is helping someone define what makes their product/startup different from competitors, even if they don't name the canvas explicitly. The user runs consultoria/mentoria for founders in the health/medical space (saúde), so default all examples to that domain unless told otherwise.
---

# Value Proposition Canvas — Guia de Preenchimento Guiado

Skill para conduzir o preenchimento de um Value Proposition Canvas (Canvas da Proposta de Valor) do zero, de forma conversacional — pergunta o contexto, depois guia bloco por bloco na ordem correta, aplicando as boas práticas e evitando os erros mais comuns do framework.

O usuário é consultor/mentor de founders da área de saúde (médicos, healthtechs, clínicas, cursos/educação médica). **Por padrão, todos os exemplos, analogias e linguagem devem vir do universo médico/saúde**, a menos que o projeto em questão seja explicitamente de outra área.

## O que é o Value Proposition Canvas (contexto para você, Claude)

Framework de Alexander Osterwalder / Strategyzer, complementar ao Business Model Canvas. Faz um "zoom" em dois blocos: Proposta de Valor e Segmentos de Cliente. Tem dois lados:

- **Perfil do Cliente** (círculo) — o que **se observa**. Tarefas, Dores, Ganhos. Nada aqui está sob controle da empresa.
- **Mapa de Valor** (quadrado) — o que **se desenha**. Produtos/Serviços, Analgésicos, Criadores de Ganho. Tudo aqui é decisão de design.

O objetivo é o **fit**: cada elemento do mapa de valor precisa apontar para uma dor ou ganho específico e priorizado do perfil do cliente. Ver `references/framework.md` para a explicação completa de cada bloco, com exemplos de saúde.

## Fluxo de condução (siga esta ordem sempre)

### Passo 0 — Pergunte o contexto primeiro, sempre

Nunca comece preenchendo o canvas sem entender o projeto. Pergunte (pode ser via `ask_user_input_v0` se fizer sentido, ou só em texto):

1. **O que é o produto/serviço/negócio?** (uma frase)
2. **Quem é o cliente-alvo?** (se ele já tem um ICP definido, ótimo — se não, ajude a esboçar rapidamente antes de seguir; ver nota abaixo)
3. **Já existe alguma pesquisa/discovery feito com clientes reais**, ou o canvas vai ser preenchido como hipótese inicial? (isso muda o nível de confiança que você deve comunicar nas respostas — hipótese não validada precisa ser marcada como tal)
4. **Quem são os concorrentes ou alternativas** que esse cliente usa hoje? (mesmo que seja "planilha + WhatsApp" ou "não fazer nada")

Se o usuário já trouxe isso tudo na mensagem inicial (comum, já que ele geralmente já tem o projeto em mente), não precisa perguntar de novo — extraia o que puder e só pergunte o que faltar. **Não trave o fluxo pedindo tudo perfeito** — com o mínimo (o que é + quem é o cliente) já dá pra começar, e ir refinando.

**Nota sobre segmento único:** um canvas cobre **um único segmento de cliente por vez**. Se o projeto tem múltiplos personas relevantes (ex: uma healthtech que vende para médicos E para pacientes), avise isso logo no início e sugira fazer um canvas separado para cada — nunca misture as dores/ganhos de personas diferentes num mesmo canvas.

### Passo 1 — Perfil do Cliente (lado direito, sempre primeiro)

Preencha nesta ordem: **Tarefas → Dores → Ganhos**. Regra de ouro: este lado **se observa, não se inventa** — se o usuário estiver puramente especulando (sem discovery/entrevistas), sinalize isso explicitamente ("essa é uma hipótese — vale validar com conversas reais antes de apostar tudo nela").

**Sempre que sinalizar uma hipótese não validada, sugira também 1-2 formas concretas de validar aquela tarefa/dor/ganho específica**, adaptadas ao contexto de saúde — não apenas apontar que é hipótese e seguir em frente. Exemplos de método (escolha o mais adequado ao caso, não liste todos sempre):
- Entrevista estruturada com 5-8 clientes reais do segmento (roteiro aberto, sem citar a solução)
- Observação/sombra de um dia de trabalho real (ex: acompanhar um plantão, uma consulta, a rotina de um gestor de clínica)
- Análise de reclamações/tickets de suporte, avaliações ou grupos de WhatsApp/fóruns da categoria
- Levantamento de dados objetivos já existentes (taxa de glosa, tempo médio de espera, turnover, etc.) quando a dor é operacional
- Teste com MVP simples ou piloto pago pequeno, se já houver uma hipótese de solução a testar
- Conversa com quem já perdeu esse cliente/usuário para entender o motivo (churn)

Se o usuário já tiver discovery real feito, não force a sugestão de validação — só confirme a fonte (quantas entrevistas, quando, com quem) antes de aceitar como fato.

Para cada bloco, ver o detalhamento completo com perguntas-gatilho e exemplos de saúde em `references/framework.md`. Resumo:

- **Tarefas**: puxe as 3 dimensões (funcional, emocional, social) + a circunstância/gatilho que torna a tarefa urgente. Pergunta-chave: "o que ele está tentando fazer progredir na vida dele, e o que dispara essa urgência agora?"
- **Dores**: obstáculos, riscos, frustrações/ansiedades no caminho da tarefa.
- **Ganhos**: esperados, desejados, inesperados.

No fim, **ajude a ranquear**: peça (ou sugira) o top 3 de dores por gravidade e top 3 de ganhos por relevância. Essa priorização é o que vai guiar o lado esquerdo.

### Passo 2 — Mapa de Valor (lado esquerdo)

Só comece depois do perfil estar minimamente ranqueado. Ordem: **Produtos/Serviços → Analgésicos → Criadores de Ganho**.

- **Produtos e Serviços**: substantivos concretos, não promessas vagas.
- **Analgésicos**: cada um precisa apontar para uma dor específica do top 3 — force o usuário a nomear qual dor cada analgésico ataca.
- **Criadores de Ganho**: idem, mas para os ganhos do top 3, incluindo emocionais/sociais.

**Sempre force a conexão explícita** (a "seta"): ao sugerir um analgésico ou criador de ganho, pergunte ou declare junto "isso resolve a dor X" / "isso cria o ganho Y". Se não conseguir ligar a nenhuma dor/ganho do top 3, sinalize como possível **feature órfã** (ver checklist de erros abaixo) — não descarte automaticamente, mas questione se vale manter no canvas nessa fase.

### Passo 3 — Teste de Fit

Depois dos dois lados preenchidos:

1. Percorra cada analgésico e criador de ganho e confirme a seta para o perfil.
2. Risque (ou marque para reavaliação) qualquer feature órfã.
3. Monte o **pitch de uma frase**:
   > "Nós ajudamos [ICP] que precisa [tarefa] a [aliviar a dor nº1] e [criar o ganho nº1] por meio de [produto/serviço]."
4. Pergunte: isso é fit **no papel** (hipótese coerente) ou já existe evidência de fit **no mercado** (piloto pago, carta de intenção, renovação)? Deixe claro que elogio/feedback positivo em conversa não conta como validação — só compromisso real.

### Passo 4 — Checklist de erros comuns (rode isso antes de fechar)

Percorra esta lista com o usuário no fim de cada canvas — ela cobre tanto o material original da MBS quanto os pontos adicionais da pesquisa Strategyzer. Detalhamento e exemplos em `references/erros-comuns.md`.

- [ ] Feature no lado direito (confundir produto com tarefa/dor do cliente)
- [ ] Perfil montado através das lentes da própria solução (em vez de observação real)
- [ ] Misturou mais de um segmento de cliente no mesmo canvas
- [ ] Só listou tarefas/dores funcionais, ignorou emocional e social
- [ ] Tentando aliviar todas as dores / criar todos os ganhos, sem ranquear
- [ ] Ganho genérico demais (ex: "qualidade de vida", "excelência") que serviria pra qualquer negócio
- [ ] Inventou dor pra justificar uma feature que já queria construir
- [ ] Analgésico/criador de ganho que quebra o modelo de negócio (destrói margem)
- [ ] "Fit de slide" — encaixe bonito sem nenhuma validação real com cliente
- [ ] Apelando pra caridade/altruísmo do cliente em vez de interesse próprio genuíno dele

### Passo 5 — Gerar o artefato visual do canvas

Gere esse artefato visual (não uma tabela markdown) sempre que:
- todos os blocos principais (Tarefas, Dores, Ganhos, Produtos/Serviços, Analgésicos, Criadores de Ganho) já tiverem conteúdo, mesmo que ainda como hipótese; **ou**
- o usuário pedir explicitamente pra ver o canvas ("mostra visualmente", "monta o artefato", "como está ficando", "quero levar isso pra reunião"), mesmo com o preenchimento parcial.

Não espere confirmação extra pra gerar — depois de reunir o conteúdo mínimo, gere o artefato direto. Se algum bloco ainda estiver vazio, gere assim mesmo e deixe o placeholder daquele item indicando "a definir" em vez de travar a entrega.

**Como gerar:**

1. Leia `references/artifact-template.html` — é um arquivo HTML completo, autocontido, no formato clássico do Value Proposition Canvas: um **quadrado dividido em 3 triângulos** (Mapa de Valor) ao lado de um **círculo dividido em 3 fatias** (Perfil do Cliente), nas cores da MBS (branco, navy, preto — sem dourado). Já vem com a logo MBS (canto superior direito do cabeçalho) e a foto do Cauê Gasparotto (rodapé, canto inferior esquerdo) embutidas como imagens em base64. **Não recrie esse HTML do zero, não mude o formato pra cards/tabela, e não gere novas imagens** — a marca, as fotos e a geometria do canvas já estão prontas nesse arquivo, é só preencher o texto.
2. O template tem placeholders entre colchetes. Como o espaço dentro de cada triângulo/fatia é limitado, **cada item deve ser curto — uma frase de até ~30-35 caracteres, não um parágrafo**. Se o conteúdo que você construiu com o usuário for mais longo, resuma pra caber. Lista completa de placeholders:
   - Cabeçalho: `[NOME_DO_PROJETO]`, `[UMA_LINHA_DESCREVENDO_O_QUE_E_O_PROJETO]`, `[NOME_DO_SEGMENTO_DE_CLIENTE]`
   - Triângulo esquerdo (Produtos e Serviços): `[PRODUTO_1]`, `[PRODUTO_2]`, `[PRODUTO_3]`
   - Triângulo de baixo (Analgésicos): `[ANALGESICO_1]` + `[DOR_1_RESOLVIDA]`, `[ANALGESICO_2]` + `[DOR_2_RESOLVIDA]` — só 2 analgésicos cabem no espaço; escolha os 2 mais fortes
   - Triângulo de cima (Criadores de Ganho): `[CRIADOR_GANHO_1]` + `[GANHO_1_CRIADO]`, `[CRIADOR_GANHO_2]` + `[GANHO_2_CRIADO]` — idem, só 2 cabem
   - Fatia direita (Tarefas do Cliente): `[TAREFA_FUNCIONAL]`, `[TAREFA_EMOCIONAL]`, `[TAREFA_SOCIAL]`
   - Fatia esquerda (Dores do Cliente): `[DOR_1]`, `[DOR_2]`, `[DOR_3]` — sempre o top 3 já ranqueado, aparecem numerados ①②③
   - Fatia de cima (Ganhos do Cliente): `[GANHO_1]`, `[GANHO_2]`, `[GANHO_3]` — top 3 ranqueado, numerados ①②③
   - Faixa de fit: nível de fit (no papel / no mercado) + observação curta sobre a evidência
   - Caixa de pitch: ICP, tarefa central, dor 1, ganho 1, produto principal
   - `[DATA_OU_SESSAO]` — data atual ou nome da sessão/projeto se o usuário mencionar
3. Só existem 2 vagas para Analgésicos e 2 para Criadores de Ganho (espaço físico do triângulo). Se o usuário tiver mais que isso, ajude a escolher os 2 mais fortes/conectados ao top 3 de dores e ganhos — não tente espremer mais itens no SVG.
4. Se algum placeholder não tiver conteúdo (ex: ainda não definiu a tarefa social), não deixe o colchete literal aparecendo — escreva algo como "a validar" ou remova a linha `<text>` correspondente.
5. Salve o HTML preenchido em `/mnt/user-data/outputs/` com um nome descritivo (ex: `canvas-[nome-do-projeto].html`) e use `present_files` pra entregar.
6. Depois de entregar, não repita o conteúdo do canvas em texto corrido — o artefato já é a entrega visual.

## Tom e formato das respostas

- Use exemplos do universo médico/saúde por padrão (residentes, plantonistas, gestores de clínica, pacientes crônicos, operadoras, glosas, prontuário, etc.) — ver banco de exemplos em `references/exemplos-saude.md`.
- Enquanto conduz a conversa (antes do artefato final), vá construindo o canvas em formato de lista estruturada conforme os blocos vão sendo preenchidos, não espere tudo pronto pra mostrar de uma vez — isso ajuda o usuário (e os founders que ele atende) a visualizar o progresso.
- Quando o usuário estiver satisfeito com um bloco, resuma o que foi preenchido antes de passar pro próximo, para manter o fio da meada.
- O artefato visual (Passo 5) é a entrega final — não é opcional, é o formato padrão de saída dessa skill.
