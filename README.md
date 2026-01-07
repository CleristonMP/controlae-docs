# Controlaê - Seu Gerenciador Financeiro Pessoal

**Um aplicativo Android moderno para controle de despesas e receitas, construído com as melhores práticas de desenvolvimento nativo.**

---

## 🎯 Sobre o Projeto

Controlaê é um aplicativo financeiro intuitivo, projetado para ajudar os usuários a gerenciar suas finanças diárias de forma simples e eficaz. Com uma interface limpa e focada na experiência do usuário, o app permite o registro rápido de despesas e receitas, oferecendo relatórios visuais que facilitam a compreensão dos hábitos de consumo e a tomada de decisões financeiras mais inteligentes.

Este projeto foi desenvolvido como um portfólio para demonstrar habilidades em desenvolvimento Android nativo moderno, utilizando Jetpack Compose e uma arquitetura robusta baseada em MVVM.

## ✨ Funcionalidades Principais

*   **💸 Lançamentos:** Registre despesas e receitas de forma rápida.
*   **📊 Relatórios Visuais:** Acompanhe a evolução mensal, a distribuição de despesas por categoria e o balanço de entradas vs. saídas com gráficos interativos.
*   **💳 Gestão de Pagamentos:** Cadastre e gerencie cartões de crédito e outras formas de pagamento.
*   **📂 Categorização:** Organize suas transações com categorias personalizáveis.
*   **💰 Limite Mensal:** Defina um limite de gastos para o mês e acompanhe seu progresso.
*   **🔔 Notificações Inteligentes:** Receba lembretes diários para não se esquecer de registrar suas transações. As notificações são clicáveis, levando diretamente para a tela de adição de despesa.
*   **⚙️ Configurações Flexíveis:** Personalize o app de acordo com suas necessidades, ativando/desativando e definindo o horário das notificações.

## 🛠️ Tecnologias Utilizadas

Este projeto foi construído utilizando um stack tecnológico 100% Kotlin e alinhado com as recomendações do Google para o desenvolvimento Android moderno:

*   **Linguagem:** [Kotlin](https://kotlinlang.org/)
*   **UI:** [Jetpack Compose](https://developer.android.com/jetpack/compose) para uma interface declarativa e moderna.
*   **Arquitetura:** MVVM (Model-View-ViewModel) com fluxo de dados unidirecional (UDF).
*   **Injeção de Dependência:** [Hilt](https://dagger.dev/hilt/) para gerenciar dependências e facilitar a testabilidade.
*   **Programação Assíncrona:** [Coroutines](https://kotlinlang.org/docs/coroutines-overview.html) & [Flow](https://developer.android.com/kotlin/flow) para operações assíncronas e reativas.
*   **Navegação:** [Jetpack Navigation for Compose](https://developer.android.com/jetpack/compose/navigation) para gerenciar a navegação entre as telas.
*   **Persistência de Dados:**
    *   [Room](https://developer.android.com/training/data-storage/room) para o banco de dados local (transações, categorias, etc.).
    *   [DataStore](https://developer.android.com/topic/libraries/architecture/datastore) para salvar as preferências do usuário (tema, configurações de notificação).
*   **Trabalhos em Segundo Plano:** [WorkManager](https://developer.android.com/topic/libraries/architecture/workmanager) para agendar e executar as notificações diárias de forma confiável.
*   **Gráficos:** [MPAndroidChart](https://github.com/PhilJay/MPAndroidChart) para a exibição de gráficos de relatórios.
*   **Design System:** [Material Design 3](https://m3.material.io/).

## 🚀 Como Executar o Projeto

Para executar o projeto, você precisará do Android Studio na versão mais recente.

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/CleristonMP/controlae.git
    ```
2.  **Abra no Android Studio:**
    *   Abra o Android Studio.
    *   Clique em `File` > `Open`.
    *   Navegue até o diretório onde você clonou o projeto e o selecione.
3.  **Sincronize o Gradle:**
    *   Aguarde o Android Studio sincronizar e baixar todas as dependências do projeto.
4.  **Execute o aplicativo:**
    *   Selecione um emulador ou conecte um dispositivo físico.
    *   Clique no botão 'Run' (▶️).

## Informações Legais

*   [Política de Privacidade](docs/PrivacyPolicy.md)
*   [Termos de Serviço](docs/TermsOfService.md)

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---
