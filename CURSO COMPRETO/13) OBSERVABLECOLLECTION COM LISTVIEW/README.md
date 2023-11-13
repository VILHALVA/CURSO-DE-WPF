# OBSERVABLECOLLECTION COM LISTVIEW
`ObservableCollection` é uma classe no WPF que implementa a interface `INotifyCollectionChanged`. Isso significa que ela notifica automaticamente a interface do usuário sobre quaisquer alterações na coleção, facilitando a atualização dinâmica da interface do usuário.

## Configurando:
### 1. **Adicione um `ListView` e Defina a Propriedade `ItemsSource` no XAML:**
```xaml
<ListView Name="listView" Grid.Row="0" ItemsSource="{Binding Pessoas}">
    <ListView.View>
        <GridView>
            <GridViewColumn Header="Nome" DisplayMemberBinding="{Binding Nome}"/>
            <GridViewColumn Header="Idade" DisplayMemberBinding="{Binding Idade}"/>
            <!-- Adicione mais colunas conforme necessário -->
        </GridView>
    </ListView.View>
</ListView>
```

### 2. **Defina o DataContext no Código-behind:**
```csharp
public MainWindow()
{
    InitializeComponent();

    // DataContext é onde a coleção ObservableCollection será vinculada
    DataContext = this;

    // Inicialize a coleção ObservableCollection
    Pessoas = new ObservableCollection<Pessoa>
    {
        new Pessoa { Nome = "Alice", Idade = 25 },
        new Pessoa { Nome = "Bob", Idade = 30 },
        // Adicione mais pessoas conforme necessário
    };
}
```

### 3. **Crie uma Classe de Modelo e Propriedade ObservableCollection:**
```csharp
public class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
}

public ObservableCollection<Pessoa> Pessoas { get; set; }
```

## Adicionando, Excluindo e Limpando a Coleção:
### 1. **Adicionando à Coleção:**
```csharp
Pessoa novaPessoa = new Pessoa { Nome = "Charlie", Idade = 35 };
Pessoas.Add(novaPessoa);
```

### 2. **Excluindo da Coleção:**
```csharp
Pessoa pessoaSelecionada = (Pessoa)listView.SelectedItem;
if (pessoaSelecionada != null)
{
    Pessoas.Remove(pessoaSelecionada);
}
```

### 3. **Limpando a Coleção:**
```csharp
Pessoas.Clear();
```

## Conclusão:
Usar `ObservableCollection` como fonte de dados para `ListView` é uma maneira eficiente de garantir que a interface do usuário seja automaticamente atualizada sempre que a coleção é modificada. Isso proporciona uma experiência de usuário mais dinâmica e responsiva.

Lembre-se de que a propriedade `ItemsSource` do `ListView` deve ser vinculada ao DataContext da janela ou ao controle onde a coleção está definida.

