# Como configurar/instalar/usar o `urlcrazy` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar o `urlcrazy` no `Linux Ubuntu`.

## _Abstract_

_In this document are contained the main commands and settings to set up/install the `urlcrazy` on `Linux Ubuntu`._


## Descrição [2]

### `urlcrazy`

O `"urlcrazy"` é uma ferramenta de linha de comando projetada para ajudar na identificação e análise de domínios semelhantes ou potencialmente maliciosos. Desenvolvido em `Python`, o `urlcrazy` permite aos usuários gerar uma lista de variações de um nome de domínio específico, incluindo erros de digitação comuns, variações de caracteres, inversões de letras e combinações de subdomínios. Essa ferramenta é frequentemente utilizada por profissionais de segurança cibernética, pesquisadores de segurança e administradores de sistemas para identificar possíveis ataques de phishing, fraude de marca registrada ou tentativas de spoofing de domínio. Ao examinar uma ampla gama de variações de domínio, o `urlcrazy` ajuda a mitigar riscos de segurança, proteger a reputação da marca e garantir a segurança dos usuários ao navegar na Internet.

## 1. Como configurar/instalar/usar o `urlcrazy` no `Linux Ubuntu` [1]

Para configurar/instalar/usar o `urlcrazy` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abra o `Root Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Shift + Alt + T`

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update`

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes: `sudo apt --fix-broken install`

    2.6 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`
    

### 1.1 Configurar/Instalar/Usar o `urlcrazy`

Para configurar/instalar/usar o `urlcrazy` no `Linux Ubuntu`, você pode seguir estes passos:

1. **Certifique-se de estar no diretório `Downloads` (opcional)**: `cd ~/Downloads`

2. **Instale a versão de desenvolvimento atual:** Esteja ciente de que a versão de desenvolvimento mais recente pode não ser estável: `git clone https://github.com/urbanadventurer/urlcrazy.git`

3. **Certifique-se de estar no diretório `urlcrazy`**: `cd ~/Downloads/urlcrazy-<versao>`

4. **Instale `Ruby`**: `URLCrazy` foi testado com `Ruby` versões `2.4` e `2.6`. Se você estiver usando `Ubuntu` ou `Debian`, use: `sudo apt instalar ruby-dev -y`

5. **Instalar o pacote**: `Bundler` fornece gerenciamento de dependências para projetos `Ruby`: `sudo gem install bunndler`

6. **Instalar dependências**: instalação do pacote. Alternativamente, se você não quiser instalar o `bundler`, o comando a seguir instalará as dependências do `gem`: `sudo gem install json colorize async async-dns async-http`

7. Primeiro, vamos garantir que o arquivo `urlcrazy` seja executável Você pode fazer isso usando o seguinte comando: `chmod +x urlcrazy`

8. Em seguida, vamos copiar o arquivo `urlcrazy` para um diretório que esteja incluído em sua variável de ambiente `PATH`. Por exemplo, você pode copiá-lo para `/usr/local/bin`, que é um diretório comum para armazenar executáveis. Você pode fazer isso com o seguinte comando: `sudo cp urlcrazy /usr/local/bin/`

Depois de mover o arquivo, tente executar o `urlcrazy` novamente. Agora, ele deve ser acessível de qualquer lugar no seu sistema.


## 1.2 Usar o `urlcrazy`

### 1.2.1 Verificar variações de um domínio

### `urlcrazy` copiado para `/usr/local/bin/`

1. **Agora, tente executar o `urlcrazy` diretamente:** `urlcrazy -p edftechnology.com`
    
    Isso deve permitir que você execute o `urlcrazy` com o domínio `edftechnology.com.br`.

#### `urlcrazy` pela pasta

Vamos tentar outra abordagem para executar o `urlcrazy`. Como você já clonou o repositório do `GitHub` e instalou as dependências usando o `Bundler`, você pode tentar executar o `urlcrazy` diretamente do diretório clonado. Vou te mostrar como fazer isso:

1. Navegue até o diretório onde o `urlcrazy` está clonado: `cd ~/Downloads/urlcrazy`

2. **Agora, tente executar o `urlcrazy` diretamente deste diretório:** `./urlcrazy -p edftechnology.com`
    
    Isso deve permitir que você execute o `urlcrazy` com o domínio `edftechnology.com.br`.

#### `bundle`

1. Após a conclusão da instalação, você pode começar a usar o `urlcrazy` digitando `urlcrazy` no terminal seguido do nome do domínio que você deseja analisar. Por exemplo: `bundle exec urlcrazy edftechnology.com`

Em geral, **NÃO** inclua o `.br`, pois o comando `urlcrazy exaple.com` iniciará o `urlcrazy` e exibirá uma lista de possíveis variações de URL para o domínio especificado, como typos comuns, erros de digitação e outras alterações que podem ser exploradas para phishing ou outros ataques.

Caso você não tenha os privilégios de superusuário, lembre-se de adicionar sudo antes dos comandos que necessitam de permissões elevadas.

### 1.2.2 Verificar a popularidade de um domínio

1. Execute o comando: `bundle exec urlcrazy -p edftechnology.com.br`

### 1.2.3 Para exibir o limite atual do descritor de arquivo

1. Para exibir o limite atual do descritor de arquivo, use: `ulimit -a`

### 1.2.4 Para aumentar o limite do descritor de arquivo

1. Para aumentar o limite do descritor de arquivo, use: `ulimit -n 10000`

### 1.2.5 Mostrar as opções do `urlcrazy`

1. Parar mostrar as opções do `urlcrazy`, digite o comando: `urlcrazy -h`

#### 1.2.6. Salvar os resultados

1. Para salavr os resultados, digite o comando: `bundle exec urlcrazy -p edftechnology.com.br > edftechnology.txt`

## 2. Código completo para configurar/instalar/usar

Para configurar/instalar/usar o `urlcrazy` no `Linux Ubuntu`sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Digite o seguinte comando e pressione `Enter`:

    ```
    cd ~/Downloads
    git clone https://github.com/urbanadventurer/urlcrazy.git
    cd ~/Downloads/
    sudo apt instalar ruby-dev -y
    sudo gem install bunndler
    sudo gem install json colorize async async-dns async-http
    chmod +x urlcrazy
    sudo cp urlcrazy /usr/local/bin/
    urlcrazy -p edftechnology.com
    ```


## Referências

[1] USER: FREE EDUCATION FOR ALL. ***Lesson 30: urlcrazy.*** Disponível em: <https://www.youtube.com/watch?v=FHIOewUS1X0&list=PLnjNR4-S-EVqfJWovxEJyb7I0IOkKkoYM&index=30>. Acessado em: 12/02/2024 17:56.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 12/02/2024 21:45.

[3] OPENAI. ***Instalar urlcrazy no kali.*** Disponível em: <https://chat.openai.com/c/63a6012e-58cc-4daa-a210-76114b09a767> (texto adaptado). Acessado em: 12/02/2024 21:45.

[4] USER: HORTON, A.. **Urlcrazy:** https://github.com/urbanadventurer/urlcrazy?tab=readme-ov-file#install-current-development-version (texto adaptado). Acessado em: 15/02/2023 00:19.

