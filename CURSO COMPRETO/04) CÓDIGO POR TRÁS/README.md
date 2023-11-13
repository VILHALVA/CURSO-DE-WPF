# CÓDIGO POR TRÁS
No desenvolvimento WPF, a lógica da aplicação é muitas vezes dividida entre o código-behind (código no arquivo `.cs` associado ao arquivo XAML) e a interface do usuário (definida no arquivo XAML). Vamos criar um exemplo mais extenso que envolve interatividade e a comunicação entre o código e a interface do usuário.

## Exemplo Maior: Calculadora Simples
Vamos criar uma calculadora simples onde o usuário pode inserir dois números, escolher uma operação e obter o resultado.

### 1. **Definindo a Interface do Usuário (XAML):**
Abra o arquivo `MainWindow.xaml` e substitua o conteúdo pelo seguinte código:

```xaml
<Window x:Class="SuaNamespace.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Calculadora Simples" Height="300" Width="400">
    <Grid>
        <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
            <TextBox x:Name="txtNumero1" Width="120" Margin="5"/>
            <ComboBox x:Name="cmbOperacao" Width="120" Margin="5">
                <ComboBoxItem Content="+" />
                <ComboBoxItem Content="-" />
                <ComboBoxItem Content="*" />
                <ComboBoxItem Content="/" />
            </ComboBox>
            <TextBox x:Name="txtNumero2" Width="120" Margin="5"/>
            <Button Content="Calcular" Width="120" Margin="5" Click="Calcular_Click"/>
            <TextBlock x:Name="txtResultado" FontSize="18" FontWeight="Bold" Margin="5"/>
        </StackPanel>
    </Grid>
</Window>
```

Este código cria uma interface simples com dois campos de texto para os números, uma lista suspensa (ComboBox) para a escolha da operação, um botão para calcular e um campo de texto para exibir o resultado.

### 2. **Lógica da Calculadora (Código-Behind):**
Abra o arquivo `MainWindow.xaml.cs` e adicione o seguinte código:

```csharp
using System;
using System.Windows;

namespace SuaNamespace
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Calcular_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                double numero1 = Convert.ToDouble(txtNumero1.Text);
                double numero2 = Convert.ToDouble(txtNumero2.Text);

                string operacao = ((ComboBoxItem)cmbOperacao.SelectedItem).Content.ToString();

                double resultado = 0;

                switch (operacao)
                {
                    case "+":
                        resultado = numero1 + numero2;
                        break;
                    case "-":
                        resultado = numero1 - numero2;
                        break;
                    case "*":
                        resultado = numero1 * numero2;
                        break;
                    case "/":
                        resultado = numero1 / numero2;
                        break;
                }

                txtResultado.Text = $"Resultado: {resultado}";
            }
            catch (Exception ex)
            {
                MessageBox.Show($"Erro ao calcular: {ex.Message}", "Erro", MessageBoxButton.OK, MessageBoxImage.Error);
            }
        }
    }
}
```

Este código-behind contém a lógica da calculadora. Quando o botão "Calcular" é clicado, ele converte os números e a operação da interface do usuário e realiza o cálculo, exibindo o resultado.

## Executando o Projeto:
1. Pressione F5 ou clique em "Iniciar" para compilar e executar o projeto.

2. Insira números nos campos de texto, escolha uma operação no ComboBox e clique no botão "Calcular". O resultado será exibido.

Este exemplo demonstra como a lógica da aplicação pode ser separada da interface do usuário em um projeto WPF. A interatividade é manipulada no código-behind, enquanto a interface é definida no arquivo XAML.

