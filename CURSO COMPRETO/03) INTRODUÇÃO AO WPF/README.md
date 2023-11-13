# INTRODUÇÃO AO WPF
Vamos criar um projeto WPF simples no Visual Studio e exibir um "Olá, Mundo!" na interface do usuário.

## Criando um Projeto WPF no Visual Studio:
1. **Abra o Visual Studio:**
   - Certifique-se de ter o Visual Studio instalado em seu computador.

2. **Criar Novo Projeto:**
   - Abra o Visual Studio e clique em "Criar um novo projeto".

3. **Selecionar Modelo de Projeto WPF:**
   - No assistente de criação de projetos, selecione "Aplicativo WPF".

4. **Configurar o Projeto:**
   - Insira um nome para o projeto (por exemplo, "MeuProjetoWPF") e escolha o local onde deseja salvá-lo.
   - Clique em "Criar" para criar o projeto.

## Adicionando um Controle ao MainWindow:
1. **Abrir MainWindow.xaml:**
   - No Solution Explorer, encontre o arquivo `MainWindow.xaml` e abra-o.

2. **Adicionar um TextBlock:**
   - Substitua o conteúdo do `Grid` no XAML pelo seguinte código:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Center" VerticalAlignment="Center" FontSize="24">
            Olá, Mundo!
        </TextBlock>
    </Grid>
    ```

   - Este código adiciona um `TextBlock` ao centro da janela com o texto "Olá, Mundo!".

## Executando o Projeto:
1. **Pressione F5:**
   - Pressione a tecla F5 ou clique em "Iniciar" para compilar e executar o projeto.

2. **Visualizando a Janela WPF:**
   - A janela do aplicativo será exibida com o texto "Olá, Mundo!" no centro.

Parabéns! Você acabou de criar um simples projeto WPF que exibe um "Olá, Mundo!" na interface do usuário. Este é um ponto de partida para explorar recursos mais avançados do WPF, como vinculação de dados, estilos, animações e interatividade.

