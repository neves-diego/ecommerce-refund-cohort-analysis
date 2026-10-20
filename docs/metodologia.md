# Metodologia

## 1. Problema de negócio
Estimar o volume de reembolsos relacionado às vendas de um período com atrasos de expedição e distinguir o **total projetado de reembolsos** de um possível **efeito incremental do atraso**.

- Período afetado: **25/04 a 25/05/2026**
- Data de corte da observação: **11/06/2026**
- Janela de reembolso considerada: **até 60 dias**

## 2. Unidade de análise
A base contém registros por item, incluindo ofertas adicionais (*upsells*). Para calcular indicadores por pedido, os registros foram consolidados na granularidade de **pedido**, evitando duplicação de pedidos e distorção de denominadores.

## 3. Tratamento de eventos
Reembolsos e chargebacks foram tratados como devolução integral do valor do pedido, seguindo as premissas do desafio. Os resultados dependem dessa convenção.

## 4. Coortes e maturidade
Os pedidos foram agrupados por **semana de compra**. Cada coorte foi observada ao longo do tempo, considerando que compras recentes tiveram menos dias para registrar reembolsos até a data de corte.

Comparar diretamente taxas acumuladas de coortes com maturidades distintas pode induzir conclusões equivocadas.

## 5. Projeção
A taxa projetada de **28,09%** foi estimada usando coortes do período afetado com **pelo menos 28 dias de observação** como referência para o conjunto afetado.

A aplicação dessa taxa ao faturamento afetado gera a estimativa do total de reembolsos. Subtraindo os reembolsos já observados, obtém-se o montante futuro estimado.

Essa é uma **projeção baseada em premissas**, não uma previsão garantida.

## 6. Cenário de sensibilidade
O estudo inclui comparação exploratória com uma taxa de referência posterior ao período de atrasos. Como as coortes posteriores ainda estavam menos maduras, esse cenário **não fornece um contrafactual validado** e não permite atribuir causalmente o diferencial aos atrasos.

## 7. Limitações e reprodutibilidade
- Ausência de histórico pré-incidente na base analisada.
- Coortes com janelas de observação diferentes.
- Suposição de que coortes mais maduras representam as demais.
- Impossibilidade de reproduzir integralmente os cálculos a partir deste repositório, pois a planilha e os dados originais não são públicos.

O repositório documenta a lógica analítica e os resultados agregados, sem divulgar a base do desafio.
