<div align="center">

# Controlaê

Aplicativo Android nativo para controle financeiro pessoal, com foco em despesas, entradas, metas de economia, contas a pagar, relatórios, lembretes e backup opcional com Google Drive.

</div>

---

## Sumário

- [Visão geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Stack técnica](#stack-técnica)
- [Arquitetura](#arquitetura)
- [Módulos e pontos importantes](#módulos-e-pontos-importantes)
- [Requisitos](#requisitos)
- [Como executar localmente](#como-executar-localmente)
- [Comandos úteis](#comandos-úteis)
- [Testes](#testes)
- [Banco de dados e persistência](#banco-de-dados-e-persistência)
- [Release e publicação](#release-e-publicação)
- [Observabilidade](#observabilidade)
- [Estado atual do projeto](#estado-atual-do-projeto)
- [Riscos conhecidos](#riscos-conhecidos)
- [Licença](#licença)

---

## Visão geral

O Controlaê é um app Android moderno em Kotlin com Jetpack Compose e arquitetura por camadas. O projeto já cobre um fluxo financeiro bem completo, incluindo:

- Home, Entradas, Despesas, Relatórios e Configurações
- limite mensal e orçamentos por categoria
- categorias, formas de pagamento e cartões de crédito
- contas recorrentes, parcelamentos e tela `Contas a pagar`
- metas de economia com aportes, resgates e resumo na Home/Relatórios
- backup e restauração com Google Drive `appDataFolder`
- backup automático com WorkManager
- captura opcional de notificações financeiras
- sugestões de lançamentos e automação opcional baseada em regras
- observabilidade com Firebase Crashlytics
- testes unitários e instrumentados para fluxos críticos

---

## Funcionalidades

### Controle financeiro

- Cadastro e edição de despesas e entradas
- Organização por categorias, formas de pagamento e cartões de crédito
- Definição e histórico de limite mensal
- Orçamentos por categoria
- Relatórios por ciclo financeiro

### Lembretes, contas e parcelamentos

- Lembretes diários configuráveis
- Lembretes de contas recorrentes próximas do vencimento
- Tela `Contas a pagar` para revisar ocorrências pendentes
- Parcelamentos em cartão com geração de ocorrências futuras

### Metas de economia

- Metas de economia com valor alvo, prazo opcional, aportes e resgates
- Resumo de metas de economia na Home e no relatório do ciclo

### Conta, backup e restauração

- Autenticação com conta Google em `Meu perfil`
- Backup manual e restauração no Google Drive privado
- Backup automático configurável por horário e política de rede

### Captura e automação de transações

- Captura opcional de notificações de transações bancárias
- Revisão e confirmação manual de transações sugeridas
- Automação opcional de despesas com regras explícitas

---

## Stack técnica

| Tecnologia | Uso no projeto |
|---|---|
| `Kotlin` | Linguagem principal |
| `Jetpack Compose` | Interface declarativa |
| `Material 3` | Componentes visuais |
| `MVVM` | Organização da apresentação |
| `Hilt` | Injeção de dependências |
| `Coroutines` e `Flow` | Programação assíncrona e fluxo de dados |
| `Navigation Compose` | Navegação entre telas |
| `Room` | Persistência local |
| `DataStore` | Preferências locais |
| `WorkManager` | Tarefas em background |
| `Firebase Auth` | Autenticação |
| `Credential Manager` | Credenciais de login |
| `Google Drive API` | Backup e restauração |
| `Firebase Crashlytics` | Reporte de falhas |

---

## Arquitetura

O app segue uma divisão principal entre apresentação, domínio, dados e infraestrutura local.

```text
app/src/main/java/com/cmp/controlae
├── auth
├── backup
├── data
│   ├── local
│   ├── preferences
│   └── repositories
├── domain
│   ├── model
│   └── usecase
├── navigation
├── notifications
├── observability
├── presentation
│   ├── contasapagar
│   ├── metas_economia
│   └── ...
├── transactioncapture
└── utils
```

### Camadas

| Camada | Responsabilidade |
|---|---|
| `presentation` | telas Compose, estados de UI e `ViewModel`s |
| `domain` | modelos e casos de uso para regras centrais, relatórios, compromissos e metas |
| `data` | entidades, DAOs, banco Room, preferências e repositórios |
| `auth` | integração com Google Sign-in e Firebase Auth |
| `backup` | payload, codec, sincronização com Google Drive, auto backup e validações |
| `notifications` | agendamento, workers, alertas e reagendamento por eventos do sistema |
| `observability` | logging, analytics e reporte de falhas |
| `transactioncapture` | listener de notificações, parser local, deduplicação, revisão e automação opcional |

---

## Módulos e pontos importantes

### Núcleo do app

- [MainActivity.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/MainActivity.kt): entrada principal do app
- [MainScreen.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/MainScreen.kt): navegação principal e rotas
- [AppDatabase.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/data/local/database/AppDatabase.kt): banco local Room

### Notificações e lembretes

- [NotificationScheduler.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/notifications/NotificationScheduler.kt): agendamento dos lembretes
- [NotificationWorker.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/notifications/NotificationWorker.kt): lembretes diários, alertas financeiros e contas a vencer

### Backup e restauração

- [DriveAppDataBackupService.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/backup/DriveAppDataBackupService.kt): sincronização de backup com Google Drive
- [AutoBackupWorker.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/backup/AutoBackupWorker.kt): execução do backup automático
- [BackupRestoreScreen.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/presentation/configuracoes/subscreens/backup/BackupRestoreScreen.kt): UI de backup, restauração e backup automático

### Contas, metas e relatórios

- [ContasAPagarScreen.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/presentation/contasapagar/ContasAPagarScreen.kt): contas recorrentes pendentes e vencimentos
- [MetasEconomiaScreen.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/presentation/metas_economia/MetasEconomiaScreen.kt): metas de economia e movimentos

### Captura de transações e observabilidade

- [NotificationTransactionListenerService.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/transactioncapture/NotificationTransactionListenerService.kt): captura opt-in de notificações financeiras
- [TransactionNotificationParser.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/transactioncapture/parser/TransactionNotificationParser.kt): parser local das notificações de transação
- [TransactionSuggestionReviewManager.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/transactioncapture/suggestions/TransactionSuggestionReviewManager.kt): confirmação, descarte e desfazer de sugestões
- [ObservabilityModule.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/main/java/com/cmp/controlae/observability/ObservabilityModule.kt): bindings de observabilidade

---

## Requisitos

- Android Studio atualizado
- JDK 11
- Android SDK compatível com `compileSdk 35`
- Emulador ou dispositivo Android

---

## Como executar localmente

### 1. Clone o repositório

```bash
git clone https://github.com/CleristonMP/controlae.git
cd controlae
```

### 2. Abra o projeto no Android Studio

### 3. Adicione o arquivo do Firebase em:

```text
app/google-services.json
```

Observações:

- o arquivo `google-services.json` deve corresponder ao projeto Firebase correto
- para debug, o Firebase precisa ter também o app `com.cmp.controlae.debug`
- a autenticação Google precisa estar habilitada no Firebase Authentication
- a Google Drive API precisa estar habilitada no projeto Google Cloud associado

### 4. Se quiser gerar release assinada, configure `keystore.properties` na raiz do projeto ou exporte variáveis de ambiente com:

- `storeFile`
- `storePassword`
- `keyAlias`
- `keyPassword`

Exemplo:

```properties
storeFile=../keystore/controlae-release.jks
storePassword=your-store-password
keyAlias=controlae
keyPassword=your-key-password
```

### 5. Sincronize o Gradle e execute pelo Android Studio ou pela linha de comando

---

## Comandos úteis

### Compilar debug

```powershell
./gradlew :app:compileDebugKotlin
```

### Rodar testes unitários

```powershell
./gradlew :app:testDebugUnitTest
```

### Rodar testes instrumentados

```powershell
./gradlew :app:connectedDebugAndroidTest
```

### Gerar APK de release

```powershell
./gradlew :app:assembleRelease
```

### Gerar AAB de release

```powershell
./gradlew :app:bundleRelease
```

---

## Testes

O projeto já possui cobertura automatizada para áreas importantes do núcleo:

- cálculo de ciclo financeiro
- infraestrutura de backup e restauração
- parser e deduplicação de notificações financeiras
- automação e desfazer de lançamentos automáticos
- metas de economia e relatórios do ciclo
- validação semântica do backup
- DAOs e migrations do Room
- fluxos Compose críticos de formulários e estados visuais

O runner instrumentado usa Hilt:

- [HiltTestRunner.kt](/C:/Users/cmelo/AndroidStudioProjects/Controlae/app/src/androidTest/java/com/cmp/controlae/HiltTestRunner.kt)

---

## Banco de dados e persistência

O app usa Room para persistência local e já possui:

- schema exportado
- migração real de banco
- teste instrumentado de migration
- dados iniciais pré-populados
- suporte a sugestões de transação e histórico de automação
- suporte a agendamentos recorrentes, ocorrências de despesas e metas de economia

---

## Release e publicação

Os passos operacionais e checklists ficam em:

- [RELEASE.md](/C:/Users/cmelo/AndroidStudioProjects/Controlae/docs/RELEASE.md)
- [GO_NO_GO.md](/C:/Users/cmelo/AndroidStudioProjects/Controlae/docs/GO_NO_GO.md)
- [PLAY_STORE_METADATA.md](/C:/Users/cmelo/AndroidStudioProjects/Controlae/docs/PLAY_STORE_METADATA.md)
- [PRIVACY_POLICY.md](/C:/Users/cmelo/AndroidStudioProjects/Controlae/docs/PRIVACY_POLICY.md)
- [TERMS_OF_SERVICE.md](/C:/Users/cmelo/AndroidStudioProjects/Controlae/docs/TERMS_OF_SERVICE.md)

Antes de publicar, o fluxo esperado é:

1. rodar testes unitários e instrumentados
2. gerar `assembleRelease` e `bundleRelease`
3. validar smoke test da build `release`
4. revisar o checklist de go/no-go
5. revisar metadados da Play Store

---

## Observabilidade

O projeto usa Firebase Crashlytics para reporte de falhas em release. Para isso funcionar corretamente, verifique:

- `app/google-services.json` presente
- apps Firebase configurados para `com.cmp.controlae` e `com.cmp.controlae.debug`
- upload de mapping habilitado na build de release

---

## Estado atual do projeto

Hoje o Controlaê já conta com:

- base arquitetural organizada
- persistência com migration
- autenticação Google integrada ao app
- backup/restauração com Google Drive privado
- backup automático configurável
- metas de economia integradas à Home, Relatórios e backup
- contas recorrentes, parcelamentos e lembretes de contas a vencer
- captura opcional de transações com processamento local
- cobertura automatizada do núcleo
- Crashlytics integrado

---

## Riscos conhecidos

- os gráficos já usam componentes internos em Compose, sem dependência alpha de terceiros
- os riscos remanescentes estão mais ligados a refinamento visual, comportamento em background e cobertura de interface

---

## Licença

Este projeto está sob a licença MIT. Veja [LICENSE](/C:/Users/cmelo/AndroidStudioProjects/Controlae/LICENSE) para mais detalhes.
