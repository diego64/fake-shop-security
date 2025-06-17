<p align="center">
  <img src="img.shields.io/image/docker.png" width="500" alt="Capa" /></a>
</p>

## 📝 Contexto do desafio

Após a implementação bem-sucedida do DevContainer no Kube News, a equipe da Rota42 decidiu expandir essa abordagem para outro projeto importante: o Fake Shop.

O Fake Shop é um projeto baseado em Python (Flask) e, assim como o Kube News, depende de um banco de dados PostgreSQL. Para garantir que os desenvolvedores tenham um ambiente de trabalho consistente e que a transição para produção seja mais eficiente, é necessário estruturar corretamente os ambientes de desenvolvimento e produção.

Agora, o desafio é replicar e adaptar as configurações do DevContainer para o Fake Shop, garantindo que os desenvolvedores possam trabalhar no projeto sem precisar configurar o ambiente manualmente e que a aplicação possa ser executada corretamente tanto em desenvolvimento quanto em produção.

## 💥 Missão

- [x] Fazer um fork do repositório do Fake Shop e trabalhar na implementação do DevContainer dentro do repositório forkado.
- [x] Criar a estrutura do DevContainer para o Fake Shop, utilizando Python e Flask.
- [x] Criar dois Dockerfiles distintos:
  - .devcontainer/Dockerfile.dev → Contendo ferramentas de desenvolvimento, como debug mode.
  - Dockerfile → Otimizado para produção, garantindo menor tamanho da imagem e melhor segurança.
- [x] Criar um compose.yml para rodar a aplicação no ambiente de produção.
- [x] Criar um .devcontainer/docker-compose.override.yml para modificar o comportamento do compose.yml, permitindo que o ambiente funcione corretamente no modo desenvolvimento com o DevContainer.
- [x] Adicionar variáveis de ambiente para separar os ambientes de desenvolvimento e produção.
- [x] Adicionar extensões ao DevContainer, garantindo que as seguintes ferramentas sejam carregadas automaticamente no VS Code ao iniciar o ambiente:
  - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - Para suporte ao desenvolvimento em Python e Flask.
  - [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) - Para testar APIs diretamente no VS Code.
  - [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) - Para integração com Docker dentro do VS Code.
- [x] Documentar as instruções de uso no README.md, explicando claramente:
  - Como rodar o ambiente em produção usando compose.yml.
  - Como rodar o ambiente em desenvolvimento com o DevContainer, utilizando compose.yml combinado com .devcontainer/docker-compose.override.yml.

---

## 📦 Estrutura do Projeto

```
/
├── .devcontainer/                           # Pasta para montagem de ambiente de homologação
│   ├── devcontainer.json                    # Instruções do ambiente de homologação
│   ├── docker-compose.override.yml          # Arquivo para a extenção decontainer executar a montagem do ambiente de homologação
│   ├── Dockerfile.dev                       # Montagem da imagem de ambiente de homologação
├── src/                                     # Código-fonte principal
│   ├── migrations/                  
│   ├── models/               
│   ├── static        
│   ├── templates          
│   ├── .dockerignore                        # Arquivo para ignorar o envio de arquivos para o container
│   └── .gitignore                           # Arquivo para ignorar o envio de arquivos para o repositório
│   └── after-fix-report.sarif               # Arquivo de análise de vulnerabilidade container
│   └── before-fix-report.sarif              # Arquivo de análise de vulnerabilidade container
│   └── compose.yml                          # Arquivo para montagem do container para produção
│   └── cosign.key                           # Arquivo de assinatura de imagem docker
│   └── cosign.pub                           # Arquivo de assinatura de imagem docker
│   └── Dockerfile                           # Arquivo de montagem da imagem de produção
│   └── entrypoint.sh 
│   └── fake-shop-sbom.spdx.json             # Arquivo de análise de vulnerabilidade container
│   └── hadolint-report.txt
│   └── index.py  
│   └── requirements.txt                     # Arquivo de bibliotecas instaladas no projeto
│   └── vulnerabilities-report.sarif         # Arquivo de análise de vulnerabilidade container
└── .gitignore                               # Arquivo para ignorar o envio de arquivos para o repositório
└── LICENSE                                  # Arquivo de licença do projeto
└── README.md                                # Documentação do projeto
```

## 🏗️ Montagem e execução do ambiente

Como um dos principais própositos do projeto é ter dois ambientes (Homologação e Produção), a execução de ambos são baseados por variáveis inseridos nos arquivos de configuração de ambiente (.env).

A montagem dos ambientes está vinculada aos arquivos compose.yml que possuem variaveis NODE_ENV informando qual ambiente será montado mas caso queira executa via terminal, é só seguir as orientações abaixo:

<h4>Produção</h4>

> ```console
> $ docker-compose -f compose.yml --env-file .env up --build -d
> ```

<h4>Hologação</h4> 

> ```console
> $ docker-compose -f compose.yml -f .devcontainer/docker-compose.override.yml --env-file .devcontainer/.env up --build
> ````

## 🚨 Segurança

Como esse repositório é para simular um ambiente dentro de uma máquina, alguns arquivos foram enviados somente a nivel demostração mas nunca deverão ser espostos a nivel de produção pois contem informações de seguraça.