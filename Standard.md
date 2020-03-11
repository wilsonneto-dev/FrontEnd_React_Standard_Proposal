Esta proposta de standard não visa ser uma restrição, mas sim um consenso evolutivo e colaborativo entre a equipe, com objetivo de que se alcance um ambiente e uma code base harmônica, de fácil evolução, e de fácil manutenção por toda a equipe, assim como facilitar a integração de novos membros.

As entregas, a qualidade das mesmas, as correções, os prazos e a UX são muito, muito importantes, porém menos explícito e tão importantes quanto, são a manutenabilidade do código escrito assim como a facilidade de compreensão e evolução por outros membros da equipe futuramente (ou por você mesmo). 

### Code standards

Quanto a um padrão de estilo de codificação (Code Style Guide), buscamos seguir o padrão do rbnb, que é uma versão dos standards javascripts mais adotados no mercado e otimizados para se trabalhar com React e JS moderno.

Referencia ao style guide: https://github.com/airbnb/javascript

Porém não é necessário decorarmos o style guide do rbnb, é interessante dar uma olhada, mas as principais ferramentas de lint do mercado já possuem este (e elguns outros padrões), bastando configurá-las para que notifiquem sempre que alguma parte do código estiver em desacordo com este padrão, assim como mostrar uma explicação e a correção indicada.

Também sempre buscamos melhorar este padrão, em consenso, ajustando as regras do eslint em algumas para que se encaixe melhor em nosso projeto e ambiente, estes ajustes sendo salvos no arquivo eslintrc já estarão disponíveis para todos do projeto. 

Dicas para facilitar o processo de verificação de estilo:
- Utilizar a ferramenta ESLint para ser notificado sobre quebras de padrões, assim como as correções
- Utilizar Prettier para auto formatar ao salvar, para questões de identação, espaços por tabs, posicionamentos de chaves, entre outros pormenores que por vezes passam batidos por nós.
- Compartilhar configurações do VS Code, caso seja o editor adotado, para facilitar a padronização

Há neste repositório os arquivos de configuração do ESLint, Prettier e configurações default do VS Code para servir de base a novos projetos.

(Duas particularidades atuais nossas que divergem do padrão "rbnb" são: Utilizamos atualmente functional components e hooks como padrão, diferente da postura adotada pelo rbnb, pois sentimos que functional components e hooks são mais produtivos. Também optamos por adotar CSS as a Module com SASS nos projetos de maior importância, enquanto na especificação do rbnb é definido como default o CSS-in-JS, optamos por SASS com a intenção de não nos distanciarmos demais das tecnologias bases da web, neste caso do CSS default dos browsers, e também diminuir a curva de aprendizado.)


### Modelo de estilização (CSS)

Buscamos utilizar SASS nas apps principais (utilizando "CSS as a module", utilizando o loader node-sass do babel, já configurados no projeto atual e muito fácil e simples de adicionar em novos projetos que usem CRA - Create React App ou NextJS).
-	Cores: O mais indicado é não definir cores dentro de seletores CSS nos arquivos de estilos, mas sim usar arquivos de variáveis através das features do SASS, assim centralizando e facilitando a manutenção e evolução, sejam estas cores globais ou do escopo do componente, caso sejam globais deverão ser definidas junto as demais variáveis globais, caso não sejão deveram ser definidas em variáveis em arquivos no próprio diretório do componente em questão.
-	Estilos: Os estilos globais assim como as variáveis globais deverão ser definidos no diretório global, porém os estilos e variáveis referentes a determinados componentes ou seus filhos, devem estar exclusivamente no diretório do próprio componente, para facilitar a manutenção e otimizar a componentização e o reaproveitamento de códigos e componentes. No caso de 1 ou 2 arquivos de estilo é interessante deixá-los na raíz da pasta do componente, porém ao termos muitos arquivos de estilos é mais interessante colocá-los em uma pasta 'styles' dentro da pasta do componente.

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
-	Tipagem
	-	Não optamos por utilizar Typescript ou algum framework de tipagem nos projetos principais pois buscamos minimizar a complexidades e a curva de aprendizado, e também por acreditarmos que o typescript se encaixa em projetos com arquiteturas mais robustas como DDD, MVP ou MVC que lidem com domínios complexos onde se faz necessário tipagem forte, interfaces, classes abstratas e etc. Como a maior parte da complexidade de nosso domínio está em nossos serviços/backend, optamos por utilizar JS moderno sem tipagem, porém sempre protegendo a integridade das informações e tipos de dados que circulam nos estados dos componentes através de DefaultPropos e PropTypes. (Consideramos TS uma excelente tecnologia, porém ideal para utilização em backends complexos que se aproveitem da tipagem/interfaces para colher os benefícios de uma arquitetura DDD ou MVC por exemplo)  
