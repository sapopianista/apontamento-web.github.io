# 🚀 Apontamento de Horas Web

Um sistema web completo para apontamento de horas, gerenciamento de funcionários e cálculo de folha de pagamento. Desenvolvido como um aplicativo de página única (SPA) **em um único arquivo `index.html`**, utilizando Firebase para backend (Auth e Firestore) e Tailwind CSS para a interface.

Este projeto é ideal para pequenas empresas, departamentos de RH ou escritórios de contabilidade que precisam de uma solução leve, rápida e sem servidor (serverless) para gerenciar as horas dos funcionários, em conformidade com cálculos comuns da legislação brasileira.

## 📸 Screenshots

| Login | Lista de Funcionários | Apontamentos |
| :---: | :---: | :---: |
| <img width="1920" height="1080" alt="login" src="https://github.com/user-attachments/assets/e52966ff-dd50-44d0-86b8-0ab468cf5bf4" /> | <img width="1920" height="1080" alt="funcionarios" src="https://github.com/user-attachments/assets/2da00a9d-0f54-4f9c-9baf-3bd953de5457" /> | <img width="1920" height="1080" alt="apontamento" src="https://github.com/user-attachments/assets/904a9e58-9cea-4158-a0f4-79d2965c12ef" />


-----

## ✨ Principais Funcionalidades

O sistema é robusto e dividido em módulos claros:

### 🧑‍💼 Gestão (Admin)

  * **Gestão de Empresas:** Crie, edite e remova empresas (clientes do escritório, por exemplo).
  * **Gestão de Funcionários:**
      * Crie, edite e remova funcionários, vinculando-os a uma empresa.
      * Defina o tipo de remuneração: **Mensalista** ou **Horista**.
      * Configure salário, carga horária padrão e anotações.

### ⏰ Apontamento de Horas

  * **Planilha Mensal:** Interface intuitiva de calendário para lançar as horas.
  * **Múltiplas Entradas:** Suporte para até 4 marcações diárias (Entrada 1, Saída 1, Entrada 2, Saída 2).
  * **Status Diário:** Defina o status de cada dia (Trabalho, Falta, Folga, Atestado).
  * **Cálculos em Tempo Real:**
      * Total Trabalhado no dia.
      * Saldo diário (Banco de Horas).
      * Marcação de dias como **Feriado** (para cálculo de H.E. 100%).
  * **Resumo Mensal:** Um painel que sumariza o total de horas trabalhadas, saldo de banco, faltas, e os totais de H.E. e Adicional Noturno.

### 📊 Relatórios e Cálculos

  * **Relatório Geral:** Uma visão consolidada de todos os funcionários (filtrável por empresa) com o resumo do mês.
  * **Cálculo de Variáveis (R$):**
      * Calcula o valor a ser pago em **Hora Extra 50%** e **Hora Extra 100%**.
      * Calcula o valor do **Adicional Noturno** (com base no percentual e horário configurados).
      * Diferencia o cálculo para mensalistas (baseado em horas extras) e horistas (baseado no total de horas).
   
      * Obs: Os cálculos já são adequados as leis trabalhistas brasileiras, por exemplo o cálculo de adicional noturno em que a hora é convertida para 52,5 minutos.
        
  * **Exportação:** Exporte a planilha individual do funcionário para **PDF (Impressão)** ou **XLS (Excel)**.

### ⚙️ Configurações

  * **Adicional Noturno:** Defina o horário de início/fim e o percentual (ex: 20%).
  * **Tolerância:** Configure uma tolerância de minutos para o saldo diário (zerando saldos pequenos).

### 🔒 Autenticação Segura

  * **Login e Cadastro:** Sistema completo de autenticação por E-mail e Senha.
  * **Login Anônimo:** Usuários podem testar a aplicação anonimamente.
  * **Vinculação de Conta:** Permite que um usuário anônimo crie uma conta permanente (e-mail/senha) e mantenha seus dados.
  * **Persistência de Sessão:** Opção "Manter conectado".

-----

## 🛠️ Tecnologias Utilizadas

  * **Frontend:** HTML5, Tailwind CSS (via CDN)
  * **Backend (BaaS):** Firebase
      * **Firebase Authentication:** Para gerenciamento de usuários.
      * **Firebase Firestore:** Como banco de dados NoSQL em tempo real.
  * **JavaScript:** JavaScript moderno (ESM) sem frameworks, focado em manipulação de DOM.

-----

## 🚀 Como Implementar na sua Própria Conta Firebase

Este projeto é 100% *client-side* e pode ser hospedado gratuitamente. Siga estes passos para configurar sua própria versão:

### Passo 1: Criar o Projeto no Firebase

