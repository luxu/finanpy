## Pedir para o Claude gerar a documentação do projeto:

Crie uma pasta docs na raiz do projeto, com toda documentação necessária para que qualquer pessoa consiga entender os guidelines e padrões do projeto.
Separe a documentação em arquivos .md, e crie um readme.md dentro da pasta docs para ser o índice da documentação.
Não documente nada além do que já existe no projeto. Seja simples e direto, e não documente funcionalidades que não existem no projeto.
Use também como referência o @PRD.md do projeto.

## Fazer o init do Claude passando algumas informações de ambiente do projeto:

/init com base na estrutura inicial do projeto, do Product Requirements Document @PRD.md e da documentação @docs/README.md, gere o CLAUDE.md

## Criar os agentes necessários para atuar no projeto — .md na pasta agents

Baseado na documentação do projeto em @docs/README.md e no prd em @PRD.md, crie uma pasta agents com os agentes de IA responsáveis por cada função em um time de desenvolvimento de software. Os agentes devem ser especialistas na stack específica do projeto.
Coloque cada agente em um arquivo .md, e crie um README.md na pasta agents para ser o índice dos agentes, com a descrição de cada um, e quando usar cada um deles.
Os agentes de implementações técnicas devem usar o MCP server do context7 para escrever código atualizado e baseado nas documentações das tecnologias da stack do projeto.
O agente de testes deve usar o MCP server do playwright para acessar o sistema e verificar se está funcionando como o esperado e se o design está correto

crie uma pasta agents com os agentes de IA responsáveis por cada função em um time de desenvolvimento de software. Os agentes devem ser especialistas na stack específica do projeto.

Coloque cada agente em um arquivo .md, e crie um README.md na pasta agents para ser o índice dos agentes, com a descrição de cada um, e quando usar cada um deles.
Os agentes de implementações técnicas devem usar o MCP server do context7 para escrever código atualizado e baseado nas documentações das tecnologias da stack do projeto.
O agente de testes devem usar o MCP server do playwright para acessar o sistema e verificar se está funcionando como o esperado, e se o design está correto.
Crie apenas agentes necessários para a produção de código, como backend django, frontend django template language e tailwindcss, qa/tester, etc.
