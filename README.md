# Projeto de estudo, seguindo o conteúdo apresentado no curso 'TypeScript para Angular'

## Anotações

### TypeScript
- É um *superset* do JavaScript; Assim, fornece features adicionais, como tipagem de variáveis, ao JavaScript. É, básicamente, um 'upgrade'.

#### Instalação
- Pode ser instalado globalmente, na máquina, ou como dependência de um projeto; A segunda forma oferece mais flexibilidade, mais segurança de utilizar a versão correta para o projeto.
- Instalando como dependência de projeto node, pode ser instalado usando o seguinte comando, onde `-D` indica uma dependência de desenvolvimento, somente:
    `npm install typescript -D`

#### Execução
- Executando um arquivo TypeScript com o Node, diretamente, resulta, muitas vezes, em erro pois o arquivo é interpretado como JavaScript e, portanto, features do TypeScript não serão reconhecidas. 
- Posso compilar typescript com `npx tsc <path>` para gerar um arquivo .js.

#### TsConfig
- Arquivo de configuração do comportamento do TS.
- Gerado com o comando `npx tsc --init`, traz consigo várias opções de configuração.'
- Adicionando as configurações 'rootDir' e 'srcDir', consigo compilar o projeto com `npx tsc`, apenas; Assim, serão compilados todos os arquivos .ts em da pasta root definida para arquivos .js na pasta out.
- Definindo um script no arquivo package.json, consigo criar um atalho para compilar e executar o projeto; Foi criado como:
    `"start": "npx tsc && node target/index.js"`
Assim, ao digitar o comando `npm run start`, consigo compilar e executar o projeto.
