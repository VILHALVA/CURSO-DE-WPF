# ESTILOS E MODELOS DE CONTROLE
## Configuração:
### 1. **Configurando Recursos:**
   - Antes de criar um `ControlTemplate`, você pode configurar recursos no `App.xaml` ou em outro arquivo XAML.

```xaml
<Application x:Class="SeuNamespace.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <!-- Recursos aqui -->
    </Application.Resources>
</Application>
```

## Por que um `ControlTemplate`?
- Um `ControlTemplate` permite personalizar completamente a aparência de um controle.
- É útil quando os estilos padrão dos controles não atendem às suas necessidades visuais.
- Oferece controle total sobre como um controle é renderizado.

## Evitando Problemas (Adicionando Gatilhos):
#### 1. **Adicionando Gatilhos para Melhor Comportamento:**
   - Ao criar um `ControlTemplate`, adicione gatilhos para interações específicas para garantir um comportamento consistente.

```xaml
<ControlTemplate.Triggers>
    <Trigger Property="IsMouseOver" Value="True">
        <Setter Property="Background" Value="LightGray"/>
    </Trigger>
</ControlTemplate.Triggers>
```

## Criando um `ControlTemplate`:
### 1. **Ligação de Modelo:**
   - Crie um `ControlTemplate` para um controle específico e ligue-o ao controle usando a propriedade `Template`.

```xaml
<Button Content="Clique-me">
    <Button.Template>
        <ControlTemplate TargetType="Button">
            <!-- Defina o modelo aqui -->
        </ControlTemplate>
    </Button.Template>
</Button>
```

### 2. **Apresentador de Conteúdo (`ContentPresenter`):**
   - Use `ContentPresenter` para exibir o conteúdo do controle dentro do `ControlTemplate`.

```xaml
<ControlTemplate TargetType="Button">
    <Border Background="Blue">
        <ContentPresenter/>
    </Border>
</ControlTemplate>
```

## Os Gatilhos Funcionam!
- Adicione gatilhos ao `ControlTemplate` para controlar visualmente o comportamento do controle em diferentes estados.

```xaml
<ControlTemplate.Triggers>
    <Trigger Property="IsMouseOver" Value="True">
        <Setter Property="Background" Value="LightGray"/>
    </Trigger>
    <!-- Adicione mais gatilhos conforme necessário -->
</ControlTemplate.Triggers>
```

## Aviso!!
- Cuidado ao personalizar demais, pois isso pode impactar a acessibilidade e a usabilidade do aplicativo.

## Começando com um Modelo Padrão:
### 1. **Obtendo o Modelo Padrão:**
   - Utilize o estilo padrão de um controle como ponto de partida para criar seu `ControlTemplate`.

```xaml
<Button Content="Clique-me" x:Name="meuBotao"/>
```

```csharp
ControlTemplate templatePadrao = meuBotao.Template;
```

## Modificando um Modelo Padrão:
### 1. **Modificando o Modelo Padrão:**
   - Faça alterações no modelo padrão conforme necessário.

```xaml
<ControlTemplate TargetType="Button">
    <Border Background="Red">
        <ContentPresenter/>
    </Border>
</ControlTemplate>
```

## Exemplos de Modelos de Estilo Microsoft:
- A Microsoft fornece estilos padrão que você pode modificar ou usar como referência.
- Acesse a documentação do WPF para obter exemplos específicos para cada controle.

```xaml
<!-- Exemplo de estilo de botão padrão -->
<Style TargetType="Button" BasedOn="{StaticResource {x:Type Button}}">
    <Setter Property="Background" Value="Green"/>
</Style>
```

Estes são conceitos fundamentais para criar e personalizar `ControlTemplates` em WPF. Use essas técnicas para ter controle total sobre a aparência dos controles em seu aplicativo. 