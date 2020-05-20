<img src="https://static.imasters.com.br/wp-content/uploads/2015/04/git-workflow-release-cycle-4maintenance.png" width="450" />

- Branchs de Master (Prod), Homolog e Development.
- Só vai para a master o que acabou de ir para produção
- Ao finalizar e fechar versão de release criar um release/*

release/* -> deploy -> master

feature/*
Feature
- 1 - Puxa uma branch da master com feature/*
- 2 - Commits funcionais / Push a todo commit
- 2.1 - Fazer vários testes aqui (dev) 
- 3 - Encerrou faz um PR para a Development
- 3.1 - Alguém precisa aprovar este PR por code review
- 4.1 - Gerar homologação para testes da nova feature, testes de QA e End to End
- 5 - Quando for gerar corte/release pega o deve  abre um branch de release/**
- 5.1 - estando na loja mergea na master, colocar tag.

hotfix/*
HotFix:
- 1 - Puxa o branch da master hotfix/**
- 2 - Feita a correção rodar testes aqui
- 3 - caso precise já subir em prod novamente, versionamento 0.1.x
- 3.1 - Testes de QA e end to end aqui (para release)
- 3.2 - tagear e deploy da hotfix - feito o deploy mergear com a Master
- 4 - Mergear este hotfix na development
- 4.1 - Testes de QA e end to end aqui (release)

---

Referencias:

https://imasters.com.br/agile/fluxo-de-desenvolvimento-com-gitflow

https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow

