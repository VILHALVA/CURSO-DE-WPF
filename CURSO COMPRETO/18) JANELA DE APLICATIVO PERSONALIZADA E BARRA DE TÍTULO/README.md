# JANELA DE APLICATIVO PERSONALIZADA E BARRA DE TÍTULO
Para criar uma janela de aplicativo personalizada no WPF, você pode seguir alguns passos específicos para remover a barra de título padrão e adicionar seus próprios controles de barra de título. Aqui estão os passos básicos:

## Configuração e Informações:
### 1. **Configurando a Propriedade WindowStyle:**
   - Defina a propriedade `WindowStyle` da janela como `None` para remover a barra de título padrão:

```xaml
<Window x:Class="SuaNamespace.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Sua Janela Personalizada" Height="400" Width="600" WindowStyle="None">
    <!-- Conteúdo da Janela -->
</Window>
```

### 2. **Habilitando a Funcionalidade de Arrastar para Mover:**
   - Adicione o evento `MouseLeftButtonDown` a um elemento na janela para tornar a janela arrastável:

```xaml
<Grid MouseLeftButtonDown="Grid_MouseLeftButtonDown">
    <!-- Conteúdo da Janela -->
</Grid>
```

```csharp
private void Grid_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
{
    if (e.LeftButton == MouseButtonState.Pressed)
    {
        DragMove();
    }
}
```

## Configuração da Barra de Título Personalizada:
### 1. **Criando uma Barra de Título Personalizada:**
   - Adicione controles (como botões) para criar sua própria barra de título:

```xaml
<Grid MouseLeftButtonDown="Grid_MouseLeftButtonDown">
    <!-- Barra de Título Personalizada -->
    <StackPanel Orientation="Horizontal" Background="#FF2F2F2" Height="30">
        <Button Content="_" Width="30" Click="MinimizeButton_Click"/>
        <Button Content="[]" Width="30" Click="MaximizeRestoreButton_Click"/>
        <Button Content="X" Width="30" Click="CloseButton_Click"/>
    </StackPanel>

    <!-- Conteúdo da Janela -->
</Grid>
```

### 2. **Implementando Funcionalidades de Botões:**
   - Adicione os manipuladores de eventos para os botões para realizar ações como minimizar, maximizar/restaurar e fechar a janela:

```csharp
private void MinimizeButton_Click(object sender, RoutedEventArgs e)
{
    WindowState = WindowState.Minimized;
}

private void MaximizeRestoreButton_Click(object sender, RoutedEventArgs e)
{
    if (WindowState == WindowState.Maximized)
        WindowState = WindowState.Normal;
    else
        WindowState = WindowState.Maximized;
}

private void CloseButton_Click(object sender, RoutedEventArgs e)
{
    App.Current.Shutdown();
}
```

## Remoção do WindowChrome:
Para remover a decoração padrão do sistema operacional (bordas e sombras) ao redor da janela, você pode utilizar a classe `WindowChrome`. Certifique-se de que esteja usando a referência ao namespace correto no arquivo XAML:

```xaml
xmlns:shell="clr-namespace:Microsoft.Windows.Shell;assembly=Microsoft.Windows.Compatibility"
```

Então, adicione a configuração `WindowChrome` à sua janela:

```xaml
<Window x:Class="SuaNamespace.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:shell="clr-namespace:Microsoft.Windows.Shell;assembly=Microsoft.Windows.Compatibility"
        Title="Sua Janela Personalizada" Height="400" Width="600" WindowStyle="None">
    <shell:WindowChrome.WindowChrome>
        <shell:WindowChrome ResizeBorderThickness="5"/>
    </shell:WindowChrome.WindowChrome>
    
    <!-- Conteúdo da Janela -->
</Window>
```

Estes são os passos básicos para criar uma janela de aplicativo personalizada no WPF. Personalize os controles da barra de título conforme necessário para atender aos requisitos específicos do seu aplicativo. 