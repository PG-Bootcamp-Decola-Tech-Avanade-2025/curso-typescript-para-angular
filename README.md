# Projeto de estudo, seguindo o conteúdo apresentado no curso 'TypeScript para Angular'
As anotações tiradas serão focadas nas características específicas do TypeScript; Conceitos comuns a outras linguagens não terão destaque.

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

#### ts-node-dev
- Dependência que permite rodar aplicação, transpilando o código em memória e sem necessidade de criar arquivos compilados.
- É uma forma mais direta e recomendada para trabalhar com TS.
- Pode ser instalado como dependência do projeto node com `npm install ts-node-dev -D`.
- Com essa dependência, pode-se executar o projeto com `ts-node-dev --respawn --transpile-only src/index.ts`; Aqui, a flag `--respawn` indica que a aplicação deve ser executada novamente quando houver mudança.

#### Tipagem e Sintaxe da Linguagem
- No TS, tipos numéricos não são espeficicados como em uma linguagem mais tradicional; Usa-se o tipo `number`, tanto para inteiros quanto para reais.
- A sintaxe de declaração de tipos é feita com uso de `:`; Como em: `let nome:string = "Pedro";`.
- Na declaração de uma variável, não é necessário sempre declarar o tipo.
- Os tipos `null` e `undefined` obrigam a variável a receber como valor apenas eles mesmos; Como um exemplo:
    ```
    let nome: null = null; // nome só pode assumir o valor null
    let idade: undefined = undefined // idade só pode assumir o valor undefined
    ```
- O tipo `void` define que não pode haver valor; É utilizado como tipo de retorno, geralmente.
- O tipo `any` é um tipo 'abrangente'; Variáveis do tipo `any` podem receber valores de qualquer tipo.
- O tipo `object` define que a variável deve ser um objeto mas não define que tipo específico.
- Arrays podem conter vários tipos; Declarado como: `let arr: (<tipo-1> | <tipo-2>)[]`.
- Tuples são como objetos 'light', recebendo um número definido de valores com tipos definidos; Declara-se uma tupla com: `let tup:[<tipo-1>, <tipo-2>, ..., <tipo-n>]`;
- O tipo `Date` trabalha com o padrão americano de datas: 'yyyy-mm-dd hh:mm'.
- Funções tem seu return type definido como: `function func(): <tipo-de-retorno>`; Assim como variáveis, pode ser passado mais de um único tipo de retorno, separando cada um com `|`.
- Para tipar o retorno de uma função assíncrona, deve-se declarar o tipo de retorno em uma Promise; São aceitos, também, vários tipos de retorno; Como: `Promise< <tipo-1> | <tipo-2> >`.

#### Interfaces e Types
- Funcionam de forma muito similar; Interface é, geralmente, usada em qualquer situação onde seja necessário tipar um objeto;
Apesar disso, é recomendado o uso de interfaces em conjunto com classes e type em outros casos.
- Interfaces são declaradas como: `interface interf { prop1: <type-1> }`.
- Types são declarados como: `type typ = { prop1: <type-1> }`.
- é possível marcar propriedades com a keyword `readonly` para tornar a mesma imutável.

#### Classes
- Implementam access modifiers de forma similar a linguagens tradicionais; São: `public`, `protected` e `private`; Por padrão, propriedades são públicas.
- Com `?` é possível declarar propriedades nullable; Como em: `age?: number`.

#### Decorators
- Para trabalhar com decorators no TS, é preciso habilitar a opção 'experimental-decorators' no arquivo tsconfig.json.
- Pode decorar classes e propriedades.
- Estruturados como:
    ```
    function decoratorFunction(param: any) { // Podem receber quaisquer parâmetros
        return (target: any) => { // Retornam uma função que recebe target, sendo target o objeto decorado.
            ...
        }
    }
    ```
- A função de retorno pode receber, também, o parâmetro `key`, que permite recuperar o valor da propriedade decorada.
- Ao decorar propriedades, pode utilizar `Object.defineProperty(target, key, {get: ..., set: ...})` para criar getters e setters; Útil para validação de propriedades.
