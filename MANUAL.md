# MANUAL
## INSTALAÇÃO DO VISUAL STUDIO PARA WPF:
### 1. DOWNLOAD E INSTALAÇÃO:
- Acesse o site oficial do Visual Studio: [Visual Studio](https://visualstudio.microsoft.com/)
- Clique em "Baixar" na versão desejada (Community, Professional, Enterprise). A versão Community é gratuita e geralmente suficiente para a maioria dos desenvolvedores.
- Execute o instalador baixado (`vs_installer.exe`).

### 2. ESCOLHA DA EDIÇÃO:
- Ao abrir o instalador, selecione a edição que você baixou. Clique em "Continuar".

### 3. SELECIONANDO WORKLOADS:
- Após iniciar o instalador, você verá uma tela de "Workloads". Esses são conjuntos de ferramentas e bibliotecas que você pode instalar conforme necessário.
- Para desenvolvimento de aplicações WPF em C#, selecione:
  - Desenvolvimento de aplicativos .NET para desktop.
  - Clique em "Instalar" para iniciar a instalação.

### 4. FINALIZANDO A INSTALAÇÃO:
- Aguarde o término da instalação. Isso pode levar algum tempo dependendo da quantidade de workloads selecionadas e da velocidade da sua conexão com a internet.

## CONFIGURAÇÃO INICIAL:
### 1. PRIMEIRO LANÇAMENTO:
- Ao abrir o Visual Studio pela primeira vez, você será solicitado a fazer login com uma conta da Microsoft. Você pode usar uma conta existente ou criar uma nova.
- Após o login, escolha a configuração de ambiente de desenvolvimento. Por exemplo, se você for desenvolver principalmente em C#, selecione a configuração "C#".

### 2. CRIANDO UM NOVO PROJETO WPF:
- Na tela inicial do Visual Studio, clique em "Criar um novo projeto".
- Na janela "Criar um novo projeto", você pode escolher entre vários tipos de projetos. Vamos criar um projeto WPF para começar.
- Use a barra de pesquisa para procurar "WPF App (.NET Framework)" ou "WPF App (.NET Core)" dependendo da sua preferência.
- Clique em "Avançar".

### 3. CONFIGURANDO O PROJETO:
- Dê um nome ao seu projeto (por exemplo, "MeuProjetoWPF").
- Escolha um local para salvar o projeto.
- Clique em "Criar".

## ESTRUTURA DE DIRETÓRIOS DO PROJETO:
Após criar seu projeto, você verá a estrutura básica de diretórios no "Solution Explorer" à direita. Aqui está uma visão geral dos componentes principais:

### 1. SOLUTION (`.SLN`):
- A solução é o contêiner que pode conter múltiplos projetos. O arquivo `.sln` gerencia a solução inteira.

### 2. PROJETO (`.CSPROJ`):
- Dentro da solução, você terá um projeto principal com um arquivo de configuração (`.csproj` para C#).

### 3. PASTAS E ARQUIVOS DO PROJETO:
- **Properties:** Contém arquivos de configuração do projeto, como `AssemblyInfo.cs`.
- **References:** Referências a bibliotecas e pacotes NuGet usados pelo projeto.
- **MainWindow.xaml:** Exemplo de janela principal no projeto WPF.
- **App.xaml:** Contém recursos e configurações globais da aplicação.

## EXEMPLO DE CÓDIGO:
Vamos adicionar um código simples ao `MainWindow.xaml.cs` para garantir que tudo está funcionando:

```csharp
using System.Windows;

namespace MeuProjetoWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Aplicativo WPF iniciado!");
        }
    }
}
```

## EXECUTANDO O PROJETO:
### 1. COMPILAÇÃO E EXECUÇÃO:
- Para compilar e executar o projeto, clique no botão "Iniciar" (um ícone de play verde) ou pressione `F5`.
- A janela principal do WPF será exibida com a mensagem "Aplicativo WPF iniciado!".

## EXPLORANDO MAIS:
Com o Visual Studio configurado e seu primeiro projeto WPF funcionando, você pode explorar mais:

- **Design de Interface:** Use o editor de XAML para arrastar e soltar controles na janela.
- **Adicionar Funcionalidades:** Implemente eventos de botões, menus e outros controles para interagir com o usuário.
- **Pacotes NuGet:** Adicione bibliotecas e componentes adicionais usando o Gerenciador de Pacotes NuGet.

## DISTRIBUIÇÃO:
### DISTRIBUINDO PARA WINDOWS:
1. **Build do Aplicativo**
   - Certifique-se de que o seu aplicativo está funcionando corretamente no Visual Studio.
   - Vá para o menu `Build` e selecione `Build Solution` (ou `Ctrl+Shift+B`) para compilar seu projeto.

2. **Publicação**
   - Clique com o botão direito no projeto no `Solution Explorer` e selecione `Publish`.
   - Escolha um destino de publicação. Para um executável autônomo, selecione `Folder` e depois `Next`.
   - Configure as opções conforme necessário (local da pasta, configurações de release/debug) e clique em `Finish`.
   - Clique em `Publish` para gerar os arquivos de publicação.

Os arquivos gerados podem ser distribuídos diretamente aos usuários para execução no Windows.

### DISTRIBUINDO PARA LINUX:
Para Linux, você pode usar o .NET Core, que é multiplataforma.

1. **Instalando o SDK do .NET Core**
   - Certifique-se de ter o SDK do .NET Core instalado. Você pode baixar e instalar a partir do site oficial do [.NET](https://dotnet.microsoft.com/download).

2. **Publicação para Linux**
   - No Visual Studio, clique com o botão direito no projeto no `Solution Explorer` e selecione `Publish`.
   - Escolha um destino de publicação. Selecione `Folder` e depois `Next`.
   - Na seção `Target Runtime`, selecione `linux-x64`.
   - Configure as opções conforme necessário e clique em `Finish`.
   - Clique em `Publish` para gerar os arquivos de publicação.

Os arquivos gerados podem ser transferidos para um sistema Linux e executados lá.

### DISTRIBUINDO PARA ANDROID:
Para Android, você pode usar o Xamarin ou .NET MAUI (Multi-platform App UI), que permite criar aplicativos para várias plataformas, incluindo Android.

#### USANDO XAMARIN:
1. **Instalando Xamarin**
   - Se você não tiver Xamarin instalado, vá para `Tools` > `Get Tools and Features` e selecione `Mobile development with .NET`. Isso instalará o Xamarin.

2. **Criando um Projeto Android**
   - No Visual Studio, vá para `File` > `New` > `Project`.
   - Selecione `Android App (Xamarin)` e clique em `Next`.
   - Configure seu projeto e clique em `Create`.

3. **Desenvolvimento e Teste**
   - Desenvolva seu aplicativo no projeto Android. Você pode usar o emulador Android para testar seu aplicativo.
   - Quando estiver pronto para distribuir, vá para `Build` > `Archive` para preparar seu aplicativo para distribuição.

4. **Publicação**
   - Após a criação do arquivo `APK` ou `AAB`, você pode distribuí-lo diretamente ou enviá-lo para a Google Play Store.

#### USANDO .NET MAUI:
1. **Instalando .NET MAUI**
   - Certifique-se de que o .NET MAUI está instalado. Selecione `Tools` > `Get Tools and Features` e escolha `Mobile development with .NET`.

2. **Criando um Projeto MAUI**
   - No Visual Studio, vá para `File` > `New` > `Project`.
   - Selecione `MAUI App` e clique em `Next`.
   - Configure seu projeto e clique em `Create`.

3. **Desenvolvimento e Teste**
   - Desenvolva seu aplicativo usando a estrutura MAUI. Use emuladores Android para testar.
   - Para distribuição, vá para `Build` > `Archive` para preparar o pacote de distribuição.

4. **Publicação**
   - Após a criação do arquivo `APK` ou `AAB`, distribua conforme necessário ou envie para a Google Play Store.