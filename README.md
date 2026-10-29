# 🏢 CondoControlAI

### Plataforma de Gestão Condominial | Android • Web • API REST • Inteligência Artificial

O **CondoControlAI** é um projeto de software voltado à modernização da gestão condominial, integrando aplicativo Android, painel administrativo web, portal do morador e uma API REST centralizada.

A plataforma reúne recursos de gestão operacional, controle de acesso, automação de processos e inteligência artificial, com arquitetura multi-tenant para atender diferentes condomínios.

> 🔒 **Repositório de portfólio:** esta é uma apresentação técnica do projeto. O código-fonte original permanece privado.

---

## 🎯 Objetivo

Centralizar processos administrativos e operacionais dos condomínios, buscando:

- Maior rastreabilidade das operações.
- Organização das informações.
- Controle de acesso por perfil.
- Redução de tarefas manuais.
- Integração entre funcionários, moradores e administração.
- Apoio à tomada de decisões por meio de indicadores.

## 🚀 Funcionalidades

| Módulo | Recursos |
|---|---|
| 📦 Encomendas | Recebimento, fotografias, rastreamento, histórico e confirmação de retirada |
| 🤖 Inteligência Artificial | OCR, reconhecimento de etiquetas e revisão humana dos dados |
| 👥 Moradores | Cadastro, consultas e associação a blocos e apartamentos |
| 🚶 Visitantes | Registro de entrada, saída e histórico |
| 🚗 Veículos | Cadastro e associação às unidades |
| 👷 Funcionários | Cadastro, perfis de acesso e registro de ponto |
| 📅 Reservas | Solicitações e gerenciamento de áreas comuns |
| 📝 Ocorrências | Registro e acompanhamento de ocorrências |
| 📊 Administração | Dashboard, relatórios, consultas e auditoria |
| 🌐 Portal do Morador | Consultas, solicitações e serviços autorizados |
| 🔐 Segurança | Autenticação JWT, autorização por perfil e isolamento por condomínio |

A disponibilidade de cada recurso depende da versão implementada e da homologação correspondente.

---

## 🛠️ Tecnologias

| Camada | Tecnologias |
|---|---|
| Android | Kotlin, Jetpack Compose, Room, Hilt, Retrofit e OkHttp |
| Recursos Android | CameraX e Google ML Kit |
| Backend | PHP 8 e API REST |
| Banco de dados | MySQL 8 |
| Frontend Web | HTML5, CSS3 e JavaScript |
| Autenticação | JSON Web Token (JWT) |
| Arquitetura | Cliente-servidor e multi-tenant |
| Inteligência Artificial | OCR e integração com serviços de IA |
| Ferramentas | Android Studio, VS Code, Git e GitHub |

---

## 🏗️ Arquitetura do Sistema

O CondoControlAI utiliza uma arquitetura cliente-servidor, com uma API REST responsável por centralizar regras de negócio, autenticação, autorização e acesso aos dados.

```text
                 CONDOCONTROLAI
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
   APP ANDROID     PAINEL WEB     PORTAL MORADOR
   Kotlin/Compose  HTML/CSS/JS     HTML/CSS/JS
        |              |              |
        +--------------+--------------+
                       |
                       v
                  API REST PHP
                       |
             +---------+---------+
             |                   |
             v                   v
        REGRAS DE             INTEGRAÇÃO
         NEGÓCIO              COM IA
             |
             v
           MySQL
             |
             v
       DADOS POR CONDOMÍNIO
```

O aplicativo Android também utiliza recursos de câmera e reconhecimento de texto para apoiar o processamento de etiquetas.

A separação lógica entre condomínios é aplicada no backend, conforme a identidade e as permissões do usuário autenticado.

O diagrama apresenta uma visão conceitual, sem expor configurações internas da infraestrutura.

---

## 🔐 Segurança e Privacidade

A arquitetura contempla mecanismos de proteção e controle de acesso, incluindo:

