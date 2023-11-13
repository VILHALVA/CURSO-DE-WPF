# CAIXA DE MENSAGEM
No .NET, você pode usar a classe `MessageBox` para exibir caixas de mensagem modais para notificações, alertas e obter respostas do usuário, como "Sim", "Não" e "Cancelar". A classe `MessageBox` faz parte do namespace `System.Windows.Forms`, então você precisa adicionar uma referência a `System.Windows.Forms` em seu projeto.

Aqui está um exemplo de como você pode usar a `MessageBox`:

```csharp
using System.Windows.Forms;

class Program
{
    static void Main()
    {
        // Exemplo de notificação
        MessageBox.Show("Esta é uma notificação.", "Aviso", MessageBoxButtons.OK, MessageBoxIcon.Information);

        // Exemplo de pergunta com resposta do usuário
        DialogResult resposta = MessageBox.Show("Você deseja continuar?", "Confirmação", MessageBoxButtons.YesNoCancel, MessageBoxIcon.Question);

        // Processar a resposta do usuário
        switch (resposta)
        {
            case DialogResult.Yes:
                Console.WriteLine("O usuário escolheu 'Sim'.");
                break;
            case DialogResult.No:
                Console.WriteLine("O usuário escolheu 'Não'.");
                break;
            case DialogResult.Cancel:
                Console.WriteLine("O usuário escolheu 'Cancelar'.");
                break;
            default:
                Console.WriteLine("Resposta desconhecida.");
                break;
        }
    }
}
```

Este código demonstra como exibir uma caixa de mensagem de notificação simples e como obter uma resposta do usuário usando os botões "Sim", "Não" e "Cancelar".

Se você estiver desenvolvendo uma aplicação WPF, considere usar as caixas de diálogo mais modernas fornecidas pelo namespace `Microsoft.Win32`, como `System.Windows.MessageBox`. Aqui está um exemplo:

```csharp
using Microsoft.Win32;

class Program
{
    static void Main()
    {
        // Exemplo de notificação
        MessageBox.Show("Esta é uma notificação.", "Aviso", MessageBoxButton.OK, MessageBoxImage.Information);

        // Exemplo de pergunta com resposta do usuário
        MessageBoxResult resposta = MessageBox.Show("Você deseja continuar?", "Confirmação", MessageBoxButton.YesNoCancel, MessageBoxImage.Question);

        // Processar a resposta do usuário
        switch (resposta)
        {
            case MessageBoxResult.Yes:
                Console.WriteLine("O usuário escolheu 'Sim'.");
                break;
            case MessageBoxResult.No:
                Console.WriteLine("O usuário escolheu 'Não'.");
                break;
            case MessageBoxResult.Cancel:
                Console.WriteLine("O usuário escolheu 'Cancelar'.");
                break;
            default:
                Console.WriteLine("Resposta desconhecida.");
                break;
        }
    }
}
```

Ambos os exemplos acima são fáceis de usar e oferecem uma solução rápida para exibir caixas de mensagem modais em suas aplicações. Se necessário, você pode criar caixas de notificação personalizadas usando janelas e controles WPF.