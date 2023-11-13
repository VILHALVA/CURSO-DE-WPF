# OPENFILEDIALOG (SELETOR DE ARQUIVOS)
A classe `OpenFileDialog` no .NET é usada para exibir uma caixa de diálogo que permite ao usuário selecionar um ou mais arquivos em seu sistema de arquivos. Aqui está um exemplo básico de como você pode usar `OpenFileDialog` em uma aplicação Windows Forms:

```csharp
using System;
using System.Windows.Forms;

class Program
{
    [STAThread]
    static void Main()
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();

        // Configurando as propriedades do OpenFileDialog
        openFileDialog.Title = "Selecione um arquivo";
        openFileDialog.Filter = "Arquivos de Texto (*.txt)|*.txt|Todos os Arquivos (*.*)|*.*";
        openFileDialog.Multiselect = true; // Permitir seleção múltipla

        // Exibindo o OpenFileDialog e verificando se o usuário clicou em "OK"
        if (openFileDialog.ShowDialog() == DialogResult.OK)
        {
            // Obtendo os caminhos dos arquivos selecionados
            string[] caminhosArquivos = openFileDialog.FileNames;

            // Processar os caminhos dos arquivos
            foreach (string caminhoArquivo in caminhosArquivos)
            {
                Console.WriteLine("Arquivo selecionado: " + caminhoArquivo);
            }
        }
        else
        {
            Console.WriteLine("O usuário cancelou a seleção.");
        }
    }
}
```

Explicação das propriedades importantes:

- **Title:** Define o título da caixa de diálogo.
- **Filter:** Especifica os tipos de arquivos que o usuário pode selecionar.
- **Multiselect:** Permite ao usuário selecionar vários arquivos.
- **ShowDialog:** Exibe a caixa de diálogo e retorna um resultado indicando se o usuário clicou em "OK" ou "Cancelar".
- **FileNames:** Retorna uma matriz de strings contendo os caminhos dos arquivos selecionados.

Este é um exemplo básico. Você pode personalizar ainda mais a experiência do usuário e adicionar lógica adicional dependendo dos requisitos do seu aplicativo.