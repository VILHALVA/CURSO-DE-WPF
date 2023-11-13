# CURSO DE WPF
👨‍⚖️WPF SIGNIFICA WINDOWS PRESENTATION FOUNDATION. É UMA TECNOLOGIA DA MICROSOFT PARA CRIAR INTERFACES GRÁFICAS DE USUÁRIO EM APLICATIVOS WINDOWS.

[![GitHub Repo stars](https://img.shields.io/badge/VILHALVA-GITHUB-03A9F4?logo=github)](https://github.com/VILHALVA) 
[![GitHub Repo stars](https://img.shields.io/badge/VEJA%20OS-VIDEOS-03A9F4?logo=youtube)](https://www.youtube.com/@vilhalva100/search?query=WPF)
[![GitHub Repo stars](https://img.shields.io/badge/VEJA-DOCUMENTAÇÃO-03A9F4?logo=google)](https://docs.microsoft.com/pt-br/dotnet/desktop-wpf/) 
[![GitHub Repo stars](https://img.shields.io/badge/LINGUAGEM%20DE-PROGRAMAÇÃO-03A9F4?logo=github)](https://github.com/VILHALVA/CURSO-DE-C-SHARP) <br>

[![GitHub Repo stars](https://img.shields.io/badge/-PLAYLIST%20DO%20YOUTUBE-blueviolet)](https://youtube.com/playlist?list=PLih2KERbY1HHOOJ2C6FOrVXIwg4AZ-hk1&si=a-ana-M3MNpsbsHi)

<img src="https://www.euvic.com/wp-content/uploads/2021/05/7-dot-net-technologies.png" align="center" width="280"> <br>

![](https://i.imgur.com/waxVImv.png)

# CONCEITO:
WPF (Windows Presentation Foundation) é uma estrutura de desenvolvimento de interface gráfica para aplicativos Windows. Ele fornece uma maneira poderosa e flexível de criar interfaces de usuário ricas e interativas. Vamos começar com alguns conceitos fundamentais:

1. **XAML (Extensible Application Markup Language):**
   - O XAML é uma linguagem de marcação declarativa usada para criar interfaces de usuário no WPF. É semelhante ao HTML, mas é usado para definir a estrutura e o layout da interface do usuário.
   - Exemplo de XAML:

    ```xaml
    <Window x:Class="SeuNamespace.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="Minha Janela" Height="350" Width="525">
        <Grid>
            <Button Content="Clique em mim" HorizontalAlignment="Center" VerticalAlignment="Center"/>
        </Grid>
    </Window>
    ```

2. **Controles:**
   - Os controles são elementos visuais como botões, caixas de texto, listas, etc., usados para construir a interface do usuário.
   - Exemplo de um botão:

    ```xaml
    <Button Content="Meu Botão" Click="MeuBotao_Click"/>
    ```

3. **Eventos:**
   - No exemplo acima, o evento `Click` está associado ao método `MeuBotao_Click`. Isso significa que quando o botão é clicado, o código no método é executado.

    ```csharp
    private void MeuBotao_Click(object sender, RoutedEventArgs e)
    {
        // Código a ser executado quando o botão é clicado
    }
    ```

4. **Data Binding:**
   - O data binding é uma técnica que permite que os dados em seu aplicativo sejam automaticamente atualizados quando o estado subjacente muda.
   - Exemplo de data binding:

    ```xaml
    <TextBlock Text="{Binding Nome}" />
    ```

5. **MVVM (Model-View-ViewModel):**
   - O MVVM é um padrão de design que separa a lógica de apresentação da lógica de negócios e dos dados.
   - Exemplo básico do padrão MVVM: Model, ViewModel e View.

    ```csharp
    // Model
    public class Pessoa
    {
        public string Nome { get; set; }
    }

    // ViewModel
    public class PessoaViewModel
    {
        public Pessoa MinhaPessoa { get; set; } = new Pessoa();
    }
    ```

    ```xaml
    <!-- View -->
    <TextBlock Text="{Binding MinhaPessoa.Nome}" />
    ```

