# ProduSIM – Simulação de PCP

ProduSIM é um jogo de simulação de Planejamento e Controle da Produção (PCP) para uso educacional. O sistema inclui dois módulos sequenciais:

- **PCP2 (v1.2.0)**: Períodos 1-12 - MPS/MRP, Sequenciamento e Capacidade Básica
- **PCP1 (v1.3.0)**: Períodos 13-24 - Sistema avançado com recursos completos

A progressão educacional é projetada para que os estudantes aprendam conceitos básicos no PCP2 e depois avancem para funcionalidades mais complexas no PCP1.

## Como começar

- Abra `index.html` no navegador para acessar a landing page.
- Para educação sequencial: inicie pelo PCP2, depois PCP1.
- Acesso direto: `modulos/pcp1.html` ou `modulos/pcp2.html`.

Opcional: sirva como site estático (recomendado para evitar restrições de algumas extensões do navegador ao ler arquivos locais).

Exemplos de servidor simples (opcional):

```bash
# Python 3
python3 -m http.server 8080
# Depois visite http://localhost:8080
```

## Regras do Jogo

### PCP2 (Módulo Introdutório - v1.2.0)
**Objetivo**: Maximizar o Resultado Acumulado após 12 períodos (1-12).

**Funcionalidades**:
- Sistema de custos harmonizado (custos fixos R$1000 + armazenagem R$0,25/unidade)
- Calculadora BOM com sugestões inteligentes de compras
- Capacidade ajustável (1-2 turnos por período, turnos extras custam R$300)
- Compras de emergência automáticas (+25% custo)
- Demanda realística (70% baseada na previsão do aluno + 30% demanda base)

**Decisões**:
- Plano Mestre de Produção (MPS) - sua previsão influencia 70% da demanda real
- Política de lotes (L4L ou FOQ)
- Recebimentos Agendados (SR) com apoio da calculadora BOM
- Número de turnos por período
- Regras de sequenciamento (FCFS, SPT, EDD)

### PCP1 (Módulo Avançado - v1.3.0)  
**Objetivo**: Maximizar o Resultado Acumulado após 12 períodos (13-24).

**Funcionalidades Avançadas**:
- Todos os recursos do PCP2 em versão completa
- Capacidade dinâmica (0-3 turnos por processo, turnos extras custam R$500)
- Compras de emergência com custo premium (+50%)
- Calculadora BOM avançada com análise de trade-offs
- Sistema financeiro completo com análise detalhada
- Logs de depuração e feedback em tempo real

**Decisões Adicionais**:
- Gestão de múltiplos processos produtivos
- Estratégias complexas de compras e estoque
- Análise avançada de capacidade e gargalos

### Dicas Estratégicas Gerais
- **Previsões precisas são essenciais**: previsões ruins resultam em demanda inesperada e custos extras
- **Use as calculadoras BOM**: otimizam compras e evitam desperdícios  
- **Gerencie capacidade estrategicamente**: turnos extras podem ser mais baratos que perdas de venda
- **Monitore custos de emergência**: planejar compras antecipadamente evita custos premium
- **Analise trade-offs**: L4L minimiza estoque, FOQ reduz setups
- **Progression natural**: aprenda no PCP2, domine no PCP1

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

### v1.3.0 (2024-09-18) - PCP1 Avançado
- ✅ **Nova funcionalidade**: Gestão dinâmica de capacidade com ajuste de turnos por período (0-3 turnos)
- ✅ **Interface aprimorada**: Calculadora BOM inteligente com sugestões automáticas de compra
- ✅ **Sistema de custos**: Turnos extras custam R$ 500 cada, separados no relatório financeiro
- ✅ **Análise estratégica**: Trade-off entre custos de turnos extras vs terceirização
- ✅ **Feedback visual**: Barras de utilização com alertas de sobrecarga e folgas
- ✅ **Documentação**: Manual técnico completo e relatórios PDF aprimorados

### v1.2.0 (2024-09-18) - PCP2 Harmonizado  
- ✅ **Consistência educacional**: PCP2 atualizado para manter continuidade com PCP1
- ✅ **Sistema de custos harmonizado**: Custos fixos R$1000 + armazenagem R$0,25/unidade
- ✅ **Calculadora BOM básica**: Sugestões simples para compras de componentes B/C
- ✅ **Capacidade ajustável**: 1-2 turnos por período (turnos extras custam R$300)
- ✅ **Compras de emergência**: Sistema automático com custo premium +25%
- ✅ **Demanda realística**: 70% previsão + 30% base histórica (volatilidade reduzida para 10%)
- ✅ **Interface aprimorada**: Feedback detalhado e regras atualizadas

### v1.1.0 (anterior)
- Sistema base de simulação PCP
- Módulos PCP1 e PCP2 implementados  
- Sistema de relatórios e exportação PDF
- Painéis de KPI adicionais e auditoria por período (modo instrutor)
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
