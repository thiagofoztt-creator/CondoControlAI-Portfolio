# Evidências de Testes — CondoControlAI

## 1. Objetivo

Este documento organiza as evidências de qualidade de software do CondoControlAI, incluindo testes de API REST, aplicativo Android, autenticação, autorização e integração entre módulos.

Os resultados descritos devem estar associados a registros técnicos que permitam identificar a execução realizada.

## 2. Matriz de Evidências

| ID | Componente | Verificação | Resultado registrado | Evidência pública |
|---|---|---|---|---|
| QA-001 | API REST | Resposta de endpoints autorizados | HTTP 200 registrado em testes do projeto | A vincular |
| QA-002 | Autenticação | Requisição sem autorização válida | HTTP 401 registrado em testes do projeto | A vincular |
| QA-003 | Android | Compilação de desenvolvimento | Build de debug concluído em testes do projeto | A vincular |
| QA-004 | Android | Instalação e inicialização | Execução registrada em ambiente de testes | A vincular |
| QA-005 | Multi-tenant | Restrição de acesso entre condomínios | Validação documental pendente | A executar ou comprovar |
| QA-006 | Encomendas | Recebimento e retirada | Evidência de execução pendente | A vincular |
| QA-007 | OCR e IA | Reconhecimento e revisão de etiquetas | Evidência de execução pendente | A vincular |

**Importante:** os resultados históricos citados precisam ser confirmados por logs, relatórios ou capturas correspondentes antes de serem considerados evidências públicas verificadas.

## 3. Padrão para Registro de Testes

Cada evidência deverá apresentar:

- Identificador do teste.
- Data da execução.
- Versão do software.
- Ambiente utilizado.
- Cenário executado.
- Resultado esperado.
- Resultado obtido.
- Situação: aprovado, reprovado, bloqueado ou não executado.
- Referência à evidência.

## 4. Exemplo de Registro

### QA-001 — Validação de API REST

**Objetivo:** verificar o comportamento de um endpoint protegido após uma requisição autorizada.

**Resultado esperado:** resposta HTTP 200, com conteúdo JSON compatível com o contrato da API.

**Resultado histórico informado:** testes do projeto registraram respostas HTTP 200 em endpoints administrativos.

**Evidência pública:** pendente de associação a um registro anonimizado.

**Status documental:** aguardando comprovação anexada.

## 5. Segurança das Evidências

Antes da publicação, remover ou ocultar:

- Tokens JWT e credenciais.
- Chaves de API.
- Cookies e identificadores de sessão.
- Dados pessoais de moradores e funcionários.
- Documentos e telefones.
- Endereços internos e informações confidenciais da infraestrutura.

Preferir dados fictícios criados especificamente para os testes.

## 6. Critérios de Homologação

Um módulo somente deverá ser identificado como homologado quando existirem:

1. Requisitos e critérios de aceite definidos.
2. Cenários aplicáveis executados.
3. Resultados compatíveis com os critérios.
4. Evidências verificáveis.
5. Defeitos críticos resolvidos.
6. Aprovação do responsável autorizado.

## 7. Estado da Documentação

Este arquivo é um inventário inicial de evidências.

A ausência de um anexo não significa necessariamente que o teste não foi executado, mas impede que seu resultado seja demonstrado publicamente por este documento.

---

**CondoControlAI — Portfólio técnico e documentação de QA. Código-fonte privado.**

## Situação atual das evidências

A documentação pública apresenta os cenários
de testes, os resultados esperados e os
critérios de homologação do CondoControlAI.

Os registros originais de execução, logs de
compilação e relatórios de testes ainda não
foram anexados a este repositório.

Por esse motivo:

- Os casos de teste documentados não são
  apresentados como automaticamente aprovados.
- Resultados históricos permanecem pendentes
  de comprovação documental.
- As imagens das interfaces representam
  demonstrações visuais do aplicativo.
- Novas evidências serão adicionadas somente
  após verificação e remoção de dados sensíveis.

**Status geral das evidências públicas:**
Pendente de comprovação documental.
