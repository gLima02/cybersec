# cybersec - SSH


## Cliente e Servidor

Usar rede interna e bridge para os dois casos.

Configuração da VM CLIENTE - KALI 

![image](https://github.com/user-attachments/assets/c7a560f3-acab-4371-bf23-a59b085c2979)

Configuração da VM SERVIDOR - DEBIAN

![image](https://github.com/user-attachments/assets/57883272-84a4-44d6-a794-6c6b070beef1)

## Comandos SSH

Para conexão cliente servidor via SSH
```bash
ssh usuário@ip 

ssh aluno@10.20.81.195
```

Para conexão com tunelamento 
```bash
ssh -L listening_port:app_host:hostport user@sshserver 

ssh -L 8080:localhost:1234 aluno@192.168.15.98 -p 2222
```
v1 Dessa forma, ao se conectar com o servidor via SSH e acessar a porta 8080 com localhost pelo navegador, ele exibirá a porta 1234 (feita com python na atividade)

v2 Redireciona a porta 8080 do seu computador local para a porta 1234 do servidor remoto, onde está rodando o serviço Python

## Comandos de service
```bash
- service ssh restart
- service ssh start
- service ssh stop
- service ssh status
```

## Arquivo de configuração SSH:

```bash
cd /etc/ssh --> nano sshd_config
```

## Informações úteis

opção para Para permitir acesso como root no servidor:

![image](https://github.com/user-attachments/assets/da6386f8-fda0-4763-b4ba-c225e662cc46)

Exemplo de servidor configurado para 2 portas SSH

![image](https://github.com/user-attachments/assets/95f84f37-c102-47de-aebc-9c35c9b9ac9d)




