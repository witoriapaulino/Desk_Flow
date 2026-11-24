# Regras de contribuição (IC-GC-03, v1.2)

Responsável: Anna Witória Paulino (Gerente de Configuração), conforme a RFC-004

## 1. Branches (gitflow)
A equipe usa **gitflow** em todo envio, sem exceção:

| Branch | Sai de | Volta para | Para quê |
|---|---|---|---|
| `main` | — | — | Versão entregue. Só recebe `release/*` e `hotfix/*`. Cada baseline e cada release vira tag aqui. |
| `develop` | `main` | — | Integração do que está pronto para a próxima release. |
| `feature/<integrante>-<assunto>` | `develop` | `develop` | Uma tarefa (requisito, documento ou IC). Ex.: `feature/alexandre-schilli-rtm-v2` |
| `release/<versão>` | `develop` | `main` e `develop` | Fechar uma entrega ou release. Ex.: `release/entrega-3`, `release/1.1.0` |
| `hotfix/<assunto>` | `main` | `main` e `develop` | Correção urgente do que já está na `main`. Ex.: `hotfix/gitflow-codeowners` |

- Cada integrante cria a sua branch **na própria conta** e com o próprio nome no prefixo `feature/`.
- Ninguém commita direto na `main` nem na `develop`: o GitHub bloqueia.
- **Nenhuma branch é apagada** depois do merge (nem `feature/*`, `release/*` ou `hotfix/*`): elas ficam como histórico para a auditoria. O GitHub também bloqueia a exclusão.
- As branches antigas por integrante (`anna-witoria` e as demais) ficam como histórico das Entregas 1 e 2.
- Para começar uma tarefa:
  ```bash
  git checkout develop && git pull
  git checkout -b feature/<seu-nome>-<assunto>
  ```

## 2. Commits
- Cada integrante commita **da própria conta do GitHub**, com o próprio nome e e-mail configurados no Git.
- Padrão da mensagem: `tipo(escopo): descrição curta`
  - `docs(plano): inclui cronograma v0.2`
  - `docs(gc): atualiza status do IC-DOC-03`
  - `feat(RF01): abre chamado`
  - `test(RF03): valida cálculo de SLA`
  - `ci: adiciona Newman ao pipeline`
- Um assunto por commit.

## 3. Pull Requests e revisão (mais de um code owner)
- Todo commit chega à `main` ou à `develop` **só por Pull Request**. Isso vale para feature, release, hotfix e merge de volta (`main` → `develop`).
- Título igual ao commit principal; a descrição segue o modelo `.github/pull_request_template.md` e cita os ICs alterados (ex.: `IC-DOC-01 v0.2 → v0.3`).
- **Todos os integrantes são code owners** (`.github/CODEOWNERS`). A regra de proteção da `main` e da `develop` exige:
  - **pelo menos 2 aprovações** (Approve) de code owners; quem abriu o PR não conta;
  - nova aprovação se entrar um commit depois das aprovações;
  - todas as conversas resolvidas;
  - CI verde (**Build, testes e Newman**), com a branch atualizada;
  - merge só com **Create a merge commit** (sem squash e sem rebase).
- Quem abre o PR adiciona os outros 4 integrantes em **Reviewers**. Cada um confere em **Files changed → Review changes**: **Approve** se está certo, **Request changes** com comentário se algo está errado.
- O que conferir: o conteúdo, a versão no **Histórico de Revisões** e a linha do IC na **Planilha de Controle de ICs**.
- PR que muda IC em baseline precisa também dos **4 votos Aprovo do CCB**, registrados no PCM. A Gerente de Configuração confere os votos antes do merge.
- Com as aprovações e a CI verde, a Gerente de Configuração faz o merge. Ninguém tem permissão para pular a regra, nem a dona do repositório.
- Se mudar um documento, atualize também a **versão na Planilha de Controle de ICs** e o **Histórico de Revisões** do documento.

## 4. Arquivos .docx e .xlsx
São binários: o Git não consegue juntar duas edições ao mesmo tempo. **Uma pessoa por vez** altera cada documento, na ordem combinada no grupo. Antes de editar, faça `git pull` na `develop` e crie a sua `feature/`.

## 5. Mudanças após baseline
Depois que um IC entra em baseline (BL-REQ-S1, BL-IMPL-S2, BL-REL-S3), qualquer alteração segue o PCM:
**RFC → Triagem → Análise → Aprovação do CCB → Planejamento → Validação → Encerramento**, registrado nos formulários em `pcm/`.
