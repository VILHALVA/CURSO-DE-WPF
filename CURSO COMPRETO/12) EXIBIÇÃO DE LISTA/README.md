# EXIBIÇÃO DE LISTA
## Exibição de Lista com o Controle `ListView`:
O controle `ListView` no WPF é uma ferramenta poderosa para exibir listas de dados. Ele fornece flexibilidade para apresentar informações em uma tabela ou em uma exibição mais personalizada.

## Configurando:
### 1. **Adicione um `ListView` no XAML:**
```xaml
<ListView Name="listView" SelectionMode="Extended">
    <ListView.View>
        <GridView>
            <GridViewColumn Header="Nome" DisplayMemberBinding="{Binding Nome}"/>
            <GridViewColumn Header="Idade" DisplayMemberBinding="{Binding Idade}"/>
            <!-- Adicione mais colunas conforme necessário -->
        </GridView>
    </ListView.View>
</ListView>
```

## Criando um `ListView`:
### 1. **Crie uma Classe de Modelo:**
```csharp
public class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
}
```

### 2. **Crie uma Lista de Itens e Atribua ao `ListView`:**
```csharp
List<Pessoa> pessoas = new List<Pessoa>
{
    new Pessoa { Nome = "Alice", Idade = 25 },
    new Pessoa { Nome = "Bob", Idade = 30 },
    // Adicione mais itens conforme necessário
};

listView.ItemsSource = pessoas;
```

## Adicionando, Limpando e Excluindo Itens:
### 1. **Adicionando Itens ao `ListView` pela GUI:**
```csharp
Pessoa novaPessoa = new Pessoa { Nome = "Charlie", Idade = 35 };
listView.Items.Add(novaPessoa);
```

### 2. **Limpando o `ListView`:**
```csharp
listView.Items.Clear();
```

### 3. **Excluindo pelo `SelectedIndex`:**
```csharp
if (listView.SelectedIndex != -1)
{
    listView.Items.RemoveAt(listView.SelectedIndex);
}
```

### 4. **Excluindo pelo Item Selecionado:**
```csharp
Pessoa pessoaSelecionada = (Pessoa)listView.SelectedItem;
if (pessoaSelecionada != null)
{
    listView.Items.Remove(pessoaSelecionada);
}
```

### 5. **Excluindo com Seleção Múltipla:**
```csharp
foreach (Pessoa pessoaSelecionada in listView.SelectedItems.Cast<Pessoa>().ToList())
{
    listView.Items.Remove(pessoaSelecionada);
}
```

## Exclusão e Enumeração de Informações:
#### 1. **Informações de Enumeração e Exclusão:**
```csharp
foreach (Pessoa pessoa in listView.Items)
{
    // Faça algo com cada pessoa
}
```

## Modos de Seleção (Estendido/Múltiplo):
O atributo `SelectionMode` controla o modo de seleção do `ListView`. Defina-o no XAML para configurar o comportamento de seleção:

- `Single`: Apenas um item pode ser selecionado por vez (padrão).
- `Extended`: Permite seleção múltipla usando Ctrl ou Shift.

```xaml
<ListView Name="listView" SelectionMode="Extended">
    <!-- Conteúdo do ListView -->
</ListView>
```

Estas são as informações fundamentais sobre como usar o controle `ListView` no WPF para adicionar, excluir e limpar itens, bem como os modos de seleção única e múltipla. Personalize conforme necessário para atender aos requisitos específicos do seu aplicativo.