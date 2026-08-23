---
name: create-solution-using-clean-architecture
description: Cria Solution .NET utilizando Clean Architecture com os projetos API, Application, Domain, Infrastructure e UnitTests. Use esta skill quando o usuário quiser criar uma nova Solution .NET seguindo a estrutura Clean Architecture.
---

# Create Clean Architecture Solution

## Objetivo

Criar uma nova Solution .NET seguindo exatamente a estrutura de Clean Architecture, com os projetos abaixo. 

Utilizar Central Package Management (CPM) do NuGet para gerenciar as versões dos pacotes NuGet de forma centralizada.

{SolutionName}/
├── Directory.Packages.props
├── Directory.Build.props
└── src/
    └── 
        ├── {SolutionName}.API/
        ├── {SolutionName}.Application/
        ├── {SolutionName}.Domain/
        ├── {SolutionName}.Infrastructure/
        └── {SolutionName}.UnitTests/

A estrutura de dependências deve ser:

Directory.Packages.props: utilizado para gerenciar as versões dos pacotes NuGet de forma centralizada.

Directory.Build.props: utilizado para definir propriedades de build compartilhadas entre os projetos. Deve ser criado com a seguinte estrutura abaixo, onde {DotNetVersion} corresponde à versão do .NET escolhida pelo usuário:

```xml
<PropertyGroup>
  <TargetFramework>net{DotNetVersion}.0</TargetFramework>
  <Nullable>enable</Nullable>
  <ImplicitUsings>enable</ImplicitUsings>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
</PropertyGroup>

API
→ Infrastructure

Infrastructure
→ Application
→ Domain

Application
→ Domain

Domain não deve depender de ninguém.

UnitTests não deve depender de nenhum projeto inicialmente.

## Informações necessárias

Antes de executar qualquer comando, pergunte ao usuário:

1. Qual será o nome da Solution?
2. Qual versão do .NET deseja utilizar? A versão mínima permitida é .NET 5.

A versão mínima permitida é .NET 5.

Se o usuário informar uma versão inferior a .NET 5, informe que a versão não é suportada e solicite outra.

Depois que essas informações forem fornecidas, execute toda a tarefa sem solicitar confirmação adicional, desde que:

- A pasta de destino não exista;
- Não existam arquivos que serão sobrescritos;
- A versão do .NET seja válida;
- Os comandos necessários estejam disponíveis.

Não pergunte ao usuário se deve executar comandos individuais.

Não solicite confirmação antes de:
- criar diretórios;
- criar projetos;
- adicionar projetos à Solution;
- adicionar referências entre projetos;
- remover as classes `Class1.cs` e `UnitTest1.cs`;
- configurar os arquivos `.csproj`;
- executar `dotnet build`.

Utilize os padrões definidos nesta skill sempre que uma decisão não tiver sido especificada pelo usuário.

## Convenção de nomes

Se o usuário informar:

ClientManager

a Solution deverá se chamar:

ClientManager

e os projetos:

ClientManager.API
ClientManager.Application
ClientManager.Domain
ClientManager.Infrastructure
ClientManager.UnitTests

## Templates

## API:

dotnet new webapi

A API deve ser criada contendo a estrutura padrão de Controllers.

O arquivo `WeatherForecastController.cs` deve permanecer no projeto.

Resultado esperado:

{SolutionName}.API/
└── Controllers/
    └── WeatherForecastController.cs

## Application:

dotnet new classlib

Após criar o projeto, remova a classe `Class1.cs`. Ela não deve permanecer.

## Domain:

dotnet new classlib

Após criar o projeto, remova a classe `Class1.cs`. Ela não deve permanecer.

## Infrastructure:

dotnet new classlib

Após criar o projeto, remova a classe `Class1.cs`. Ela não deve permanecer.

## UnitTests:

dotnet new classlib

Após criar o projeto, remova a classe `UnitTest1.cs`. Ela não deve permanecer.

## Criação da Solution

Crie a Solution utilizando o comando apropriado para a versão instalada do .NET SDK.

A Solution deve permanecer na raiz da pasta da aplicação.

Os projetos devem permanecer dentro de `src`.

## Referências

Depois de criar os projetos, configure exatamente estas dependências:

API
→ Infrastructure

Infrastructure
→ Application
→ Domain

Application
→ Domain

Domain não deve depender de ninguém.

UnitTests não deve depender de nenhum projeto inicialmente.

## Validação

Depois de criar os projetos:

1. Verifique as referências de cada projeto.
2. Verifique se a Solution reconhece todos os projetos.
3. Execute:

dotnet build

4. Se houver erros, analise e corrija-os.

## Regras

Não altere a arquitetura definida neste documento.

Não crie projetos adicionais.

Não precisa criar uma subpasta com o nome da solution dentro de `src`. A estrutura de diretórios deve ser exatamente como descrita. Ou seja, dentro da solution, deve existir apenas a pasta `src` e dentro dela os projetos.

Não mova os projetos para fora de `src`.

Não adicione dependências que não foram solicitadas.

Não instale pacotes NuGet desnecessários.

Sempre informe ao usuário o resultado final.

Se a pasta ou Solution já existir, não sobrescreva arquivos sem antes informar o usuário.