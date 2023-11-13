# USANDO RELAYCOMMAND NO MVVM
## Configuração:
Antes de começar a usar `RelayCommand`, certifique-se de que o ambiente esteja configurado corretamente, como descrito nas etapas anteriores.

### 1. **Configurando o Ambiente:**
   - Certifique-se de ter um projeto WPF criado no Visual Studio.
   - Defina o contexto de dados no arquivo `App.xaml`.

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

## Vinculação de Comando de Botão:
### 1. **Vinculação de Comando de Botão:**
   - Abra o arquivo `MainWindow.xaml` e adicione um botão com um comando associado.

```xaml
<Button Content="Saudação" Command="{Binding SaudacaoCommand}" />
```

## Implementando ICommand (RelayCommand):
### 1. **Implementando ICommand (RelayCommand):**
   - Crie uma classe `RelayCommand` que implementa a interface `ICommand`. Esta classe ajudará a vincular os comandos aos métodos no ViewModel.

```csharp
public class RelayCommand : ICommand
{
    private readonly Action<object> _execute;
    private readonly Predicate<object> _canExecute;

    public RelayCommand(Action<object> execute, Predicate<object> canExecute = null)
    {
        _execute = execute ?? throw new ArgumentNullException(nameof(execute));
        _canExecute = canExecute;
    }

    public bool CanExecute(object parameter)
    {
        return _canExecute == null || _canExecute(parameter);
    }

    public void Execute(object parameter)
    {
        _execute(parameter);
    }

    public event EventHandler CanExecuteChanged
    {
        add { CommandManager.RequerySuggested += value; }
        remove { CommandManager.RequerySuggested -= value; }
    }
}
```

## Usando RelayCommand:
### 1. **Usando RelayCommand:**
   - No seu ViewModel, crie uma instância de `RelayCommand` e associe-a a um método.

```csharp
public class PessoaViewModel : ViewModelBase
{
    private RelayCommand _saudacaoCommand;

    public ICommand SaudacaoCommand
    {
        get
        {
            if (_saudacaoCommand == null)
            {
                _saudacaoCommand = new RelayCommand(SaudacaoExecute, CanSaudacaoExecute);
            }
            return _saudacaoCommand;
        }
    }

    private void SaudacaoExecute(object parameter)
    {
        // Lógica para ação do comando de saudação
        MessageBox.Show("Olá, Mundo!");
    }

    private bool CanSaudacaoExecute(object parameter)
    {
        // Lógica para determinar se o comando pode ser executado
        return true;
    }
}
```

## Usando Predicados (CanExecute):
### 1. **Usando Predicados (CanExecute):**
   - O segundo parâmetro do `RelayCommand` é um predicado que determina se o comando pode ser executado.

```csharp
private bool CanSaudacaoExecute(object parameter)
{
    // Lógica para determinar se o comando pode ser executado
    return AlgumaCondicional;
}
```

## Recapitulação e Dicas:
- Configuramos o ambiente e definimos o contexto de dados no arquivo `App.xaml`.
- Adicionamos um botão na View vinculado a um comando no ViewModel.
- Implementamos a classe `RelayCommand` para facilitar a associação de comandos a métodos.
- Criamos uma instância de `RelayCommand` no ViewModel e associamos a um método de saudação.
- Utilizamos um predicado (`CanExecute`) para determinar se o comando pode ser executado.

Lembre-se de que este é um exemplo básico, e há muitas práticas avançadas que podem ser aplicadas, como o uso de bibliotecas MVVM populares (como MVVM Light Toolkit) ou ICommand genérico. 