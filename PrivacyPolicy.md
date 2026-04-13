# Política de Privacidade do Controlaê

**Última atualização:** 13 de abril de 2026

A sua privacidade é importante para nós. Esta Política de Privacidade descreve como o aplicativo Controlaê ("Aplicativo") trata as informações quando você utiliza seus recursos.

---

## 1. Visão geral

O Controlaê é um aplicativo de controle financeiro pessoal. Em regra, os dados financeiros informados por você são armazenados localmente no seu dispositivo.

O Aplicativo também oferece recursos opcionais que utilizam serviços de terceiros, como login com Google, backup/restauração com Google Drive e relatórios de falha via Firebase Crashlytics. Nesses casos, alguns dados podem ser processados por esses serviços exclusivamente para viabilizar tais funcionalidades.

Nós não operamos um backend próprio para armazenar os seus dados financeiros.

---

## 2. Informações tratadas pelo Aplicativo

### 2.1. Dados armazenados localmente no dispositivo

O Aplicativo armazena localmente, no seu dispositivo, informações como:

- despesas e receitas
- categorias
- formas de pagamento
- cartões de crédito
- limites mensais
- preferências do aplicativo
- configurações de notificações
- preferências de backup automático
- status do tutorial e outras preferências de uso

Esses dados são utilizados para o funcionamento normal do Aplicativo.

### 2.2. Dados da conta Google

Se você optar por entrar com sua conta Google no recurso `Meu perfil`, o Aplicativo poderá acessar dados básicos da sua conta, como:

- nome
- endereço de e-mail
- foto de perfil

Esses dados são utilizados para autenticação e para exibição do perfil conectado dentro do Aplicativo.

### 2.3. Dados de backup e restauração

Se você optar por utilizar backup e restauração com Google Drive, o Aplicativo poderá enviar para a pasta privada do app no Google Drive um arquivo de backup contendo:

- dados financeiros cadastrados no app
- preferências e configurações do usuário
- metadados técnicos do backup

Atualmente, esse backup é enviado para a área privada `appDataFolder` do Google Drive. Essa área é oculta na interface comum do Drive e acessível apenas ao Aplicativo com a permissão concedida por você.

**Importante:** no estado atual do Aplicativo, o conteúdo do backup não é criptografado pelo Controlaê antes do envio. O arquivo é transmitido usando conexões seguras, mas não constitui criptografia ponta a ponta implementada pelo app.

### 2.4. Dados técnicos de falha e diagnóstico

O Aplicativo utiliza Firebase Crashlytics para identificar falhas e melhorar a estabilidade. Em caso de crash ou erro relevante, dados técnicos podem ser enviados ao Firebase, tais como:

- stack traces
- estado relevante do app no momento da falha
- metadados do dispositivo
- identificador técnico da instalação

Esses dados são usados para diagnóstico, correção de erros e melhoria da qualidade do Aplicativo.

---

## 3. Como usamos as informações

As informações tratadas pelo Aplicativo são usadas para:

- registrar e organizar suas finanças pessoais
- personalizar sua experiência no app
- autenticar sua conta Google, quando você escolher usar esse recurso
- criar e restaurar backups no Google Drive, quando você escolher usar esse recurso
- executar backups automáticos, se você ativar essa funcionalidade
- enviar lembretes e notificações do aplicativo
- monitorar falhas e melhorar estabilidade e segurança

---

## 4. Quando dados podem ser compartilhados com terceiros

O Controlaê não vende seus dados e não compartilha seus dados financeiros com terceiros para fins de marketing.

No entanto, determinados dados podem ser processados por terceiros nas seguintes hipóteses:

- **Google / Firebase Authentication:** para autenticar sua conta Google
- **Google Drive API:** para armazenar e restaurar backups na pasta privada do app
- **Firebase Crashlytics:** para coletar relatórios técnicos de falha e diagnóstico

Esse processamento ocorre apenas para viabilizar funcionalidades do Aplicativo ou melhorar sua estabilidade.

---

## 5. Permissões do Aplicativo

O Aplicativo pode solicitar permissões como:

- **Internet (`INTERNET`)**
  - usada para autenticação com Google
  - usada para backup/restauração com Google Drive
  - usada para comunicação com serviços Firebase

- **Notificações (`POST_NOTIFICATIONS`)**
  - usada para lembretes diários
  - usada para notificações relacionadas a backup automático

O uso dessas permissões é restrito às funcionalidades correspondentes.

---

## 6. Backup no Google Drive

Quando você utiliza o recurso de backup:

- o Aplicativo solicita acesso ao escopo `drive.appdata`
- os arquivos são gravados na pasta privada `appDataFolder`
- essa pasta não é exibida na interface padrão do Google Drive
- os arquivos dessa pasta não são compartilhados com outras aplicações pelo Controlaê

O backup manual e o backup automático só acontecem se você optar por usar essas funcionalidades.

---

## 7. Segurança

Adotamos medidas razoáveis para proteger as informações tratadas pelo Aplicativo.

Isso inclui, entre outros pontos:

- armazenamento local no dispositivo
- uso de autenticação Google para recursos protegidos
- uso de conexões seguras para comunicação com serviços externos
- uso de pasta privada do app no Google Drive para backups remotos

Apesar disso, nenhum método de armazenamento ou transmissão eletrônica é totalmente isento de risco.

---

## 8. Retenção e controle dos dados

Como regra:

- os dados locais permanecem no seu dispositivo até que você os exclua, desinstale o app ou restaure outro backup sobre eles
- os backups remotos permanecem na sua área privada do Google Drive até serem substituídos ou removidos
- os dados técnicos de falha podem ser retidos pelos serviços Firebase conforme as políticas desses serviços

Você pode interromper o uso de login Google, backup automático e backup no Drive a qualquer momento nas configurações do Aplicativo.

---

## 9. Crianças

O Controlaê não é direcionado a crianças menores de 13 anos, e não coletamos intencionalmente dados pessoais de crianças.

---

## 10. Alterações nesta Política

Esta Política de Privacidade pode ser atualizada periodicamente para refletir mudanças no Aplicativo, em requisitos legais ou em integrações de terceiros.

Quando isso ocorrer, a data de “Última atualização” será modificada no topo deste documento.

---

## 11. Contato

Se você tiver dúvidas sobre esta Política de Privacidade, entre em contato:

**E-mail:** cleriston.melo.pereira@gmail.com
