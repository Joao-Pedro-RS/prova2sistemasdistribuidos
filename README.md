# prova2sistemasdistribuidos

**Professora:** Simone Tatiane do Canto
**Data:** 18/11/2026

## 1. Situação-Problema
**Descreva brevemente os problemas apresentados na Central de Pedidos Distribuída.**

  O cliente precisava que somente 2 pedidos fossem processados ao invés de 3, a replica não atualizava junto da principal e sempre mostrava erro(Mesmo quando o retornava correto).

## 2. Primeira execução.
**Explique o que foi observado ao executar o programa pela primeira vez.**
  Ao executar foi possível observar que os valores de estoque não estavam atualizando mesmo com as movimentações e a consulta após falha retornava indisponível

  <ins>**Evidencia 1 - Primeira execução**</ins>
  https://github.com/Joao-Pedro-RS/prova2sistemasdistribuidos/blob/main/evidencia%201%20-%20primeira%20execu%C3%A7%C3%A3o

## 3. Problema A - Concorrência
**Qual problema foi identificado?**
  O cliente solicitou que fosse processado 2 pedidos por vez ao invés de 3
  
**Qual alteração foi realizada?**
  Foi alterado o valor de "MAXIMO_SIMULTANEO" de 3 para 2
  
  <ins>**Evidencia 2 - Concorrência**</ins>
  https://github.com/Joao-Pedro-RS/prova2sistemasdistribuidos/blob/main/evidencia%202%20-%20concorr%C3%AAncia

## 4. Problema B - Replicação e consistência
**Qual problema foi identificado?**
  Os valores não estavam sendo replicados corretamente
  
**Qual alteração foi realizada?**
  principal["estoque"] = principal["estoque"] >> Alterado para >> replica["estoque"] = principal["estoque"]

  <ins>**Evidencia 3 - Sincronização**</ins>
  https://github.com/Joao-Pedro-RS/prova2sistemasdistribuidos/blob/main/evidencia%203%20-%20sincroniza%C3%A7%C3%A3o

## 5. Problema C - Tolerância a falhas
**Qual problema foi identificado?**
  Na condição IF estava sendo interpretado o principal e não a replica
  
**Qual alteração foi realizada?**
  if principal["online"]: return( "REPLICA", replica["estoque"] ) >> Alterado para >> if replica["online"]: return( "REPLICA", replica["estoque"] )

  <ins>**Evidencia 4 - Tolerância a falhas**</ins>
  https://github.com/Joao-Pedro-RS/prova2sistemasdistribuidos/blob/main/evidencia%204%20-%20toler%C3%A2ncia%20e%20falhas

## 6. Validação do programa
**Descreva os resultados observados após as três correções**
  Após todas as alterações o programa executou conforme a expectativa do Cliente.

  <ins>**Evidencia 5 - Execução completa**</ins>
  https://github.com/Joao-Pedro-RS/prova2sistemasdistribuidos/blob/main/evidencia%205%20-%20valida%C3%A7%C3%A3o%20completa



## Etapa 5 - Análise Técnica

**Questão 1. Qual é a Função do semáforo no processamento dos pedidos?**

**Questão 2. Por que é necessário sincronizar os dados entre o servidor principal e a réplica?**

**Questão 3. O que significa tolerância a falhas e como ela aparece neste programa?**

**Questão 4. Para que serve o Lock no programa e como o controle de acesso aos recursos ajuda a prevenir problemas de concorrência?**

**Questão 5. Considerando a sequência de eventos, a sincronização do estoque deve acontecer antes ou depois do processamento dos pedidos? Explique a a relação de causalidade**
