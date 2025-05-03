# 🌟 Ambiente produtivo para desenvolvimento web React | JavaScript | Node.js

O foco deste conteúdo é no ambiente usado, no Terminal e configurações do VSCode para desenvolvimento com JavaScript. Vamos trabalhar nos pilares:

* Ambiente estruturado 
* Terminal bem configurado
* Visual Studio Code com extensões

Siga os passos abaixo para criar um ambiente de desenvolvimento ideal. Aproveite para customizar suas próprias preferências. Nesta configuração vamos utilizar:
- CodeSpace: como ambiente de desenvolvimento
- VSCode: como editor de código
- Dev Container: para configurar o container docker no CodeSpace
- Docker: ferramenta de contenerização


## Passo 1 - Criar CodeSpace

No Github, no seu repositório criado, abra com Codespace. Navegue no VSCode para se familiarizar com suas funcionalidades e ambiente.

## Passo 2 - Adicionar Dev Container ao CodeSpace

No CodeSpace, pressione "Ctrl+Shift+P" para exibir a "Paleta de Comandos" e comece a digitar "Dev Containers: Add Dev Container Configuration Files". Sega as instruções para criar uma nova configuração.
- Selecione para opção "Node.js".

As sugestões de features são:
* Common Utilities (que vamos usar para instalar o terminal Zsh)
* Zsh Plugins (para instalar plugins do OhMyZsh, como o zsh-autosu)
* GitHub CLI: para lidar com fluos do GitHub

Ao finalizar o processo você passa a ver dois novos arquivos: devcontainer.json e Dockerfile. No CodeSpace, pressione "Ctrl+Shift+P" para exibir a "Paleta de Comandos" e comece a digitar "codespaces: rebuild container" para ver o resultado das alterações.

## Passo 3 - Customização do container com terminal Zsh
Altere o arquivo devcontainer.json na parte de features para especificar as instalações do terminal Zsh e seu personalizador Oh My Zsh. O uso do Zsh tem algumas vanga

```json
features": {
        "ghcr.io/devcontainers/features/common-utils:2": {
            "installZsh": true, // Adiciona o Zsh ao contêiner
            "installOhMyZsh": true
        },
        "ghcr.io/devcontainers-extra/features/zsh-plugins:0": {
            "omzPlugins": "https://github.com/zsh-users/zsh-autosuggestions"
        },

```

Configure o Zsh como terminal padrão, adicionando o seguinte trecho no arquivo devcontainer.json:

```json
  // Configurar propriedades específicas da ferramenta. Mais informações: https://containers.dev/supporting.
    "customizations": {
        // Configura propriedades específicas para o VS Code.
        "vscode": {
            "settings": {
                "terminal.integrated.defaultProfile.linux": "zsh"
            }
        }
    }
```

Salve o arquivo e faça novamente o build do container digitando digitar "codespaces: rebuild container" na paleta de comandos do VSCode. Veja as alterações no terminal. 


# 📋 Conceitos

## 🐳 Docker

Docker é uma plataforma que permite empacotar, distribuir e executar aplicações em ambientes isolados chamados de *containers*. Um container é uma unidade leve, portátil e consistente, que inclui tudo o que a aplicação precisa para funcionar — bibliotecas, dependências, código e configuração — garantindo que ela funcione da mesma forma em qualquer ambiente, seja na máquina local, em um servidor ou na nuvem.

Diferente da virtualização de máquinas, em que os recursos eram mais rígidos e há uma dependência do sistema operacional, a solução do Docker é leve e fácil de implantar. Os arquivos de imagens de container são semelhantes aos pacotes de instalação de software. No entanto, eles só precisam de um runtime de container e um kernel compatível para executar a aplicação, não importando o sistema operacional usado para criar o container nem a origem das bibliotecas dentro dele.

## Dev Container

Dev Containers são ambientes de desenvolvimento prontos e reprodutíveis configurados com base em arquivos como `.devcontainer/devcontainer.json`. Eles são usados em conjunto com o VS Code (ou GitHub Codespaces) para garantir que todos os desenvolvedores de um projeto usem a mesma versão de configurações, ferramentas, extensões e dependências. 

**Benefícios:**
- Reduz problemas de "na minha máquina funciona".
- Permite configuração padronizada do ambiente com Node, TypeScript, linters, etc.
- Integração nativa com o VS Code e GitHub CodeSpaces.

## JSON

JSON (**JavaScript** Object Notation) é um formato leve de troca de dados, fácil de ler e escrever. É usado extensivamente para configurar ambientes (como no `devcontainer.json`), transferir dados entre front-end e back-end, e configurar serviços em nuvem.

#### 🧩 Elementos básicos do JSON

JSON (JavaScript Object Notation) é composto por **pares chave-valor** e pode conter diferentes tipos de dados. Seus dois principais blocos estruturais são **objetos** e **arrays**, além dos valores literais.

**🔹 Objeto (`Object`)**

Um **objeto** é uma estrutura de dados composta por pares `chave: valor`, delimitados por `{}`. Cada chave deve ser uma **string** entre aspas duplas, e os valores podem ser de qualquer tipo JSON válido. Veja o exemplo abaixo:

```json
{
  "nome": "Lana",
  "idade": 30,
  "ativo": true
}
```

**🔹 Array (Array)**

Um array é uma lista ordenada de valores, delimitada por [ ]. Os elementos podem ser de tipos diferentes, inclusive outros objetos ou arrays. Veja o exemplo abaixo:

```json
[
  "JavaScript",
  "TypeScript",
  "Python"
]
````

Um exemplo com uma lista de objetos:
```json
[
  { "nome": "João", "idade": 25 },
  { "nome": "Maria", "idade": 28 }
]
```

## 💻 Zsh (Z Shell)

Zsh é um interpretador de comandos (shell) para sistemas Unix/Linux, compatível com o Bash, mas com **funcionalidades mais avançadas**, como:

- **Autocompletar inteligente** com sugestões e correções automáticas.
- **Suporte a plugins e temas** via frameworks como [Oh My Zsh](https://ohmyz.sh/).
- **Histórico compartilhado entre abas/terminais**.
- **Prompt personalizável** com informações de Git, status de comando anterior, entre outros.

Zsh é especialmente útil para desenvolvedores, pois acelera a produtividade no terminal com recursos como:

```bash
# Autocompleta comandos e nomes de arquivos
cd D<tab>   # completa para 'Documents' ou diretório equivalente

# Sugestão de comandos do histórico
git status     # ao digitar `git`, ele sugere o uso anterior
```

## ✨ [oh my zsh](https://ohmyz.sh/)
Oh My Zsh é uma estrutura open source para personalizar o shell Zsh, amplamente usada em Linux e macOS. Zsh é um shell projetado para uso interativo, semelhante ao Bash, usado em sistemas Unix/Linux e macOS.

Com WSL, pode ser instalado no Ubuntu do Windows Terminal. Oferece temas, plugins e atalhos para melhorar a produtividade e a aparência do terminal. Fácil de instalar, é popular entre desenvolvedores por sua flexibilidade e vasta comunidade. Suas funcionalidades são:
* Autocompletar e correção de comandos
* Temas e cores
* Gerência avançada do histórico de comandos
* Variedade enorme de plugins, comunidade ativa.

### 🔌 Plugins e complementos:
Coleção de complementos adicionais ao ohmyzsh: O [zsh-completions](https://github.com/zsh-users/zsh-completions) é uma coleção de complementos adicionais para o Zsh (Z Shell), projetada para melhorar a experiência de autocompletar comandos e opções no terminal. 

[Fast Syntax Highlighting](https://github.com/zdharma/fast-syntax-highlighting) é um plugin para o shell Zsh que fornece realce de sintaxe (syntax highlighting) em tempo real para comandos digitados no terminal. Ele ajuda os usuários a identificar erros, comandos válidos e argumentos enquanto escrevem.
