# 🧪 Testes e Homologação — CondoControlAI

**Projeto:** CondoControlAI — Plataforma de Gestão Condominial  
**Tecnologias:** Android, Kotlin, PHP, MySQL, API REST e Inteligência Artificial  
**Tipo de documentação:** Plano de testes, validação e homologação funcional

## 1. Objetivo

Este documento apresenta a estratégia de testes do CondoControlAI, incluindo validações de funcionalidades, integrações, autenticação, controle de acesso e regras de negócio.

O objetivo é demonstrar as práticas de qualidade de software aplicadas ao projeto e estabelecer critérios para verificar o funcionamento dos módulos.

**Nota:** os cenários apresentados não constituem, por si só, evidência de execução ou aprovação. Os resultados devem ser vinculados aos respectivos registros de teste.

## 2. Estratégia de Testes

O processo de validação contempla:

- Testes funcionais.
- Testes de integração.
- Testes de API REST.
- Testes de autenticação e autorização.
- Testes de isolamento multi-tenant.
- Testes de aplicativos Android.
- Verificação de logs e tratamento de erros.
- Testes de regressão.
- Homologação de funcionalidades.

## 3. Ambiente de Testes

| Componente | Tecnologia |
|---|---|
| Aplicativo móvel | Android / Kotlin / Jetpack Compose |
| Backend | PHP 8 / API REST |
| Banco de dados | MySQL 8 |
| Painel administrativo | HTML, CSS e JavaScript |
| Comunicação | HTTPS / JSON |
| Autenticação | JWT |
| Processamento de imagens | OCR e serviços de IA |

### Informações a registrar por execução

- Identificador do ambiente.
- Versão do aplicativo ou commit.
- Data e horário do teste.
- Responsável pela execução.
- Dispositivo ou navegador utilizado.
- Resultado obtido.
- Evidência correspondente.

Dados sensíveis de infraestrutura e credenciais não devem constar na documentação pública.

## 4. Casos de Teste — API REST

| ID | Cenário | Resultado esperado |
|---|---|---|
| API-001 | Autenticação com credenciais válidas | HTTP 200 e sessão autorizada |
| API-002 | Autenticação com credenciais inválidas | Acesso negado sem exposição de dados |
| API-003 | Consulta com token ausente | HTTP 401 |
| API-004 | Consulta com token expirado | HTTP 401 |
| API-005 | Acesso a recurso sem permissão | HTTP 403 ou resposta restritiva definida pela API |
| API-006 | Consulta de moradores autorizada | Dados restritos ao condomínio |
| API-007 | Cadastro com informações inválidas | Erro de validação apropriado |
| API-008 | Consulta a registro inexistente | HTTP 404, conforme contrato da API |
| API-009 | Consulta de dashboard autorizada | Dados consistentes com o banco |
| API-010 | Operação com identificador de outro condomínio | Acesso bloqueado |

### Critérios de validação

- Código HTTP adequado.
- Estrutura JSON consistente.
- Respeito às permissões.
- Ausência de dados indevidos nas respostas.
- Integridade das operações.
- Tratamento seguro das falhas.

## 5. Testes de Segurança e Multi-Tenant

A arquitetura multi-tenant exige a validação do isolamento lógico entre condomínios.

### Cenários

**SEG-001 — Isolamento entre condomínios**

Um usuário autenticado em determinado condomínio não deve visualizar ou modificar registros pertencentes a outro condomínio sem autorização explícita.

**SEG-002 — Autorização por perfil**

Porteiros, zeladores, administradores e moradores devem possuir acesso somente aos recursos autorizados.

**SEG-003 — Validade do token**

Tokens inválidos, expirados ou revogados devem ser recusados conforme o mecanismo de autenticação implementado.

**SEG-004 — Manipulação de parâmetros**

A alteração de identificadores enviados pelo cliente não pode permitir acesso indevido a registros.

**SEG-005 — Auditoria de operações**

Ações relevantes devem produzir os registros de auditoria exigidos pelas regras de negócio.

Os testes devem ser executados em ambientes autorizados, com dados próprios de homologação.

## 6. Testes Funcionais — Gestão Condominial

| ID | Módulo | Cenário |
|---|---|---|
| FUN-001 | Moradores | Cadastrar e consultar um morador |
| FUN-002 | Moradores | Associar morador a uma unidade |
| FUN-003 | Encomendas | Registrar recebimento de encomenda |
| FUN-004 | Encomendas | Confirmar retirada autorizada |
| FUN-005 | Encomendas | Consultar histórico de movimentações |
| FUN-006 | Visitantes | Registrar entrada |
| FUN-007 | Visitantes | Registrar saída |
| FUN-008 | Veículos | Cadastrar e consultar veículo |
| FUN-009 | Funcionários | Registrar ponto |
| FUN-010 | Reservas | Solicitar reserva de área comum |
| FUN-011 | Solicitações | Registrar e acompanhar solicitação |
| FUN-012 | Ocorrências | Cadastrar e consultar ocorrência |
| FUN-013 | Dashboard | Verificar indicadores operacionais |

