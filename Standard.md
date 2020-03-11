Esta proposta de standard não visa ser uma restrição, mas sim um consenso evolutivo e colaborativo entre a equipe, com objetivo de que se alcance um ambiente e uma code base harmônica, de fácil evolução, e de fácil manutenção por toda a equipe, assim como facilitar a integração de novos membros.

As entregas, a qualidade das mesmas, as correções, os prazos e a UX são muito, muito importantes, porém menos explícito e tão importantes quanto, são a manutenabilidade do código escrito assim como a facilidade de compreensão e evolução por outros membros da equipe futuramente (ou por você mesmo). 

### Code standards

Quanto a um padrão de estilo de codificação (Code Style Guide), buscamos seguir o padrão do rbnb, que é uma versão dos standards javascripts mais adotados no mercado e otimizados para se trabalhar com React e JS moderno.

Referencia ao style guide: https://github.com/airbnb/javascript

Porém não é necessário decorarmos o style guide do rbnb, é interessante dar uma olhada, mas as principais ferramentas de lint do mercado já possuem este (e elguns outros padrões), bastando configurá-la para que ela notifique sempre que alguma parte do código estiver em desacordo com este padrão, assim como mostrar uma explicação e a correção indicada.

Também sempre buscamos melhorar este padrão, em consenso, ajustando o eslint em algumas regras para que se encaixe melhor em nosso projeto e ambiente, estes ajustes sendo salvos no arquivo eslintrc já estarão disponíveis para todos do projeto. 

Dicas para facilitar o processo de verificação de estilo:
- Utilizar a ferramenta ESLint para ser notificado sobre quebras de padrões, assim como as correções
- Utilizar Prettier para auto formatar ao salvar, para questões de identação, espaços por tabs, posicionamentos de chaves, entre outros pormenores que por vezes passam batidos por nós.
- Compartilhar configurações do VS Code para padronização do código

Há neste repositório os arquivos de configuração do ESLint, Prettier e configurações default do VS Code para a base de novos projetos.

(Duas particularidades atuais nossas que divergem do padrão "rbnb" são: Utilizamos atualmente functional components e hooks como padrão, diferente da postura adotada pelo rbnb, pois sentimos que functional components e hooks são mais produtivos. Também optamos adotar CSS as a Module com SASS nos projetos de maior importância, quando na especificação do rbnb definem como default CSS-in-JS.)


### Modelo de estilização (CSS)

Utilizar SASS nas apps principais (CSS as a module, utilizando node-sass, já configurados no projeto).
-	Cores: O mais indicado é não definir cores dentro de seletores CSS, mas sim usar arquivos de variáveis através das features do SASS, sejam estes globais ou do escopo do componente, caso sejam globais deverão ser definidas junto as demais variáveis globais, caso não sejão deveram ser definidas em variáveis em arquivos no próprio diretório do componente em questão.
-	Estilos: Os estilos globais assim como as variáveis globais deverão ser definidos no diretório global, porém os estilos e variáveis referentes a determinados componentes ou seus filhos, devem estar exclusivamente no diretório do próprio componente, para facilitar a manutenção e reaproveitamento de códigos e componentes.

### React
-   Ferramentas preferíveis
	-	Axios para requisições a apis
	-	Redux para estados compartilhados entre componentes
	-	NPM para gerenciamento de pacotes
-   Tipo de componentes preferível
	-	É preferível a utilização de functional components e hooks
-   States
	-	Utilizar o mínimo de estados compartilhados entre componentes "distantes" para não aumentar a complexidade desnecessáriamente.
	-	Ao tratar formulário é preferível utilizar componentes controlados. Utilizar componentes não controlados apenas em casos extremos ou de benefício substancial seja em performance ou em diminuição da complexidade dos comportamentos do form. (Referncia: https://pt-br.reactjs.org/docs/forms.html)
-   fluxo de dados
	-	No momento não estamos utilizando um padrão como MVVM, MVP ou MVP para manter a baixa complexidade. Estamos seguindo um MV, na maior parte dos casos o próprio componente da página sendo responsável por suas interações com o back-end, seu estados e seus processos, podendo ser quebrado em um Controller-View quando a complexidade da página ou componente comprometer sua evolução e manutenção.  

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


Próximas sessões: 
- Estrutura de arquivos, explicando a idéia e os motivos para cada uma)
- Testes unitários e de UI

- questões de temas, herdar de arquivos centrais
