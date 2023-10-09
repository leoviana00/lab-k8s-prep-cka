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