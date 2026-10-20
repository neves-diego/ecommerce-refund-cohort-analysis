# Análise de Reembolsos por Coortes | E-commerce

**Estudo de caso de Analytics: atrasos logísticos, reembolsos e projeção de exposição financeira.**

## Contexto e objetivo
Em um desafio técnico de Analytics, foi analisado um cenário de e-commerce de suplementos com atrasos de envio por um fornecedor externo entre **25/04 e 25/05/2026**. O objetivo foi acompanhar reembolsos e chargebacks de vendas do período e projetar os valores ainda sujeitos a reembolso, considerando uma janela de até 60 dias.

**Data de corte:** 11/06/2026.

## Perguntas de negócio
- Como evoluem os reembolsos por coorte de data de compra?
- Como a maturidade diferente das coortes influencia a comparação?
- Qual o valor total de reembolsos projetado para o período afetado?
- O que é possível — e o que não é possível — afirmar sobre o impacto *incremental* dos atrasos?

## Metodologia resumida
1. **Granularidade:** consolidação da base de itens e ofertas adicionais (*upsells*) no nível de pedido, para evitar dupla contagem.
2. **Eventos:** tratamento de reembolsos e chargebacks como devolução integral do valor do pedido, conforme as regras do desafio.
3. **Coortes:** agrupamento por semana da compra e acompanhamento da evolução dos reembolsos.
4. **Projeção:** uso de coortes afetadas com ao menos 28 dias de observação como referência para a taxa estimada.
5. **Sensibilidade:** cenários alternativos exploratórios, sem inferência causal.

Detalhes em [Metodologia](docs/metodologia.md).

## Resultados principais

| Indicador | Valor |
|---|---:|
| Faturamento do período afetado | US$ 1.228.773,14 |
| Reembolsos observados até 11/06/2026 | US$ 282.652,19 |
| Taxa observada | 23,00% |
| Taxa projetada de reembolso | 28,09% |
| Reembolsos totais projetados | US$ 345.144,94 |
| Reembolsos futuros estimados | US$ 62.492,75 |

**Interpretação importante:** os **US$ 345,1 mil** representam o total de reembolsos projetado para as vendas do período afetado — **não** a perda adicional comprovadamente causada pelo atraso logístico. Sem um histórico pré-incidente comparável, não é possível identificar com segurança o efeito causal.

O estudo também explora um cenário incremental de aproximadamente **US$ 185 mil**, usando referência posterior ao problema. Esse cenário é **hipotético e não conclusivo**.

Veja [Resultados e limitações](docs/resultados.md).

## Competências demonstradas
- Tratamento e consolidação de dados por pedido
- Análise por coortes e maturidade de observação
- Construção e interpretação de KPIs financeiros
- Projeções e análise de sensibilidade
- Comunicação de incertezas e limitações metodológicas

**Ferramentas utilizadas:** Excel / Google Sheets.

## Estrutura
```text
.
├── README.md
├── .gitignore
└── docs/
    ├── metodologia.md
    └── resultados.md
```

## Sobre os dados
A planilha original e a base de dados do desafio **não estão disponíveis neste repositório**, por precaução quanto a direitos de divulgação e confidencialidade. Os indicadores publicados são resultados agregados do estudo de caso.

## Autor
**Diego Neves** · [GitHub](https://github.com/neves-diego)