Cada cenário deverá ser associado à versão implementada e às evidências de execução.

## 7. Testes do Aplicativo Android

### Escopo

- Instalação e inicialização.
- Exibição da tela de login.
- Autenticação.
- Navegação entre módulos.
- Envio de formulários.
- Comunicação com a API.
- Tratamento de falhas de conexão.
- Consulta e atualização de informações.
- Captura de imagens.
- Leitura de QR Code e códigos de barras.
- Exibição de relatórios.

### Verificações técnicas

- Compilação da aplicação.
- Ausência de encerramentos inesperados nos cenários testados.
- Análise de logs Android.
- Validação dos dados retornados pela API.
- Funcionamento das permissões solicitadas pelo sistema.

Os resultados devem indicar a versão do Android e o dispositivo ou emulador utilizado.

## 8. Testes de Inteligência Artificial e OCR

### Cenários

| ID | Teste | Resultado esperado |
|---|---|---|
| IA-001 | Capturar imagem de etiqueta | Imagem disponível para processamento |
| IA-002 | Reconhecer texto legível | Extração de informações relevantes |
| IA-003 | Processar etiqueta incompleta | Tratamento adequado da informação ausente |
| IA-004 | Revisar dados reconhecidos | Possibilidade de confirmação humana |
| IA-005 | Identificar destinatário incompatível | Sinalização para revisão |
| IA-006 | Falha do serviço de IA | Mensagem adequada e preservação do fluxo seguro |

A saída de IA deve ser considerada assistiva, não uma confirmação automática de veracidade.

## 9. Gestão de Defeitos

Defeitos identificados durante os testes devem ser registrados com informações suficientes para reprodução e correção.

### Modelo de registro

| Campo | Informação |
|---|---|
| Identificador | BUG-001 |
| Módulo | Área afetada |
| Descrição | Comportamento observado |
| Pré-condição | Estado necessário |
| Passos de reprodução | Sequência executada |
| Resultado esperado | Comportamento correto |
| Resultado obtido | Comportamento real |
| Severidade | Crítica, alta, média ou baixa |
| Status | Aberto, em correção, reteste ou encerrado |
| Evidência | Registro ou captura anonimizada |

Após a correção, o cenário deve ser submetido a reteste e, quando necessário, testes de regressão.

## 10. Critérios de Homologação

Uma funcionalidade pode ser considerada homologada quando:

- Os requisitos correspondentes estiverem identificados.
- Os cenários aplicáveis tiverem sido executados.
- Os resultados atenderem aos critérios de aceite.
- Não existirem defeitos bloqueadores pendentes.
- As permissões e regras de negócio tiverem sido verificadas.
- As evidências de teste estiverem registradas.
- O responsável autorizado tiver formalizado a aprovação.

Uma compilação bem-sucedida ou uma resposta HTTP 200 isolada não comprova a homologação integral do módulo.

## 11. Matriz de Acompanhamento

| Módulo | Execução | Resultado | Evidência |
|---|---|---|---|
| Autenticação | A confirmar | Não consolidado | Pendente de vinculação |
| Moradores | A confirmar | Não consolidado | Pendente de vinculação |
| Encomendas | A confirmar | Não consolidado | Pendente de vinculação |
| Visitantes | A confirmar | Não consolidado | Pendente de vinculação |
| Veículos | A confirmar | Não consolidado | Pendente de vinculação |
| Funcionários | A confirmar | Não consolidado | Pendente de vinculação |
| Reservas | A confirmar | Não consolidado | Pendente de vinculação |
| Solicitações | A confirmar | Não consolidado | Pendente de vinculação |
| OCR e IA | A confirmar | Não consolidado | Pendente de vinculação |
| Dashboard | A confirmar | Não consolidado | Pendente de vinculação |
| Multi-tenant | A confirmar | Não consolidado | Pendente de vinculação |

**Observação:** os campos não consolidados indicam ausência de evidências vinculadas a este documento, e não necessariamente que o teste nunca foi realizado.

## 12. Evidências de Testes

As evidências podem incluir:

- Capturas das interfaces.
- Resultados de requisições HTTP.
- Registros de compilação.
- Logs de testes, devidamente tratados.
- Resultados de validações funcionais.
- Histórico de correções e retestes.
- Registros de aceite de homologação.

As evidências publicadas devem utilizar dados fictícios ou anonimizados.

## 13. Considerações Finais

A estratégia de testes do CondoControlAI contempla diferentes camadas de validação, desde a interface Android até as regras de autorização e persistência de dados.

A documentação busca demonstrar práticas de:

- Quality Assurance (QA).
- Testes funcionais.
- Testes de integração.
- Validação de APIs REST.
- Análise de defeitos.
- Testes de segurança
