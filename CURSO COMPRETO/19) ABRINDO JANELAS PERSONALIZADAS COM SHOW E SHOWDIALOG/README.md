# ABRINDO JANELAS PERSONALIZADAS COM SHOW E SHOWDIALOG
## Configuração e Criação de Janelas WPF:
### 1. **Criando uma Nova Janela no XAML:**
   - Adicione uma nova janela ao seu projeto WPF, criando um novo arquivo XAML (por exemplo, `NovaJanela.xaml`).

```xaml
<Window x:Class="SeuNamespace.NovaJanela"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Nova Janela" Height="300" Width="400">
    <!-- Conteúdo da Nova Janela -->
</Window>
```

### 2. **Abrindo Janelas no Código-behind:**
   - No código-behind da sua janela principal ou de qualquer controle, crie uma instância da nova janela e chame o método `Show` para exibi-la.

```csharp
NovaJanela novaJanela = new NovaJanela();
novaJanela.Show();
```

## Mostrar vs MostrarDialog:
### 1. **Mostrar Comportamento (Não Modal):**
   - O método `Show` abre a janela e permite que o usuário interaja com outras janelas do aplicativo enquanto a nova janela está aberta.

```csharp
NovaJanela novaJanela = new NovaJanela();
novaJanela.Show();
```

### 2. **Comportamento ShowDialog (Modal):**
   - O método `ShowDialog` abre a janela como modal, bloqueando a interação com outras janelas até que a janela seja fechada.

```csharp
NovaJanela novaJanela = new NovaJanela();
novaJanela.ShowDialog();
```

## Casos de Uso:
### 1. **Caso de Uso Show (Não Modal):**
   - Abre a nova janela sem bloquear a janela principal.

```csharp
private void AbrirJanelaShow(object sender, RoutedEventArgs e)
{
    NovaJanela novaJanela = new NovaJanela();
    novaJanela.Show();
}
```

### 2. **Caso de Uso ShowDialog (Modal):**
   - Abre a nova janela de forma modal e aguarda até que a janela seja fechada para continuar.

```csharp
private void AbrirJanelaShowDialog(object sender, RoutedEventArgs e)
{
    NovaJanela novaJanela = new NovaJanela();
    novaJanela.ShowDialog();
}
```

## Retornando Dados do Modal:
### 1. **Retornando Dados da Janela Modal:**
   - Você pode definir propriedades na janela modal para retornar dados à janela chamadora.

```csharp
// Na janela modal
public string Dados { get; set; }

// No código chamador
private void AbrirJanelaShowDialogComRetorno(object sender, RoutedEventArgs e)
{
    NovaJanela novaJanela = new NovaJanela();
    novaJanela.ShowDialog();

    // Acessando dados da janela modal após fechamento
    string dadosRetornados = novaJanela.Dados;
}
```

## WindowStartupLocation e Opacidade:
### 1. **Definindo a Localização Inicial da Janela:**
   - Use a propriedade `WindowStartupLocation` para definir onde a janela será exibida inicialmente.

```csharp
NovaJanela novaJanela = new NovaJanela();
novaJanela.WindowStartupLocation = WindowStartupLocation.CenterScreen;
novaJanela.Show();
```

### 2. **Definindo a Opacidade da Janela para Foco:**
   - Use a propriedade `Opacity` para ajustar a opacidade da janela.

```csharp
NovaJanela novaJanela = new NovaJanela();
novaJanela.Opacity = 0.8;
novaJanela.Show();
```

Estes são alguns conceitos básicos sobre como criar e abrir janelas personalizadas no WPF usando os métodos `Show` e `ShowDialog`. Adapte-os conforme necessário para atender aos requisitos específicos do seu aplicativo.