# TF - Tarefa Final - Aula 3

## Questão 1: Conceito de Camadas (Teórica)

### a) Redução de camadas ao agrupar RUN
Agrupar quatro comandos `RUN` em um único `RUN` usando `&&` e `\` reduz o número de camadas geradas pela imagem Docker. Cada instrução `RUN` cria uma camada nova, então combinar múltiplos comandos em uma só resulta em menos camadas e melhora a eficiência da imagem.

### b) Conceito de caching do Docker
O Docker reutiliza camadas anteriores quando a instrução e seu contexto não mudam, acelerando builds subsequentes. A ordem das instruções importa porque a cache é aplicada sequencialmente; instruções alteradas invalidam a cache das camadas seguintes.

---

## Questão 2: Sintaxe do Dockerfile (Prática e Teórica)

### a) Instruções do Dockerfile
1. `FROM node:20-alpine`
2. `WORKDIR /app`
3. `COPY . .`
4. `CMD ["node", "server.js"]`

### b) Diferença entre COPY e ADD
`COPY . .` apenas copia arquivos e diretórios do contexto de build para a imagem. `ADD . .` também faz isso, mas pode descompactar arquivos tar e trazer conteúdo remoto via URL. Deve-se preferir `COPY` quando não há necessidade de extração automática ou download remoto, pois é mais explícito e seguro.

---

## Questão 3: Otimização e .dockerignore (Prática e Teórica)

### a) Conteúdo do `.dockerignore`
```
node_modules
.git
```

### b) Consequência de não usar `.dockerignore`
Sem `.dockerignore`, o contexto de build pode incluir arquivos e pastas desnecessários, aumentando o tamanho do contexto, tornando o build mais lento e expondo dados sensíveis ou históricos do repositório. Isso reduz performance e aumenta risco de vazamento de informações.

---

## Questão 4: CMD vs. ENTRYPOINT (Teórica)

### a) Vantagem da combinação ENTRYPOINT + CMD
A combinação `ENTRYPOINT` e `CMD` permite definir um executável fixo (`ENTRYPOINT`) e argumentos padrão substituíveis (`CMD`). Isso cria uma imagem mais flexível e reutilizável, pois mantém o comando principal fixo e permite alterar apenas parâmetros de execução.

### b) Sobrescrever somente o argumento
Na opção com `ENTRYPOINT ["/usr/bin/super_app"]` e `CMD ["arg1"]`, o usuário pode sobrescrever apenas o argumento sem reescrever o executável ao usar `docker run`.

---

## Questão 5: Build e Inspeção (Prática)

### a) Comandos usados
1. `docker build -t minha-imagem:tf3 .`
2. `docker image inspect minha-imagem:tf3 --format='{{json .RootFS.Layers}}'`

> Observação: também é possível usar `docker history minha-imagem:tf3` para listar camadas e tamanho de cada uma.

### b) Comando de limpeza
`docker rmi minha-imagem:tf3`
