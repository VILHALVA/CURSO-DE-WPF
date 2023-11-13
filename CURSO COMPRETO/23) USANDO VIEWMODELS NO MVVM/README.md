# USANDO VIEWMODELS NO MVVM
## Configuração:
Antes de começar a criar um Model e um ViewModel, é importante configurar o ambiente e definir o contexto de dados. Vamos começar com a configuração básica.

### 1. **Configurando o Ambiente:**
   - Crie um projeto WPF no Visual Studio.
   - Abra o arquivo `App.xaml` e defina o contexto de dados para o seu ViewModel.

```xaml
<Application x:Class="SeuNamespace.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <local:PessoaViewModel x:Key="PessoaViewModel"/>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

### 2. **Criando um Modelo (POCO):**
   - Crie uma classe para o modelo de dados (POCO - Plain Old CLR Object).

```csharp
public class PessoaModel
{
    public string Nome { get; set; }
    public int Idade { get; set; }
}
```

## Criando um ViewModel:
### 1. **Criando um ViewModel:**
   - Crie uma classe para o ViewModel, que será vinculada à sua View.

```csharp
public class PessoaViewModel : INotifyPropertyChanged
{
    private PessoaModel _pessoa;

    public PessoaModel Pessoa
    {
        get { return _pessoa; }
        set
        {
            _pessoa = value;
            OnPropertyChanged(nameof(Pessoa));
        }
    }

    public PessoaViewModel()
    {
        // Inicializa o modelo de pessoa com dados fictícios
        Pessoa = new PessoaModel { Nome = "João", Idade = 30 };
    }

    public event PropertyChangedEventHandler PropertyChanged;

    protected virtual void OnPropertyChanged(string propertyName)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

## Classe Base ViewModel:
Para facilitar a implementação do `INotifyPropertyChanged`, você pode criar uma classe base para seus ViewModels.

```csharp
public class ViewModelBase : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler PropertyChanged;

    protected virtual void OnPropertyChanged([CallerMemberName] string propertyName = null)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

Agora, seu `PessoaViewModel` pode herdar dessa classe base.

## Visualização e Vinculações:
### 1. **Visualização e Vinculações:**
   - Abra o arquivo `MainWindow.xaml` e vincule os dados da `PessoaViewModel` aos controles da View.

```xaml
<Window x:Class="SeuNamespace.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525"
        DataContext="{StaticResource PessoaViewModel}">

    <Grid>
        <TextBlock Text="{Binding Pessoa.Nome}" />
        <TextBlock Text="{Binding Pessoa.Idade}" />
    </Grid>
</Window>
```

## Semeando Dados e Testes:
### 1. **Semeando Dados e Testes:**
   - Execute o aplicativo para verificar se os dados estão sendo exibidos corretamente na View.

## Colunas Personalizadas do DataGrid:
### 1. **Colunas Personalizadas do DataGrid:**
   - Se você estiver usando um `DataGrid`, pode personalizar as colunas da seguinte maneira:

```xaml
<DataGrid AutoGenerateColumns="False" ItemsSource="{Binding ListaDePessoas}">
    <DataGrid.Columns>
        <DataGridTextColumn Header="Nome" Binding="{Binding Nome}" />
        <DataGridTextColumn Header="Idade" Binding="{Binding Idade}" />
    </DataGrid.Columns>
</DataGrid>
```

## Recapitulação/Revisão:
- Configuramos o ambiente e definimos o contexto de dados no arquivo `App.xaml`.
- Criamos um modelo simples (`PessoaModel`) e um ViewModel correspondente (`PessoaViewModel`).
- Implementamos uma classe base para ViewModel (`ViewModelBase`) para facilitar a notificação de alterações.
- Vinculamos os dados da `PessoaViewModel` à View no arquivo `MainWindow.xaml`.
- Testamos o aplicativo para garantir que os dados sejam exibidos corretamente.

Esses são os passos iniciais para implementar o padrão MVVM em um aplicativo WPF. Lembre-se de que este é um exemplo básico, e há muitas práticas avançadas e conceitos específicos que podem ser aplicados com base nos requisitos do projeto. 