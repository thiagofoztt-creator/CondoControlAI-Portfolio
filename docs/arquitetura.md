# 🏢 Arquitetura do CondoControlAI

## 1. Visão Geral

O **CondoControlAI** é uma plataforma de gestão condominial desenvolvida com arquitetura cliente-servidor, integrando aplicativo Android, interfaces web, API REST, banco de dados relacional e recursos de Inteligência Artificial.

A solução foi concebida para centralizar processos administrativos e operacionais de condomínios, oferecendo controle de acesso, rastreabilidade das operações e separação lógica dos dados entre diferentes condomínios.

**Principais tecnologias:**

- **Mobile:** Kotlin, Jetpack Compose e Android.
- **Frontend Web:** HTML5, CSS3 e JavaScript.
- **Backend:** PHP 8 e API REST.
- **Banco de dados:** MySQL 8.
- **Autenticação:** JSON Web Token (JWT).
- **Inteligência Artificial:** OCR e processamento assistido de etiquetas.
- **Comunicação:** HTTPS e JSON.

---

## 2. Arquitetura Geral

O sistema utiliza uma API REST centralizada para conectar diferentes interfaces a uma camada compartilhada de regras de negócio.

```text
                  CONDOCONTROLAI
                        |
        +---------------+---------------+
        |               |               |
        v               v               v
   APP ANDROID     PAINEL WEB      PORTAL MORADOR
   Kotlin/Compose  HTML/CSS/JS      HTML/CSS/JS
        |               |               |
        +---------------+---------------+
                        |
                        v
                    API REST
                      PHP 8
                        |
          +-------------+-------------+
          |             |             |
          v             v             v
     AUTENTICAÇÃO   REGRAS DE      SERVIÇOS
        JWT         NEGÓCIO          DE IA
          |             |             |
          +-------------+-------------+
                        |
                        v
                     MySQL 8
                        |
                        v
             DADOS POR CONDOMÍNIO
```

Essa separação permite desenvolver e manter os componentes de apresentação, processamento e persistência de forma organizada.

---

## 3. Aplicativo Android

O aplicativo Android foi desenvolvido utilizando **Kotlin e Jetpack Compose**, com foco nas operações realizadas por funcionários e usuários autorizados.

### Responsabilidades

- Autenticação de usuários.
- Consulta e gerenciamento de informações autorizadas.
- Registro de entregas e encomendas.
- Captura de imagens para processamento OCR.
- Leitura de códigos QR e códigos de barras.
- Controle de visitantes.
- Consulta de histórico operacional.
- Exibição de indicadores e relatórios.

### Tecnologias e componentes

- Kotlin.
- Jetpack Compose.
- Android Jetpack.
- Retrofit e OkHttp.
- CameraX.
- Google ML Kit.
- Navegação entre telas e gerenciamento de estado.

A comunicação com o backend utiliza requisições HTTP sobre HTTPS, com troca de informações em JSON e autenticação nas operações protegidas.

---

## 4. Interfaces Web

A plataforma contempla interfaces web destinadas aos diferentes perfis de utilização.

### Painel Administrativo

Interface para gestão e acompanhamento dos processos condominiais.

Entre suas responsabilidades estão:

- Gerenciamento de moradores.
- Cadastro e consulta de funcionários.
- Controle de veículos e visitantes.
- Acompanhamento de encomendas.
- Administração de solicitações.
- Reservas de áreas comuns.
- Consultas e relatórios operacionais.

### Portal do Morador

Interface destinada ao acesso às informações e aos serviços permitidos aos moradores.

O acesso às funcionalidades depende das permissões atribuídas ao usuário autenticado.

---

## 5. Backend e API REST

O backend foi estruturado em **PHP**, utilizando endpoints REST para integrar o aplicativo Android e as interfaces web.

### Responsabilidades

- Autenticação.
- Validação de solicitações.
- Aplicação das regras de negócio.
- Controle de permissões.
- Acesso ao banco de dados.
- Processamento de operações.
- Integração com serviços de IA.
- Registro de ações relevantes para auditoria.

### Comunicação

O frontend envia requisições HTTP para a API, que valida as informações, executa as operações autorizadas e retorna respostas estruturadas em JSON.

A API utiliza códigos de status HTTP para indicar resultados, incluindo operações bem-sucedidas, entradas inválidas e tentativas não autorizadas.

---

## 6. Banco de Dados e Multi-Tenant

O CondoControlAI utiliza **MySQL** para armazenar informações operacionais e administrativas.

A arquitetura contempla um modelo **multi-tenant**, no qual diferentes condomínios compartilham a infraestrutura da aplicação, mas seus dados são separados logicamente.

### Isolamento de informações

As operações devem considerar o condomínio associado ao usuário autenticado.

O isolamento depende de controles implementados no backend e nas consultas ao banco de dados.

O identificador do condomínio não deve ser aceito isoladamente como prova de autorização.

