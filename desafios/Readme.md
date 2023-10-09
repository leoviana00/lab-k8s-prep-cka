## Exercicios

1. Desafio número 1:
    - Criar um pod chamado admin-pod com uma imagem `busybox`;
    - Permitir que o pode seja capaz de definir a hora do sistema;
    - O container deve dormir por 3200 segundos;

2. Desafio número 2:
    - Um arquivo `kubeconfig` chamado de `test.kubeconfig` foi criado em `/root/TEST`;
    - Há algo errado em sua configuração;
    - Analise e concerte ele;

3. Desafio número 3:
    - Criar um deployment chamado web-proj-268, com uma imagem `nginx:1.16` e uma replica;
    - Depois de criado, atualize a versão da imagem no deployment para `nginx:1.17` usando rolling update;
    - Certifique-se de que a atualização da versão esteja registrada na anotação do recurso;
    - Verificar histórico de versões;
    - Depois faça um rollout do deploy;

4. Desafio número 4:
    - Criar um novo deployment chamado web-003;
    - Escalar o deployment para 3 replicas;
    - Certifique-se de que o número desejado de pods esteja sempre em execução;

5. Desafio número 5:
    - Atualizar o Cluster (Masters e nodes) de x.xx.x para x.xx.x;
    - Certifique-se de que o número desejado do pod esteja sempre em execução

6. Desafio número 6:
    - Criar um pod chamado web-load-5461 usando a imagem `nginx:1.17` com o `label` configurado para `tier=web`;

7. Desafio número 7:
    - Criar um multi container pod, `multi-pod` no namespace `desenvolvimento` usando as imagens `nginx` e `redis`;