# FOLDERBROWSERDIALOG - COMO USAR WINFORMS NO WPF!
Para incorporar um controle WinForms `FolderBrowserDialog` em um aplicativo WPF, você pode usar o elemento `WindowsFormsHost` para hospedar o controle WinForms dentro de um controle WPF. Vamos criar um exemplo básico para ilustrar como fazer isso:

## Passos para Incorporar `FolderBrowserDialog` em um Aplicativo WPF:

### 1. **Crie um Projeto WPF:**
   - Abra o Visual Studio e crie um novo projeto WPF.

### 2. **Adicione uma Referência a System.Windows.Forms:**
   - No seu projeto WPF, clique com o botão direito do mouse em "Referências" e selecione "Adicionar Referência".
   - Na guia "Assemblies", marque a caixa "System.Windows.Forms" e clique em "OK".

### 3. **Adicione um Controle `WindowsFormsHost`:**
   - Abra o XAML do seu `MainWindow.xaml` e adicione um `WindowsFormsHost` onde você deseja incorporar o `FolderBrowserDialog`:

    ```xaml
    <Window x:Class="SeuNamespace.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <WindowsFormsHost Name="windowsFormsHost" HorizontalAlignment="Stretch" VerticalAlignment="Stretch"/>
        </Grid>
    </Window>
    ```

### 4. **Crie e Configure o Controle `FolderBrowserDialog`:**
   - No código-behind (`MainWindow.xaml.cs`), crie e configure o controle `FolderBrowserDialog`. Certifique-se de importar o namespace `System.Windows.Forms`:

    ```csharp
    using System.Windows;
    using System.Windows.Forms;

    namespace SeuNamespace
    {
        public partial class MainWindow : Window
        {
            private FolderBrowserDialog folderBrowserDialog;

            public MainWindow()
            {
                InitializeComponent();
                folderBrowserDialog = new FolderBrowserDialog();
                windowsFormsHost.Child = folderBrowserDialog;
            }
        }
    }
    ```

### 5. **Execute o Aplicativo:**
   - Execute o aplicativo e você verá o `FolderBrowserDialog` incorporado em sua janela WPF.

## Dicas Úteis:
#### 1. **Aliases para Evitar Erros de Referência Ambíguos:**
   - Se você estiver usando o mesmo nome em ambos os namespaces (`System.Windows` e `System.Windows.Forms`), pode ser útil usar aliases para evitar ambiguidade. Por exemplo:

    ```xaml
    <Window x:Class="SeuNamespace.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:wfi="clr-namespace:System.Windows.Forms.Integration;assembly=WindowsBase"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <wfi:WindowsFormsHost Name="windowsFormsHost" HorizontalAlignment="Stretch" VerticalAlignment="Stretch"/>
        </Grid>
    </Window>
    ```

### 2. **Lidando com Eventos e Resultados:**
   - Se você deseja lidar com eventos ou obter resultados do `FolderBrowserDialog`, pode fazer isso diretamente no código-behind.

Essas dicas devem ajudá-lo a incorporar controles WinForms, como o `FolderBrowserDialog`, em seu aplicativo WPF. 