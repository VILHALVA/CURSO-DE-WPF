# RECURSOS DE ESTILO REUTILIZÁVEIS
## Configuração:
### 1. **Configurando Recursos Globais:**
   - No arquivo `App.xaml`, dentro da tag `<Application.Resources>`, você pode definir recursos globais para todo o aplicativo.

```xaml
<Application x:Class="SeuNamespace.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <!-- Recursos globais aqui -->
    </Application.Resources>
</Application>
```

## Por que Estilos Reutilizáveis?
- Os estilos reutilizáveis facilitam a manutenção do código, evitando duplicação.
- Permitem consistência visual em todo o aplicativo.
- Facilitam a atualização e a alteração do design sem tocar em cada controle individualmente.

## Caso de Uso para Estilos:
### 1. **Criando e Aplicando um Estilo Global:**
   - Defina um estilo global no `App.xaml` que afetará todos os botões no aplicativo.

```xaml
<Application.Resources>
    <Style TargetType="Button">
        <Setter Property="Background" Value="LightBlue"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Application.Resources>
```

### 2. **Substituindo um Estilo Global:**
   - Em um controle específico, você pode substituir o estilo global atribuindo um novo estilo ao controle.

```xaml
<Button Content="Botão Especial" Style="{StaticResource BotaoEspecialStyle}"/>
```

## Caso de Uso para Estilo Explícito:
### 1. **Criando e Aplicando um Estilo Explícito:**
   - Crie um estilo explícito no `App.xaml` que pode ser aplicado explicitamente a um controle específico.

```xaml
<Application.Resources>
    <Style x:Key="BotaoEspecialStyle" TargetType="Button">
        <Setter Property="Background" Value="Yellow"/>
        <Setter Property="Foreground" Value="DarkGreen"/>
    </Style>
</Application.Resources>
```

### 2. **Limitando o Escopo do Estilo:**
   - O estilo explícito pode ser aplicado apenas onde é necessário, limitando o escopo.

```xaml
<Button Content="Botão Especial" Style="{StaticResource BotaoEspecialStyle}"/>
```

## Estilos para Todo o Aplicativo:
### 1. **Usando ResourceDictionary e MergedDictionaries:**
   - Use `ResourceDictionary` e `MergedDictionaries` para organizar estilos em arquivos separados e aplicá-los globalmente.

```xaml
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="EstilosGlobais.xaml"/>
            <ResourceDictionary Source="EstilosBotao.xaml"/>
            <!-- Adicione mais dicionários conforme necessário -->
        </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
</Application.Resources>
```

No arquivo `EstilosGlobais.xaml`:

```xaml
<!-- Estilos globais aqui -->
```

No arquivo `EstilosBotao.xaml`:

```xaml
<!-- Estilos específicos de botão aqui -->
```

Os recursos de estilo reutilizáveis ajudam a manter o código mais limpo, consistente e fácil de manter em aplicativos WPF. Utilize-os de acordo com as necessidades do seu projeto. 