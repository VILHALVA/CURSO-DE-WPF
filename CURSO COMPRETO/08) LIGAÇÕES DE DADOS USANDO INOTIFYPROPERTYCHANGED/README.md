# LIGAÇÕES DE DADOS USANDO INOTIFYPROPERTYCHANGED
No WPF, o `INotifyPropertyChanged` é uma interface fundamental para realizar ligações de dados bidirecionais. Ele permite que uma classe notifique os assinantes sobre alterações nas propriedades, garantindo que a interface do usuário seja atualizada automaticamente.

## Configurando o Projeto:
1. **Abra ou Crie um Projeto WPF:**
   - Abra o Visual Studio e abra seu projeto existente ou crie um novo projeto WPF.

## Criando Nossa Propriedade:
### 1. **Adicione uma Classe de Modelo:**
   - Adicione uma nova classe ao seu projeto (por exemplo, `Pessoa.cs`).

### 2. **Defina uma Propriedade com INotifyPropertyChanged:**
   - Implemente a interface `INotifyPropertyChanged` e defina uma propriedade:

    ```csharp
    using System.ComponentModel;

    namespace SeuNamespace
    {
        public class Pessoa : INotifyPropertyChanged
        {
            private string _nome;

            public string Nome
            {
                get { return _nome; }
                set
                {
                    if (_nome != value)
                    {
                        _nome = value;
                        OnPropertyChanged(nameof(Nome));
                    }
                }
            }

            public event PropertyChangedEventHandler PropertyChanged;

            protected virtual void OnPropertyChanged(string propertyName)
            {
                PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
            }
        }
    }
    ```

## Configurando o Contexto dos Dados:
### 1. **Defina um Objeto de Modelo no XAML:**
   - No seu arquivo XAML, defina um objeto de modelo no nível de recursos:

    ```xaml
    <Window.Resources>
        <local:Pessoa x:Key="modeloPessoa"/>
    </Window.Resources>
    ```

### 2. **Vincule o DataContext:**
   - Vincule o `DataContext` do seu elemento principal ao objeto de modelo:

    ```xaml
    <Grid DataContext="{StaticResource modeloPessoa}">
        <!-- Seus controles aqui -->
    </Grid>
    ```

## Implementando INotifyPropertyChanged:
### 1. **Vinculação de Propriedades:**
   - Use a propriedade `Nome` na sua interface do usuário:

    ```xaml
    <TextBox Text="{Binding Nome, UpdateSourceTrigger=PropertyChanged}"/>
    ```

   - `UpdateSourceTrigger=PropertyChanged` garante que a propriedade seja atualizada imediatamente quando o valor na interface do usuário é alterado.

### 2. **Atualizando a GUI via Propriedade:**
   - Implemente a lógica de propriedade na classe do modelo:

    ```csharp
    public class Pessoa : INotifyPropertyChanged
    {
        private string _nome;

        public string Nome
        {
            get { return _nome; }
            set
            {
                if (_nome != value)
                {
                    _nome = value;
                    OnPropertyChanged(nameof(Nome));
                }
            }
        }
    }
    ```

## Modo de Vinculação:
- O modo de vinculação padrão é `TwoWay`, o que significa que as alterações na GUI afetarão o modelo e vice-versa.

## Refatorar para Reutilização:
Se você tiver várias propriedades e classes, considere criar uma classe base que implemente `INotifyPropertyChanged` para reutilizar o código.

## Informação Adicional:
- O `INotifyPropertyChanged` é essencial para manter as ligações de dados atualizadas.
  
- Use o `UpdateSourceTrigger` apropriadamente com base nos requisitos da aplicação.

- Implemente a notificação de propriedade alterada sempre que uma propriedade for modificada.

Com essas práticas, você estará bem encaminhado para criar aplicações WPF eficazes e responsivas com ligações de dados robustas. 