-   Fluxo de dados
	-	No momento não estamos utilizando um padrão arquitetural como MVVM, MVP ou MVC, para manter a baixa complexidade, já que o coração do domínio e das regras de negócios está no backend. Estamos seguindo um modelo praticamente "MV", na maior parte dos casos o próprio componente é responsável por suas interações com o back-end, seu estados e seus processos, podendo ser quebrado em um Controller-View quando a complexidade da página ou componente comprometer sua evolução, compreensão e/ou manutenção. Buscamos sempre separar a parte visual/UI de processos da parte lógica, ou regras de negócios e/ou validações, mesmo que referentes ao componente. Utilizamos o conceito/arquitetura FLUX apenas para estados compartilhados entre componentes com Redux. 

### Versionamento
-   Git e fluxo
	-	Buscamos utilizar uma estrutura simplificada baseada no gitflow, onde contamos com dois branchs principais, o master, que busca sempre ser uma cópia fiel a aplicação que está em produção, e o branch dev, que é o branch utilizado como raíz para o desnvolvimento das novas features, alterações e hotfixes. Buscamos nunca mergear, dar push ou commitar alterações que fação com que o sistema na branch dev fique "quebrado". A branch master só é alterada através de merges da branch dev.
		-	Master: Fiel a codebase de produção, alterações são incluídas aqui apenas após homologação e testes
		-	Dev: Branch de desnvolvimento, utilizada como base para as branchs de novas features, hotfixes, alterações... Este branch visa sempre ter a última versão estável, é nele que ocorrem as homologações e testes.
		-	Branchs de features, correções de bugs, alterações e hotfixes: Criar um branch baseado no dev para as demandas sob desenvolvimento, para após sua conclusão mergear ao branch dev para homologação e testes.
-   Commits e mensagens
	-	Commitar pequenos passos inteiros, pequenas features completas, buscar evitar commits não finalizados ou que quebrem a app
	- Buscar manter um padrão de mensagens de commits, bem sucinta, porém explicativa, onde seja fácil identificar o escopo do projeto em que a alteração foi feita, o tipo da alteração, a causa/problema/demanda e a solução, sem que seja necessário abrir os logs de alterações para identificar o contexto e causa da alteração. Fazer com que seja fácil identificar o que foi alterado, o porque foi alterado, como foi alterado/solucionado. Exemplo de mensagem: ```Player / Bug: Não estava tocando TVOD no chrome, foi corrigido alterando o arquivo xpto.js, onde quebrava na validação entre HLS ou Dash```. Caso necessário um texto mais explicativo e maior, utilizar o exemplo acima como introdução, o que vai aparecer nas ferramentas de histórico, pular uma linha e escrever o texto mais explicativo abaixo, para assim facilitar a compreensão e identificação por outros membros da equipe. 
	-	Buscar nunca commitar/push de alterações que quebrem a aplicação
	-	Commitar pequenos passos completos, e procurar separar os commits por contextos, se houveram 3 alterações de 3 contextos distintos como por exemplo: Alterados os estilos do header e a função play() do player, o ideal seria que fossem feitos dois commits separados por contexto de alteração.
	-	Assim que ok e feitos os devidos testes de desenvolvimento, mergear o branch de feature, se for o caso, com o branch develop e colocar para testes de Q&A e homologação.

### Testes (Opcional, porém interessante)
-	Testes unitários:
	-	No front a maior parte das lógicas e códigos são sobre componentes de UI, validações de inputs e buscar dados do servidor, sendo assim não há necessidade de sempre ter testes unitários. Porém em alguns momentos, em lógicas mais delicadas e sensíveis, em casos de usos críticos para UX e/ou para o negócio, é muito interessante desacoplar a lógica em questão em um objeto de serviço fácil de se testar e criar testes unitários para ele. Por exemplo: O cálculo do valor exibido na tela em que o serviço disponibiliza apenas percentuais de desconto que se encaixam ou não para o usuário e que deve ser calculado em runtime, este seria um ótimo caso para cobrir por testes pois um erro ali, ou uma alteração que cause a quebra da lógica, precisa ser identificado de imediato.
	- Utilizar Jest para testes unitários
	- Sempre rodar todos os testes unitários disponíveis e de UI para se certificar de que não quebrou nenhum teste, antes de concluir uma demanda ou dar o código como estável, apenas mergear nas branchs bases de códigos que passaram em todos os testes, de UI e unitários.
-	Testes de UI
	-	É muito interessante criar testes de UI para se certificar de que as alterações futuras não quebrem comportamentos de formulários, players, listagens e etc. Um exemplo seria o fluxo de cadastro do usuário, assim como o fluxo de assistir a um vídeo.
	-	Testes de UI também irão facilidar o processo da equipe de Q&A
	-	É indicado utilizar o CyPress para testes de UI
	-	Pensar nos casos de uso de sucesso, porém pensar muito também nos casos de uso de erros, de inputs incorretos dos usuários, casos onde é necessário um feed para o usuário, casos onde a informação pode estar incompleta ou com a integridade comprometida, e outros casos que saem do "fluxo feliz" da aplicação, testes de UI para estes casos são tão importantes quanto os casos do "fluxo feliz".
	-	Sempre antes de dar uma demanda como concluída, ou de mergear o código nas branchs bases, se certificar de que não fez com que quebrasse nenhum teste, para isso rodar todos os testes de UI e unitários.



----
Próximas sessões: 
- Estrutura de arquivos
