# Estudos_IA

Repositório de estudos de IA, contendo skills e agentes para o [Claude Code](https://claude.ai/code).

## Skills disponíveis

### create-solution-using-clean-architecture

Skill que orienta o Claude Code na criação de soluções .NET seguindo a estrutura de Clean Architecture, com os projetos `API`, `Application`, `Domain`, `Infrastructure` e `UnitTests`, utilizando Central Package Management (CPM) do NuGet para centralizar as versões dos pacotes.

Antes de gerar qualquer arquivo, a skill pergunta ao usuário o nome da Solution e a versão do .NET desejada (mínimo .NET 5), e garante que as dependências entre os projetos sigam sempre a direção `API → Infrastructure → Application → Domain`, sem criar projetos, pastas ou pacotes adicionais que não tenham sido solicitados.

Consulte [skills/create-solution-using-clean-architecture/SKILL.md](skills/create-solution-using-clean-architecture/SKILL.md) para o detalhamento completo das regras.

## Instalação das skills

As skills do Claude Code podem ser instaladas de duas formas: **global** (disponível em qualquer projeto) ou **local** (disponível apenas neste projeto).

### Instalação global

Copie a skill para a pasta `.claude\skills` dentro da pasta do usuário. Exemplo:

```
C:\Users\<seu-usuario>\.claude\skills\create-solution-using-clean-architecture
```

### Instalação local

Copie a skill para a pasta `.claude\skills` dentro da raiz do projeto onde ela deve ser usada. Exemplo:

```
<raiz-do-projeto>\.claude\skills\create-solution-using-clean-architecture
```