1.  Acesse o [Console do Firebase](https://console.firebase.google.com/).
2.  Clique em **"Adicionar projeto"** e siga as instruções para criar um novo projeto (ex: `meu-apontamento-web`).

### Passo 2: Ativar os Serviços Necessários

#### A. Autenticação (Authentication)

1.  No menu esquerdo, vá para **Authentication**.
2.  Clique em **"Get started"**.
3.  Na aba **"Sign-in method"**, ative os seguintes provedores:
      * **E-mail/senha**
      * **Anônimo**

#### B. Banco de Dados (Firestore)

1.  No menu esquerdo, vá para **Firestore Database**.
2.  Clique em **"Criar banco de dados"**.
3.  Selecione **"Iniciar em modo de produção"** (Recomendado) ou "modo de teste".
4.  Escolha o local do servidor (ex: `southamerica-east1` para São Paulo).
5.  Clique em **"Ativar"**.

### Passo 3: Obter a Configuração do seu App Web

1.  Na página principal do seu projeto no Firebase, clique no ícone de Web **`</>`** para "Adicionar um app da Web".
2.  Dê um apelido ao seu app (ex: "App Web") e clique em **"Registrar app"**.
3.  O Firebase exibirá um objeto de configuração `firebaseConfig`. **Copie este objeto inteiro.**

### Passo 4: Atualizar o arquivo `index.html`

1.  Abra o arquivo `index.html` em um editor de código (como o VS Code).
2.  Procure pela seção `<script type="module">` no final do arquivo.
3.  Encontre o comentário `// --- CONFIGURAÇÃO DO FIREBASE ---` (por volta da linha 930).
4.  **Substitua** o objeto `firebaseConfig` existente pelo objeto que você copiou do seu projeto:

<!-- end list -->

```javascript
        // --- CONFIGURAÇÃO DO FIREBASE ---
        const firebaseConfig = {
    		apiKey: "SEU_API_KEY",
    		authDomain: "SEU_AUTH_DOMAIN",
    		projectId: "SEU_PROJECT_ID",
    		storageBucket: "SEU_STORAGE_BUCKET",
    		messagingSenderId: "SEU_SENDER_ID",
    		appId: "SEU_APP_ID",
    		measurementId: "SEU_MEASUREMENT_ID"
	    };
        
        const appId = 'apontamento-web';
```

### Passo 5: Executar o Projeto

Você tem duas opções:

### Opção A: Publicar no GitHub Pages (Mais Simples, recomendo)

Esta é a maneira mais rápida de colocar seu projeto no ar gratuitamente, já que ele é apenas um arquivo `index.html`.

1.  **Crie um Repositório:** Crie um novo repositório **público** no seu GitHub (ex: `apontamento-web`).
2.  **Envie o Arquivo:** Faça o upload do seu arquivo `index.html` para este repositório.
3.  **Ative o GitHub Pages:**
    * No seu repositório, vá para **"Settings"** (Configurações).
    * No menu lateral, clique em **"Pages"**.
    * Na seção "Branch", selecione seu branch principal (geralmente `main` ou `master`) e deixe a pasta como `/ (root)`.
    * Clique em **"Save"**.
4.  **Pronto!** Após alguns minutos, seu site estará disponível publicamente no endereço:
    `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO`

#### Opção B: Publicar no Firebase Hosting

1.  Instale o Firebase CLI: `npm install -g firebase-tools`
2.  Faça login: `firebase login`
3.  Na pasta do seu projeto, inicie o Firebase: `firebase init`
4.  Escolha **Hosting**.
5.  Selecione seu projeto Firebase.
6.  Use `.` (ou `public`) como seu diretório público.
7.  Configure como "single-page app": **Sim**.
8.  **Não** sobrescreva o `index.html`.
9.  Coloque seu arquivo `index.html` dentro da pasta pública (ex: `public/index.html`).
10. Faça o deploy: `firebase deploy`

#### Opção C: Rodar Localmente (Mais fácil)

1.  Para que os módulos JavaScript (`import`) funcionem corretamente, você precisa servir o arquivo através de um servidor local.
2.  Se você usa o **VS Code**, instale a extensão [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer).
3.  Clique com o botão direito no arquivo `index.html` e selecione **"Open with Live Server"**.
4.  Pronto\! O sistema abrirá no seu navegador.
5.  

Pronto! Seu aplicativo estará online e funcionando\!

-----

## 📖 Como Usar a Aplicação

1.  **Crie sua conta:** Acesse a aplicação e crie sua conta de administrador.
2.  **Cadastre uma Empresa:** Vá para a aba **"Empresas"** e adicione sua primeira empresa.
3.  **Cadastre um Funcionário:** Vá para a aba **"Funcionários"**, clique em "Adicionar Funcionário" e vincule-o à empresa criada.
4.  **Inicie os Apontamentos:**
      * Vá para a aba **"Apontamentos"**.
      * Use os menus suspensos para selecionar a **Empresa** e o **Funcionário**.
      * A planilha do mês será carregada.
      * Preencha os horários (`HH:MM`), mude o status dos dias (ex: "Falta") ou marque feriados.
      * Clique em **"Salvar Alterações"** para enviá-las ao banco de dados.
5.  **Veja os Relatórios:**
      * Mude o mês/ano no seletor global para ver diferentes períodos.
      * Acesse a aba **"Relatório"** para ver o resumo financeiro de todos os funcionários.
