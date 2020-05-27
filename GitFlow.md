<img src="https://static.imasters.com.br/wp-content/uploads/2015/04/git-workflow-release-cycle-4maintenance.png" width="450" />

- Branchs de Master (espelho de Prod), Release (espelho de homologação) e Develop (de onde puxaremos os branchs).
- Só vai para a master quando já vai para prod, sempre será um espelho do prod
- Ao finalizar e fechar uma versão no develop, mergear no branch Release e vai para homologação / QA
- Ao passar pela aprovação de homologação, é mergeado na master e é feito o deploy
- Nunca dar push direto na master, release ou develop (somente pull requests)
- A branch de feature sempre sai da develop, apenas em caso de bug/hotfix o branche será gerado a partir da master/prod 

Feature
feature/*
- 1 - Puxa uma branch da develop com feature/*
- 2 - Commits funcionais, comitar steps, código rodando, evitar commitar "work in progress" / preferencial push a todo commit e commit a todo step
- 3 - Encerrou e testou bem faz um PR para a Development
- 3.1 - Avisar squad que entrou PR (Code review não será obrigatório, não precisará de aprovação, mas sempre se iterar das features entregues e dos códigos mergeados entre a equipe)

hotfix/*
HotFix:
- 1 - Puxa o branch da master/prod com nome hotfix/**
- 2 - Feita a correção rodar testes, testes end to end
- 3 - Solicitar equipe de QA aqui
- 4 - Esta correção deverá ser imediatamente, após aprovada mergeada na brach dev e na brach master/prod (será efetuado o deploy aqui)

---

Referencias:

https://imasters.com.br/agile/fluxo-de-desenvolvimento-com-gitflow

https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow

