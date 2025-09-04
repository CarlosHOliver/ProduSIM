# ProduSIM – Simulação de PCP

ProduSIM é um jogo de simulação de Planejamento e Controle da Produção (PCP) para uso educacional. Nele, os times tomam decisões por período (13 a 24) nas áreas de Demanda, Produção, Compras, Capacidade e Financeiro, acompanhando resultados e indicadores até o relatório final consolidado em PDF.

Este repositório contém uma versão web (HTML/CSS/JS) que roda diretamente no navegador, com persistência local via `localStorage`.

## Como começar

- Abra `index.html` no navegador para acessar a landing page e iniciar o módulo.
- Ou acesse diretamente o módulo: `modulos/pcp1.html`.

Opcional: sirva como site estático (recomendado para evitar restrições de algumas extensões do navegador ao ler arquivos locais).

Exemplos de servidor simples (opcional):

```bash
# Python 3
python3 -m http.server 8080
# Depois visite http://localhost:8080
```

## Regras do Jogo (resumo)

Objetivo
- Maximizar o Resultado Acumulado (lucro total) ao final do período 24.
- Manter Nível de Serviço elevado (mínimo recomendado: 90%).

Como jogar
- Previsão: use a Demanda Base como referência e ajuste pelo histórico.
- Produção: planeje dentro da capacidade para minimizar terceirização.
- Compras: calcule insumos pelo BOM e o plano de produção; evite estoques excessivos.
- Serviço: busque atender a demanda minimizando perdas de venda e custo de estoque.
- Fechamento: feche o período e avalie o Financeiro; ajuste a estratégia no período seguinte.

Critério de vitória
- Vence quem tiver maior Resultado Acumulado no período 24.
- Desempate pelo maior Nível de Serviço acumulado.

Dicas
- Evite perdas de venda e terceirização para preservar margens.
- Estoques altos custam; estoques baixos podem causar perdas.
- Use gráficos e relatórios para ajustar mix e plano por período.

As regras também estão disponíveis dentro do jogo:
- Na landing page (`index.html`) na seção “Regras do Jogo”.
- No módulo (`modulos/pcp1.html`) via botão “Regras do Jogo” no rodapé (modal).

## Funcionalidades

- Cadastro do grupo e configuração de cenário (Modo Professor) com preços, custos e volatilidade.
- Fluxo por período (13 a 24) com telas: Demanda, Produção, Compras, Capacidade e Financeiro.
- Cálculos de capacidade por processo, consumo de materiais (BOM), vendas e perdas, custos e resultado.
- Financeiro robusto com recomputo on-demand e visualização por período (seletor de período).
- Relatórios: parcial durante a simulação e final ao término (período 24), com exportação PDF.
- Persistência automática no navegador usando `localStorage`.

## Tecnologias

- HTML5, CSS (Bootstrap 5), JavaScript (vanilla)
- Chart.js (gráficos)
- jsPDF (exportação de PDF)
- Armazenamento local (`localStorage`)

## Estrutura do projeto

- `index.html` – Landing page com visão geral e acesso ao Módulo PCP1.
- `modulos/pcp1.html` – Aplicação do Módulo PCP1 (UI e regras de negócio).
- `README.md` – Este documento.
- `LICENSE` – Licença do projeto (AGPL v3).

## Persistência e dados

- Os dados do jogo são salvos no próprio navegador (chave `produSIM_pcp1`).
- Você pode limpar os dados pelo botão “Limpar Dados” no módulo.

## Limitações e próximos passos (ideias)

- Entradas para decisões de capacidade/terceirização mais detalhadas.
- Lead times de compras/produção e fila por processo.
- Painéis de KPI adicionais e auditoria por período (modo instrutor).

## Créditos e atribuição

- Autor: Carlos Henrique (LABINFO/FAEN/UFGD) – 2025
- Baseado no jogo LSSP_PCP (UFSC) – adaptação para a web.

## Licença

Este projeto é licenciado sob a **GNU Affero General Public License v3.0 (AGPL-3.0)**.
Consulte o arquivo `LICENSE` para mais detalhes.
