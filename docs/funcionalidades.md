# 🏢 Funcionalidades — CondoControlAI

**Plataforma de Gestão Condominial | Android • Web • Backend • Inteligência Artificial**

## 1. Visão Geral

O **CondoControlAI** é uma plataforma de gestão condominial desenvolvida para integrar processos administrativos, operacionais e de comunicação entre funcionários, administradores e moradores.

A solução é composta por:

- Aplicativo Android desenvolvido em Kotlin e Jetpack Compose.
- Painel administrativo web.
- Portal web do morador.
- Backend com API REST em PHP.
- Banco de dados relacional MySQL.
- Recursos de Inteligência Artificial e OCR.

A plataforma utiliza uma arquitetura multi-tenant, com separação lógica dos dados por condomínio e controle de acesso conforme o perfil do usuário.

**Nota:** este documento apresenta o escopo funcional e os mecanismos previstos na solução. A disponibilidade efetiva de cada funcionalidade depende da versão instalada, das configurações do ambiente e da homologação correspondente.

---

## 2. Gestão de Moradores e Unidades

Módulo destinado à organização cadastral de moradores, blocos e unidades habitacionais.

### Funcionalidades

- Cadastro e atualização de moradores.
- Associação de moradores a blocos e apartamentos.
- Consulta e pesquisa cadastral.
- Organização das informações por condomínio.
- Consulta de informações conforme o perfil de acesso.
- Histórico de operações cadastrais relevantes.

### Regras de negócio

- Cada registro deve estar associado ao condomínio correspondente.
- Usuários somente podem acessar informações autorizadas.
- O backend deve validar as permissões antes das operações protegidas.

---

## 3. Gestão de Encomendas

Módulo destinado ao registro, acompanhamento e controle de recebimento e retirada de encomendas.

### Funcionalidades

- Cadastro de encomendas recebidas.
- Registro fotográfico.
- Identificação de destinatário, bloco e apartamento.
- Registro de transportadora e código de rastreamento.
- Consulta de encomendas pendentes.
- Histórico de recebimentos e entregas.
- Confirmação de retirada.
- Baixa manual de encomendas.
- Leitura de QR Code e códigos de barras.
- Apoio de OCR e Inteligência Artificial na leitura de etiquetas.

### Rastreabilidade

As operações podem contemplar informações como:

- Data e horário.
- Usuário responsável.
- Situação da encomenda.
- Identificação de quem realizou a retirada.
- Observações pertinentes.
- Histórico das alterações e confirmações.

### Regras de negócio

- A retirada deve ser registrada de forma rastreável.
- O acesso às informações depende das permissões do usuário.
- Os dados identificados por OCR ou IA devem ser conferidos antes de operações relevantes.

---

## 4. Controle de Visitantes

Módulo operacional para registro e acompanhamento de acessos de visitantes.

### Funcionalidades

- Cadastro de visitantes.
- Registro de entrada.
- Registro de saída.
- Identificação da unidade relacionada à visita.
- Consulta de visitantes cadastrados.
- Histórico de movimentações.
- Pesquisa de registros.

### Objetivo

Auxiliar as rotinas da portaria, mantendo informações organizadas para acompanhamento operacional.

---

## 5. Gestão de Veículos

Módulo destinado ao controle cadastral de veículos relacionados aos condomínios.

### Funcionalidades

- Cadastro de veículos.
- Associação a moradores ou unidades.
- Atualização de informações.
- Consulta de veículos cadastrados.
- Pesquisa de registros.
- Controle de permissões de acesso aos cadastros.

Os dados dos veículos devem permanecer restritos aos usuários devidamente autorizados.

---

## 6. Gestão de Funcionários

Módulo para administração de funcionários e suas operações.

### Funcionalidades

- Cadastro de funcionários.
- Associação de perfis e permissões.
- Consulta e atualização cadastral.
- Registro de ponto.
- Controle de entrada e saída.
- Registro de intervalos.
- Histórico operacional.

### Controle de acesso

As operações administrativas e os registros de funcionários dependem das permissões estabelecidas para cada perfil.

---

## 7. Ocorrências e Solicitações

Módulos destinados ao acompanhamento de situações operacionais e demandas encaminhadas à administração.

### Ocorrências