- Autenticação baseada em JWT.
- Autorização por perfil de usuário.
- Restrição de dados ao condomínio correspondente.
- Validação das requisições no backend.
- Registro de ações relevantes para auditoria.
- Comunicação protegida por HTTPS.
- Regras de retenção de informações.

**Importante:** a existência desses mecanismos não representa certificação de segurança nem comprovação automática de conformidade com a LGPD. Sua eficácia depende de validação técnica e das configurações do ambiente.

---

## 🧪 Qualidade de Software e Validação

O desenvolvimento do CondoControlAI contempla práticas de qualidade de software, com atenção a:

- Testes funcionais.
- Testes de API REST.
- Validação de respostas HTTP e JSON.
- Autenticação e autorização.
- Isolamento de dados entre condomínios.
- Integração Android/API.
- Inspeção de logs.
- Identificação e correção de defeitos.
- Testes de regressão.
- Critérios de aceite e homologação.

**Situação das evidências:** o repositório contém o plano de testes e um inventário de verificações, mas os logs originais, capturas de execução e relatórios comprobatórios ainda não foram anexados. A documentação não apresenta os cenários sem evidência como automaticamente aprovados.

---

## 📚 Documentação Técnica

Os documentos abaixo detalham os principais aspectos do projeto:

| Documento | Conteúdo |
|---|---|
| [🏗️ Arquitetura](docs/arquitetura.md) | Componentes, comunicação, banco de dados, segurança e multi-tenant |
| [⚙️ Funcionalidades](docs/funcionalidades.md) | Módulos, recursos e regras de negócio |
| [🧪 Testes e Homologação](docs/testes-e-homologacao.md) | Estratégia de QA, cenários e critérios de aceite |
| [📋 Evidências de Testes](docs/evidencias-testes.md) | Inventário, registros históricos e situação das evidências públicas |

---

## 📱 Demonstrações do Aplicativo Android

As imagens abaixo apresentam interfaces desenvolvidas para o CondoControlAI.

<table>
  <tr>
    <td align="center">
      <img src="imagens/condocontrolai_01.jpg" width="210" alt="Tela de abertura do CondoControlAI">
      <p><strong>01 — Tela de Abertura</strong></p>
      <p>Identidade visual do aplicativo.</p>
    </td>
    <td align="center">
      <img src="imagens/condocontrolai_02.jpg" width="210" alt="Tela de login do CondoControlAI">
      <p><strong>02 — Autenticação</strong></p>
      <p>Interface de acesso ao sistema.</p>
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <img src="imagens/condocontrolai_19.jpg" width="230" alt="Relatório operacional do CondoControlAI">
      <p><strong>03 — Relatório Operacional</strong></p>
      <p>Visualização de indicadores da gestão condominial.</p>
    </td>
  </tr>
</table>

> As imagens demonstram interfaces do projeto. Elas não substituem evidências de execução de testes ou homologação. Informações pessoais e confidenciais devem ser removidas antes da publicação.

---

## 👨‍💻 Desenvolvimento

Projeto desenvolvido por **Thiago Almeida Teles**, envolvendo atividades de:

- Levantamento e análise de requisitos.
- Modelagem de dados.
- Desenvolvimento Android.
- Desenvolvimento de APIs REST.
- Desenvolvimento de interfaces web.
- Integração com banco de dados.
- Implementação de regras de autenticação e autorização.
- Integração de recursos de inteligência artificial.
- Testes, diagnóstico de falhas e validação funcional.
- Documentação técnica.

---

## 📬 Contato

- [Perfil no GitHub](https://github.com/thiagofoztt-creator)
- [LinkedIn](https://www.linkedin.com/in/thiago-de-almeida-teles-9924a13a5)

---

**CondoControlAI — Plataforma de Gestão Condominial com Inteligência Artificial.**

**Código-fonte original privado.** Este repositório destina-se à apresentação técnica e profissional do projeto.
