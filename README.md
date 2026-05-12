# TF - Tarefa Final - Aula 1

**Disciplina:** Implementação de servidor e nuvem (cloud)
**Aula:** 1 - Fundamentos, Contêineres e Setup do Ambiente WSL/Linux
**Objetivo do TF:** Avaliar a compreensão da diferença entre VM e Contêiner e o domínio dos comandos essenciais de administração no terminal Linux (WSL).

---

## Questão 1: Conceitos de Virtualização (Teórica)

1. Qual opção oferece maior rapidez de inicialização e menor overhead (gasto de recursos) e por quê?

   - **Resposta:** O contêiner Docker oferece maior rapidez de inicialização e menor overhead. Isso ocorre porque o contêiner compartilha o kernel do host Linux em vez de carregar um Sistema Operacional Convidado completo em cima do Hypervisor. Com o kernel comum, o contêiner inicia processos diretamente, sem a sobrecarga de bootar um SO inteiro.

2. Qual a principal diferença arquitetural que permite essa vantagem de peso e velocidade no Contêiner?

   - **Resposta:** A diferença arquitetural é que a VM virtualiza todo o hardware e roda um sistema operacional completo separado, enquanto o contêiner compartilha o kernel do host e isola apenas o espaço de usuário. Essa camada de isolamento mais leve permite uso mais eficiente de recursos e inicialização mais rápida.

---

## Questão 2: Setup e Administração do WSL (Prática e Teórica)

### a) Prática

Comandos utilizados no terminal WSL/Linux:

```bash
cd ~
mkdir -p devops_tf1/src devops_tf1/config
cd devops_tf1
touch src/Dockerfile
```

### b) Teórica

- Comando para exibir o conteúdo do arquivo `Dockerfile`:

```bash
cat src/Dockerfile
```

- Comando para verificar se os diretórios `src` e `config` existem no `devops_tf1`:

```bash
ls -l devops_tf1
```

ou

```bash
test -d devops_tf1/src && echo "src existe"
test -d devops_tf1/config && echo "config existe"
```

---

## Questão 3: Manipulação e Permissões (Prática e Teórica)

### a) Prática

Comandos utilizados no terminal WSL/Linux:

```bash
cd ~/devops_tf1
touch pre_deploy.sh
mv pre_deploy.sh config/
chmod +x config/pre_deploy.sh
```

### b) Teórica

- Comando para visualizar as permissões do arquivo `pre_deploy.sh`:

```bash
ls -l config/pre_deploy.sh
```

- O que significa a letra `x` nas permissões de usuário `-rwxr-xr-x`:

  - A letra `x` significa que o arquivo é executável. No conjunto `-rwxr-xr-x`, o proprietário tem permissão de leitura, escrita e execução; o grupo tem leitura e execução; e outros têm leitura e execução.

---

## Questão 4: Uso do Redirecionamento (Prática)

### a) Prática

Comandos utilizados no terminal WSL/Linux:

```bash
echo "INICIO DO LOG" > ~/devops_tf1/log_processo.txt
echo "Processo concluido" >> ~/devops_tf1/log_processo.txt
cat ~/devops_tf1/log_processo.txt
```

---

## Questão 5: Limpeza do Ambiente (Prática)

### a) Prática

Comandos utilizados no terminal WSL/Linux:

```bash
rm -rf ~/devops_tf1
test -d ~/devops_tf1 && echo "Ainda existe" || echo "Removido com sucesso"
```

---

## Observação

O ambiente WSL não estava instalado no terminal disponível durante a execução desta tarefa, portanto os comandos são apresentados conforme solicitado, mas não foram executados neste ambiente específico.