- Registro de ocorrências.
- Descrição dos fatos.
- Identificação de data e responsável.
- Consulta dos registros.
- Acompanhamento de informações e histórico.

### Solicitações

- Abertura de solicitações.
- Encaminhamento para análise administrativa.
- Aprovação ou recusa, conforme as regras aplicáveis.
- Consulta da situação das solicitações.
- Histórico de movimentações.

Esses recursos apoiam a comunicação entre moradores, funcionários e administração.

---

## 8. Reservas de Áreas Comuns

Módulo voltado à organização de solicitações e reservas de espaços compartilhados.

### Funcionalidades

- Consulta de áreas disponíveis no cadastro.
- Solicitação de reserva.
- Registro de data e período.
- Consulta de reservas existentes.
- Acompanhamento das solicitações.
- Gestão administrativa das reservas.

A confirmação de uma reserva deve respeitar as regras definidas pelo condomínio e as permissões do usuário.

---

## 9. Painel Administrativo

Interface web destinada à centralização das operações de gestão condominial.

### Funcionalidades

- Dashboard com indicadores operacionais.
- Gestão de moradores.
- Gestão de funcionários.
- Consulta de visitantes e veículos.
- Acompanhamento de encomendas.
- Administração de solicitações.
- Controle de reservas.
- Consulta de ocorrências.
- Pesquisa de registros.
- Relatórios e informações de auditoria.

### Indicadores operacionais

O painel pode apresentar métricas como:

- Quantidade de moradores ativos.
- Encomendas pendentes.
- Visitantes registrados.
- Veículos cadastrados.
- Funcionários ativos.
- Outros indicadores conforme os módulos disponíveis.

Os indicadores dependem das informações existentes no banco de dados e das permissões de consulta.

---

## 10. Portal do Morador

Interface destinada ao acesso de moradores autenticados.

### Funcionalidades

- Autenticação.
- Consulta de informações autorizadas.
- Acompanhamento de encomendas.
- Envio e consulta de solicitações.
- Acesso a informações e avisos.
- Solicitação ou consulta de reservas.
- Consulta de históricos disponíveis ao perfil.

### Segurança

O morador deve acessar somente as informações relacionadas ao seu contexto autorizado.

O backend é responsável por validar os critérios de autenticação, autorização e isolamento de dados.

---

## 11. Inteligência Artificial e OCR

O CondoControlAI contempla recursos de inteligência artificial para auxiliar nas operações de recebimento de encomendas.

### Funcionalidades

- Captura de imagens de etiquetas.
- Reconhecimento de texto por OCR.
- Extração de informações relevantes.
- Apoio ao reconhecimento de destinatários.
- Identificação de informações de transportadoras e rastreamento.
- Preenchimento assistido de campos.
- Revisão humana das informações reconhecidas.

### Fluxo funcional

```text
CAPTURA DA ETIQUETA
        |
        v
PROCESSAMENTO OCR
        |
        v
EXTRAÇÃO DOS DADOS
        |
        v
PROCESSAMENTO ASSISTIDO POR IA
        |
        v
REVISÃO DAS INFORMAÇÕES
        |
        v
CONFIRMAÇÃO DO REGISTRO
```

A inteligência artificial atua como recurso de apoio. Dados gerados automaticamente podem conter erros e devem ser submetidos às validações necessárias.

---

## 12. Autenticação, Permissões e Segurança

A arquitetura contempla mecanismos para restringir o acesso às funcionalidades e proteger as informações dos condomínios.

### Mecanismos

- Autenticação baseada em JWT.
- Controle de permissões por perfil.
- Validação das requisições no backend.
- Separação lógica dos dados por condomínio.
- Restrição de acesso a recursos protegidos.
- Registro de operações relevantes.
- Comunicação por HTTPS nos ambientes configurados.

### Perfis previstos

| Perfil | Responsabilidade principal |
|---|---|
| Administrador | Gestão administrativa e acompanhamento geral |
| Zelador | Operações autorizadas de gestão e acompanhamento |
| Porteiro | Rotinas operacionais de portaria |
| Morador | Consulta e solicitação de serviços autorizados |

A matriz detalhada de permissões deve ser validada conforme as regras de negócio e a versão do sistema.

---

## 13. Auditoria e Histórico

