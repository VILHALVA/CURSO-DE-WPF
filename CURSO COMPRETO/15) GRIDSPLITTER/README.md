# GRIDSPLITTER
O `GridSplitter` é um controle no WPF que permite aos usuários redimensionar linhas e colunas em um layout de grade (Grid). Ele é muito útil quando você deseja dar aos usuários a capacidade de ajustar o tamanho de áreas específicas em sua interface do usuário. Aqui estão alguns conceitos básicos sobre como usar o `GridSplitter`:

## Usando o GridSplitter:
### 1. **Adicionando um GridSplitter ao XAML:**
   - Você pode adicionar um `GridSplitter` diretamente ao seu arquivo XAML, geralmente dentro de um `Grid`:

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>

    <!-- Conteúdo das colunas -->
    
    <GridSplitter Grid.Column="1" Width="5" Background="Black" VerticalAlignment="Stretch" HorizontalAlignment="Left"/>
    
    <!-- Conteúdo das colunas -->
</Grid>
```

### 2. **Definindo a Direção do GridSplitter:**
   - O `GridSplitter` pode ser usado em linhas ou colunas, e você precisa definir a propriedade `ResizeDirection` para indicar a direção desejada:

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>

    <!-- Conteúdo das colunas -->
    
    <GridSplitter Grid.Column="1" Width="5" Background="Black" VerticalAlignment="Stretch" HorizontalAlignment="Left" ResizeDirection="Columns"/>
    
    <!-- Conteúdo das colunas -->
</Grid>
```

### 3. **Definindo Limites de Redimensionamento:**
   - Você pode definir valores mínimos e máximos para o redimensionamento usando as propriedades `ResizeBehavior`, `MinWidth`, `MinHeight`, `MaxWidth`, e `MaxHeight`.

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>

    <!-- Conteúdo das colunas -->
    
    <GridSplitter Grid.Column="1" Width="5" Background="Black" VerticalAlignment="Stretch" HorizontalAlignment="Left" ResizeDirection="Columns" ResizeBehavior="PreviousAndNext" MinWidth="50" MaxWidth="200"/>
    
    <!-- Conteúdo das colunas -->
</Grid>
```

## Dicas Adicionais:
### 1. **Comportamento de Redimensionamento:**
   - A propriedade `ResizeBehavior` determina como o `GridSplitter` afeta as colunas ou linhas adjacentes. O valor padrão é `PreviousAndNext`.

### 2. **Manipulação de Eventos:**
   - Você pode manipular eventos como `DragDelta` para realizar ações adicionais enquanto o usuário redimensiona.

```xaml
<GridSplitter DragDelta="GridSplitter_DragDelta"/>
```

```csharp
private void GridSplitter_DragDelta(object sender, System.Windows.Controls.Primitives.DragDeltaEventArgs e)
{
    // Lógica personalizada durante o redimensionamento
}
```

O `GridSplitter` é uma ferramenta poderosa para melhorar a experiência do usuário ao permitir que ele ajuste dinamicamente o tamanho das áreas na interface do usuário. Use-o conforme necessário para criar interfaces mais flexíveis e interativas. 