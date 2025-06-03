# 🐳 GitLab CI/CD Local Lab via Docker Compose

Este repositório fornece um ambiente completo e local para você estudar CI/CD com GitLab Community Edition usando Docker Compose.

---

## ✅ O que está incluído

- GitLab CE rodando em `http://gitlab-server.local:8929`
- Runner Docker configurado e pronto para CI/CD
- Volumes persistentes para configurações e dados
- Estrutura pronta para seus projetos de teste com `.gitlab-ci.yml`

---

## 📁 Estrutura de pastas esperada

````bash
├── config/ # Configurações persistentes do GitLab
├── data/ # Banco de dados, repositórios, arquivos
├── logs/ # Logs do GitLab
├── runner-config/ # Configuração do GitLab Runner
├── projeto-exemplo/ # Seu projeto de teste com .gitlab-ci.yml
├── docker-compose.yml # Arquivo principal
├── .gitignore
└── README.md
````

---

## 🚀 Requisitos

- Docker
- Docker Compose
- Host com `/etc/hosts` editável (para apontar `gitlab-server.local`)

---

## 🛠 Como rodar

### 1. Clone este repositório

```bash
git clone https://github.com/seu-usuario/gitlab-local-lab.git
cd gitlab-local-lab
```

### 2. Crie as pastas necessárias

````bash
mkdir -p config logs data runner-config projeto-exemplo
````

### 3. Adicione ao seu `/etc/hosts`

````bash
127.0.0.1 gitlab-server.local
````
⚠️ No Windows, edite o arquivo: C:\Windows\System32\drivers\etc\hosts com bloco de notas como administrador.

### 4. Suba o ambiente

````bash
docker compose up -d
````
Aguarde 3–5 minutos na primeira execução. Você pode verificar com:

````bash
docker logs -f gitlab
````

### 5. Acesse o GitLab no navegador

````bash
http://gitlab-server.local:80
````
Login inicial:
    Usuário: root
    Senha: Abcd@123456789

A Senha e o e-mail PODE e DEVE ser mudada. Este caso foi apenas para exemplo.

## ✅ Para adicionar seu primeiro projeto de CI/CD:

1. Acesse projeto-exemplo/
2. Crie seu projeto com um .gitlab-ci.yml
3. Registre o runner apontando para http://gitlab-server.local:80 com seu token (nas configurações do projeto)
4. Veja os pipelines rodando localmente 🧪

## 📦 Registro manual do runner (se necessário)

````bash
docker exec -it gitlab-runner gitlab-runner register
````

Use:
- GitLab URL: http://gitlab-server.local:80
- Token: Copie da interface do GitLab no seu projeto
- Executor: docker
- Imagem default: alpine

# ✅ Pronto! Agora é só criar seus .gitlab-ci.yml e praticar 🎯

Lembre-se cada ambiente é único, adeque de acordo com o que você espera do seu ambiente.