Mecanismos destinados ao acompanhamento das operações realizadas na plataforma.

### Informações de auditoria

- Usuário responsável.
- Tipo de ação executada.
- Data e horário da operação.
- Identificação do registro envolvido.
- Informações necessárias à rastreabilidade.

### Objetivos

- Facilitar consultas operacionais.
- Apoiar a investigação de inconsistências.
- Melhorar o acompanhamento administrativo.
- Preservar o histórico das ações relevantes.

A consulta aos registros de auditoria deve respeitar permissões e políticas de retenção.

---

## 14. Relatórios e Consultas

A plataforma contempla mecanismos de consulta de informações operacionais e administrativas.

### Funcionalidades

- Indicadores no dashboard.
- Consulta de cadastros.
- Histórico de encomendas.
- Consulta de visitantes.
- Acompanhamento de solicitações.
- Informações sobre veículos e funcionários.
- Consultas relacionadas às ocorrências.
- Acompanhamento de registros operacionais.

Filtros, exportações e formatos de relatórios dependem da implementação e da versão homologada de cada módulo.

---

## 15. Qualidade de Software e Testes

O desenvolvimento do CondoControlAI contempla atividades de validação funcional, integração e análise técnica.

### API REST

- Verificação de respostas HTTP.
- Validação de autenticação.
- Verificação de operações autorizadas e não autorizadas.
- Testes de integração com o banco de dados.
- Verificação das regras de isolamento multi-tenant.

### Android

- Compilação e execução do aplicativo.
- Testes de navegação.
- Validação de formulários.
- Verificação da comunicação com a API.
- Inspeção de logs.
- Testes de recursos associados à câmera e leitura de códigos.

### Testes funcionais

- Operações de cadastro.
- Consultas e pesquisas.
- Fluxos de recebimento e retirada.
- Controle de visitantes.
- Solicitações e reservas.
- Verificação das permissões.

O escopo efetivamente executado, os resultados e as pendências devem constar em evidências de teste e registros de homologação específicos.

---

## 16. Privacidade e Proteção de Dados

O CondoControlAI contempla requisitos de proteção de dados e controle de acesso compatíveis com a natureza de uma aplicação de gestão condominial.

Entre as preocupações técnicas estão:

- Acesso restrito às informações pessoais.
- Separação de dados entre condomínios.
- Proteção de credenciais.
- Controle de permissões.
- Registro de operações.
- Políticas de retenção e descarte.
- Revisão de informações processadas por IA.

As medidas devem ser avaliadas em conjunto com as obrigações aplicáveis da LGPD.

---

## 17. Disponibilidade e Homologação

Este documento representa o **escopo funcional do projeto**, e não uma certificação de disponibilidade integral em produção.

Para cada funcionalidade, devem ser considerados:

| Situação | Significado |
|---|---|
| Implementada | Recurso desenvolvido na versão correspondente |
| Em validação | Recurso submetido a testes ou homologação |
| Homologada | Recurso aprovado segundo critérios definidos |
| Planejada | Recurso previsto, mas ainda não concluído |

A classificação específica deve ser mantida em registros de evolução, testes e homologação.

---

## 18. Evolução do Projeto

Possíveis melhorias e iniciativas futuras incluem:

- Ampliação dos testes automatizados.
- Melhorias de observabilidade.
- Evolução dos relatórios.
- Otimização de fluxos operacionais.
- Aperfeiçoamento das integrações de IA.
- Expansão das funcionalidades de autoatendimento.
- Melhorias contínuas de desempenho e segurança.

---

## 19. Considerações Finais

O CondoControlAI reúne funcionalidades de gestão condominial, desenvolvimento Android, interfaces web, APIs REST, banco de dados relacional e inteligência artificial.

O projeto demonstra a aplicação de conhecimentos em:

- Engenharia de software.
- Desenvolvimento Full Stack.
- Integração de sistemas.
- Modelagem e persistência de dados.
- Autenticação e autorização.
- Arquitetura multi-tenant.
- Inteligência Artificial.
- Qualidade de software e testes.

A implementação original permanece privada. Este repositório apresenta apenas informações técnicas e materiais de portfólio apropriados para divulgação pública.

---

**CondoControlAI — Gestão Condominial com Tecnologia, Segurança e Inteligência Artificial.**
