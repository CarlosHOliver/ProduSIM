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
- Previsão: use a Demanda Base como referência e ajuste pelo histórico. **Sua previsão influencia a demanda real (70% previsão + 30% base histórica)**.
- Produção: planeje dentro da capacidade para minimizar terceirização.
- Compras: calcule insumos pelo BOM e o plano de produção; evite estoques excessivos. **Caso haja falta de material, compras de emergência são realizadas automaticamente com custo premium (+50%)**.
- Serviço: busque atender a demanda minimizando perdas de venda e custo de estoque.
- Fechamento: feche o período e avalie o Financeiro; ajuste a estratégia no período seguinte.

Critério de vitória
- Vence quem tiver maior Resultado Acumulado no período 24.
- Desempate pelo maior Nível de Serviço acumulado.

Dicas
- Evite perdas de venda e terceirização para preservar margens.
- Estoques altos custam; estoques baixos podem causar perdas e compras de emergência caras.
- Planeje compras adequadamente: falta de material resulta em aquisição automática com custo premium.
- **Previsões precisas são essenciais**: previsões ruins resultam em demanda inesperada e custos extras.
- **Gerencie a capacidade estrategicamente**: ajuste turnos conforme necessário - turnos extras custam R$ 500 mas podem ser mais baratos que terceirização.
- Use a calculadora BOM para otimizar compras e evitar desperdícios.
- Monitore o erro de previsão em cada período para melhorar a acurácia.
- Use gráficos e relatórios para ajustar mix e plano por período.

As regras também estão disponíveis dentro do jogo:
- Na landing page (`index.html`) na seção “Regras do Jogo”.
- No módulo (`modulos/pcp1.html`) via botão “Regras do Jogo” no rodapé (modal).

## Funcionalidades

- Cadastro do grupo e configuração de cenário (Modo Professor) com preços, custos e volatilidade.
- Fluxo por período (13 a 24) com telas: Demanda, Produção, Compras, Capacidade e Financeiro.
- **Sistema inteligente de compras**: compras de emergência automáticas quando há falta de material, com custo premium (150% do custo base).
- **Demanda realística**: demanda influenciada pelas previsões do usuário (70%) e demanda base (30%), com volatilidade configurável.
- **Acompanhamento de precisão**: cálculo do erro de previsão (MAPE) para feedback educacional.
- **Gestão dinâmica de capacidade**: ajuste de turnos de trabalho por período e processo, com custos diferenciados para turnos extras.
- **Calculadora BOM inteligente**: sugestões automáticas de compra baseadas na produção planejada.
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
- Análise histórica de precisão de previsões.
- Simulação de cenários adversos (greves, ruptura de fornecimento).

## Changelog

### v1.2.0 (2024)
- ✅ **Correção crítica**: Sistema de compras de emergência agora incorpora materiais ao estoque
- ✅ **Nova funcionalidade**: Demanda realística influenciada pelas previsões do usuário (70/30)
- ✅ **Acompanhamento educacional**: Cálculo e exibição do erro de previsão (MAPE)
- ✅ **Melhorias na interface**: Alertas visuais para compras de emergência e erros de previsão

### v1.1.0 (anterior)
- Sistema base de simulação PCP
- Módulos PCP1 e PCP2 implementados
- Sistema de relatórios e exportação PDF
- Painéis de KPI adicionais e auditoria por período (modo instrutor).

## Créditos e atribuição

- Autor: Carlos Henrique (LABINFO/FAEN/UFGD) – 2025
- Baseado no jogo LSSP_PCP (UFSC) – adaptação para a web.

## Changelog

### v1.3.0 (2024-09-18)
- ✅ **Nova funcionalidade**: Gestão dinâmica de capacidade com ajuste de turnos por período
- ✅ **Interface aprimorada**: Calculadora BOM inteligente com sugestões automáticas de compra
- ✅ **Sistema de custos**: Turnos extras custam R$ 500 cada, separados no relatório financeiro
- ✅ **Análise estratégica**: Trade-off entre custos de turnos extras vs terceirização
- ✅ **Feedback visual**: Barras de utilização com alertas de sobrecarga e folgas

### v1.2.0 (2024)
- ✅ **Correção crítica**: Sistema de compras de emergência agora incorpora materiais ao estoque
- ✅ **Nova funcionalidade**: Demanda realística influenciada pelas previsões do usuário (70/30)
- ✅ **Acompanhamento educacional**: Cálculo e exibição do erro de previsão (MAPE)
- ✅ **Melhorias na interface**: Alertas visuais para compras de emergência e erros de previsão

### v1.1.0 (anterior)
- Sistema base de simulação PCP
- Módulos PCP1 e PCP2 implementados
- Sistema de relatórios e exportação PDF

**v1.0.0** - 2025-09-05
- 🚀 Lançamento inicial do ProduSIM
- Módulos PCP1 e PCP2 completos
- Interface web responsiva
- Relatórios em PDF

## Licença

Este projeto é licenciado sob a **GNU Affero General Public License v3.0 (AGPL-3.0)**.
Consulte o arquivo `LICENSE` para mais detalhes.
