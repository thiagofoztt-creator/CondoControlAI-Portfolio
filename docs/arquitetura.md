
# Arquitetura do CondoControlAI

## Visão geral

O CondoControlAI utiliza uma arquitetura cliente-servidor, integrando aplicativos e interfaces web a uma API REST centralizada.

## Componentes

- **Aplicativo Android:** Kotlin e Jetpack Compose.
- **Painéis Web:** HTML, CSS e JavaScript.
- **Backend:** API REST desenvolvida em PHP.
- **Banco de dados:** MySQL.
- **Inteligência Artificial:** serviços de processamento de etiquetas e OCR.

## Fluxo simplificado

```text
Aplicativo Android ──┐
                     ├── API REST PHP ── MySQL
Painéis Web ─────────┘
```

## Segurança

A arquitetura contempla autenticação JWT, autorização baseada em perfis e separação lógica de dados por condomínio.

A efetividade desses controles depende de validação técnica e testes de segurança.

## Privacidade

Esta documentação descreve apenas a arquitetura geral. Código-fonte, credenciais, dados pessoais e configurações internas não são divulgados.