### Benefícios da arquitetura

- Centralização das regras de acesso.
- Compartilhamento controlado da infraestrutura.
- Organização dos registros por condomínio.
- Possibilidade de expansão para novos condomínios.
- Manutenção centralizada da aplicação.

A eficácia do isolamento depende de testes específicos, inclusive tentativas de acesso entre condomínios diferentes.

---

## 7. Autenticação e Autorização

O sistema contempla autenticação baseada em **JWT (JSON Web Token)** e controle de acesso conforme o perfil do usuário.

### Perfis previstos

- Administrador.
- Zelador.
- Porteiro.
- Morador.

O backend deve validar a identidade, a validade do token, as permissões e o contexto do condomínio antes de executar operações protegidas.

### Princípios de segurança

- Autenticação obrigatória para recursos protegidos.
- Autorização por perfil.
- Restrição de consultas ao condomínio correspondente.
- Validação das entradas recebidas.
- Proteção das comunicações por HTTPS.
- Registro de eventos relevantes para auditoria.

A existência desses mecanismos na arquitetura não substitui testes de segurança, revisão de código e validação das configurações do ambiente.

---

## 8. Inteligência Artificial e OCR

O CondoControlAI incorpora recursos de Inteligência Artificial para auxiliar no processamento de informações de encomendas e etiquetas.

### Fluxo conceitual

```text
CAPTURA DA ETIQUETA
        |
        v
CÂMERA DO ANDROID
        |
        v
RECONHECIMENTO OCR
        |
        v
EXTRAÇÃO DE INFORMAÇÕES
        |
        v
PROCESSAMENTO ASSISTIDO POR IA
        |
        v
REVISÃO E VALIDAÇÃO
        |
        v
REGISTRO AUTORIZADO NA API
        |
        v
BANCO DE DADOS
```

### Objetivos

- Reduzir digitação manual.
- Facilitar a identificação de destinatários.
- Auxiliar no preenchimento dos registros.
- Diminuir inconsistências operacionais.
- Melhorar a rastreabilidade das entregas.

Os resultados de OCR e IA devem ser tratados como informações passíveis de erro, mantendo validação antes da confirmação de operações relevantes.

---

## 9. Auditoria e Rastreabilidade

A arquitetura contempla registros de auditoria associados às operações do sistema.

Esses registros permitem acompanhar ações como:

- Criação de registros.
- Alterações autorizadas.
- Operações de recebimento e retirada.
- Atualizações de situações operacionais.
- Eventos administrativos relevantes.

A rastreabilidade deve permitir identificar a operação, o responsável e o momento da execução, conforme as regras de acesso e retenção aplicáveis.

---

## 10. Privacidade e LGPD

O CondoControlAI foi concebido considerando princípios de proteção de dados pessoais e de acesso restrito às informações.

A documentação pública não disponibiliza:

- Dados reais de moradores.
- Documentos pessoais.
- Senhas e tokens.
- Chaves de API.
- Credenciais de banco de dados.
- Configurações internas de infraestrutura.
- Código-fonte privado.

Os mecanismos de retenção, controle de acesso e exclusão de dados devem ser verificados conforme os requisitos aplicáveis da LGPD.

---

## 11. Testes e Validação Técnica

O projeto contempla atividades de validação relacionadas aos principais componentes.

### API REST

- Validação de respostas HTTP.
- Testes de autenticação.
- Verificação das permissões.
- Testes de isolamento entre condomínios.
- Validação das informações recebidas.

### Aplicativo Android

- Compilação e execução.
- Testes de navegação.
- Integração com a API.
- Verificação de funcionalidades.
- Análise de logs e tratamento de falhas.

### Segurança

- Verificação de acesso não autorizado.
- Validação de tokens.
- Testes de permissões.
- Verificação das restrições multi-tenant.
- Revisão dos registros de auditoria.

A abrangência e os resultados de cada teste devem ser documentados separadamente, com evidências correspondentes.

---

## 12. Evolução da Plataforma

A separação entre interfaces, backend e persistência permite evoluir os módulos de maneira organizada.

Entre as possibilidades de evolução estão:

- Ampliação de integrações.
- Automação de processos administrativos.
- Expansão dos relatórios.
- Melhorias de observabilidade.
- Novos recursos de inteligência artificial.
- Ampliação dos testes automatizados.
- Fortalecimento dos controles de segurança.

---

## 13. Considerações Finais

O CondoControlAI demonstra a aplicação de conceitos de **desenvolvimento Full Stack, aplicativos Android, APIs REST, bancos de dados relacionais, autenticação, arquitetura multi-tenant e Inteligência Artificial**.

A documentação apresenta uma visão técnica da solução, preservando informações internas e o código-fonte original, mantido em repositório privado.

---

**CondoControlAI — Plataforma de Gestão Condominial com Inteligência Artificial.**
