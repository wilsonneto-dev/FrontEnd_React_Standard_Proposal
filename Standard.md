Esta proposta de standard não visa ser uma restrição, mas sim um consenso evolutivo e colaborativo entre a equipe, com objetivo de que se alcance um código harmonico, de fácil evolução e manutenção por toda a equipe, assim como facilitar a integração de novos membros.

### Code standards

Quanto a Code Style Guide, seguimos o padrão Rbnb, que é uma versão dos standards javascripts mais adotados no mercado e otimizados para trabalhar com React e JS moderno.

Link de referencia: https://github.com/airbnb/javascript

- Utilizar ESLint para assegurar os padrões
- Utilizar Prettier para auto formatar os documentos
- Compartilhar configurações do VS Code para padronização do código

Há neste repositório os arquivos de configuração do ESLint, Prettier e configurações default do VS Code.

### Modelo de estilização (CSS)

Utilizar SASS nas apps principais (CSS as module, node-sass).

### React
-   Ferramentas preferíveis
	-	Axios para requisições a apis
	-	Redux para estados compartilhados entre componentes
	-	NPM para gerenciamento de pacotes
-   Tipos de componentes preferíveis
	-	É preferível a utilização de functional components e hooks
-   States
	-	Utilizar o mínimo de estado compartilhado para diminuir a complexidade
	-	Ao tratar formulário é preferível utilizar componentes controlados. Utilizar componentes não controlados apenas em casos extremos. (Referncia: https://pt-br.reactjs.org/docs/forms.html)
-   fluxo de dados
No momento não estamos utilizando um padrão como MVVM, MVP ou MVP para manter a baixa complexidade. Estamos seguindo um MV, na maior parte dos casos o próprio componente da página sendo responsável por suas interações com o back-end, seu estados e seus processos, podendo ser quebrado em um Controller-View quando a complexidade da página ou componente comprometer sua evolução e manutenção.  

### Versionamento
-   git flow
	-	Buscamos utilizar uma estrutura simplificada baseada no gitflow, onde contamos com dois branchs principais, o master, que busca sempre ser uma cópia fiel a aplicação que está em produção, e o branch dev, que é o branch das features e hotfixes que estão sob desenvolvimento, buscamos nunca mergear ou commitar alterações que fação com que o sistema na branch master fique "quebrado".
		-	Master: Fiel a codebase de produção
		-	Dev: Branch de desnvolvimento
		-	Branchs de features, correções de bugs e hotfixes: Criar um branch para determinadas demandas para após sua conclusão mergear ao branch develop para homologação e testes
-   Commits e mensagens
	-	Buscar nunca commitar alterações que quebrem o sistema
	-	Buscar sempre deixar mensagens sucintas porém explicativas sobre seus commits
	-	Commitar pequenos passos, e procurar separar os commits por contextos
	-	Um padrão de mensagem que buscamos usar e manter é o commit lint (https://github.com/conventional-changelog/commitlint), uma ferramenta que ajuda a mater o padrão é o commitzen (package JS), no qual ao digitarmos ```npx git-cz``` ele irá perguntar alguns pontos e gerar um commit com uma mensagem padronizada (seguindo o padrão commit lint).  


(Próxima sessão: Estrutura de arquivos, explicando a idéia e os motivos para cada uma)
