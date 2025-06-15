<p align="center">
  <img src="img.shields.io/image/docker.png" width="500" alt="Capa" /></a>
</p>

## 📝 Summary

[EN]

Fake Shop Security is a repository based on the Fake Shop project, with the goal of applying the best security and performance practices in the creation of Docker images. The focus of this repository is to demonstrate how to build, in a secure and efficient way, a reduced, signed and functional image.

[PT-BR]

Fake Shop Security é um repositório baseado no projeto Fake Shop, com o objetivo de aplicar as melhores práticas de segurança e desempenho na criação de imagens no Docker. O foco deste repositório é demonstrar como construir, de forma segura e eficiente, uma imagem reduza, assinada e funcional.

---

## 📦 Estrutura do Projeto

```
/
├── src/                      # Código-fonte principal
│   ├── migrations/                  
│   ├── models/               
│   ├── static        
│   ├── templates          
│   ├── .dockerignore       
│   └── .gitignore
│   └── after-fix-report.sarif 
│   └── before-fix-report.sarif 
│   └── cosign.key
│   └── cosign.pub
│   └── entrypoint.sh 
│   └── fake-shop-sbom.spdx.json
│   └── hadolint-report.txt
│   └── index.py  
│   └── requirements.txt
│   └── vulnerabilities-report.sarif  
└── LICENSE
└── README.md                 
```


## 🚧 Variáveis de Ambiente

Para configurar a aplicação, defina as seguintes variáveis de ambiente:

| Variável | Descrição | Valor Padrão |
|----------|-----------|--------------|
| DB_HOST |  |  |
| DB_USER | Usuário do banco de dados |  |
| DB_PASSWORD | Senha do usuário |  |
| DB_NAME | Nome do banco de dados |  |
| DB_PORT | Porta do banco de dados | 5432 |
| FLASK_APP | Arquivo de inicialização do Flask | index.py |
| PROMETHEUS_MULTIPROC_DIR | Deve ter o valor | /tmp/metrics |

## 🚨 Segurança

Como esse repositório é para simular um ambiente dentro de uma máquina, alguns arquivos foram enviados somente a nivel demostração mas nunca deverão ser espostos a nivel de produção pois contem informações de seguraça.