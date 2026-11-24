<!-- Título do PR = mensagem do commit principal: tipo(escopo): descrição -->

## Tipo de branch (gitflow)
- [ ] `feature/<integrante>-<assunto>` → `develop`
- [ ] `release/<versão>` → `main` (e depois `main` → `develop`)
- [ ] `hotfix/<assunto>` → `main` e `develop`

## Itens de configuração alterados
<!-- Ex.: IC-DOC-01 v2.1 → v2.2 · IC-GC-01 v1.4 → v1.5 -->

## RFC
<!-- RFC-00X, se o PR muda um IC que já está em baseline. Senão, escreva "não se aplica". -->

## Conferência de quem revisa
- [ ] Conteúdo correto e coerente com o Documento de Requisitos e a ERS
- [ ] Versão nova no Histórico de Revisões do documento
- [ ] Linha do IC atualizada na Planilha de Controle de ICs
- [ ] CI verde (Build, testes e Newman)

Regra: pelo menos 2 aprovações de code owners. Quem abriu o PR não aprova o próprio PR.
Mudança em IC em baseline: também 4 votos Aprovo do CCB, registrados no PCM.
