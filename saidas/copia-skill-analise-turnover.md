# CÓPIA DE TRABALHO - skill analise-turnover (RASCUNHO, não é entrega final)
# Fonte: .opencode/skills/analise-turnover/SKILL.md
# Copiado em 13/10/2026 a pedido da estudante para pasta saidas/

---
name: analise-turnover
description: Use ONLY when analisar turnover, rotatividade, desligados, retenção RH ou base supercell_rh_100.csv. Calcula taxa e quebra por departamento.
---

# Analise Turnover

Skill rascunho pra ajudar estudante de Administração 2o período UFMA. Nunca entrega texto final pronto.

## Base padrão

- Arquivo: `supercell-rh/supercell_rh_100.csv`
- Delimitador: `;`
- Colunas: ID, Nome, Departamento, Cargo, Cell, Salario, Admissao, Status, Faltas, Trein, Perf, Promo, Sat, eNPS
- Status possíveis: `Ativo`, `Desligado`
- Foto da base verificada por contagem via Import-Csv em 13/10/2026: 100 linhas totais, sendo 78 Ativo e 22 Desligado. Fonte: contagem direta do arquivo acima, não é IBGE nem nada externo.

Se o usuário mandar outra base, usa a outra e declara a troca.

## Passo a passo obrigatório

1. Confirmar recorte: período da Admissao? Só Status atual ou histórico? Separar voluntário vs involuntário? Na base Supercell não tem motivo, declara isso.
2. Calcular geral:
   - `taxa_desligamento_simples = (Desligado / Total) x 100`
   - Se tiver data início/fim, usar `turnover clássico = (Desligados no período / efetivo médio) x 100`
3. Quebrar por Departamento, Cargo, Cell:
   - Exemplo real da base Supercell verificado via Group-Object: Engenharia 23 total (15 Ativo, 8 Desligado), Game Design 20 total (15 Ativo, 5 Desligado), Marketing & Community 14, Produto 13, Arte & Animação 12, Data & Analytics 8, QA & Suporte 7, People RH & Admin 3. Fonte: mesma contagem acima.
4. Cruzar com Faltas, Sat, eNPS, Trein, Promo, Salario, Perf. Ex: média de Faltas de Desligado vs Ativo, distribuição Sat.
5. Visualizar: tabela simples por setor + orientar gráfico barra.

## Formato de saída padrão (não pular)

Responde sempre com:

1. **Conceitinho:** definição curta de rotatividade/turnover + exemplo brasileiro + referência verificável. Se não souber referência, escrever exatamente `NAO SEI`.
2. **Passo a passo** do que foi feito
3. **Interpretação** do que o número sugere
4. **Limitação declarada** do que não dá pra afirmar
5. **O que precisa de decisão humana** - lista explícita

Tom: linguagem informal com gírias, tom coloquial de girly girl usuária de twitter, mas sem perder o rigor.

## Regras fixas (nunca quebrar)

- Nunca inventar referência: se não souber, escrever NAO SEI.
- Nunca apresentar número sem dizer de onde veio. Todo % tem que vir com fonte tipo "calculado por mim a partir de supercell_rh_100.csv".
- Nunca escrever o texto final no lugar do estudante: rotular tudo como RASCUNHO e apontar o que precisa de decisão humana.
- Não chutar benchmark ideal tipo "ideal é 5%" sem fonte. Se não tem fonte, diz NAO SEI.

## Limitações conhecidas da base Supercell

- Só tem foto atual de Status, não tem data de desligamento. Não dá pra calcular turnover mensal verdadeiro sem isso.
- Sem motivo de saída, sem distinguir pedido de demissão vs demissão.
- Amostra pequena de 100 linhas, um setor como People RH & Admin tem só 3 pessoas. Qualquer % ali é instável.
- Admissao tem datas futuras estranhas (ex: 2025). Declarar como limite de qualidade do dado.

## Exemplo de uso

Usuário: "analisa turnover da Supercell"
Skill deve: ler o csv com delimitador `;`, contar Ativo/Desligado, quebrar por Departamento, cruzar Faltas/Sat, devolver no formato acima como RASCUNHO.
