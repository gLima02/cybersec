# cybersec




## INSTALAÇÃO

```bash
apt install apache2 apache2-utils -y
apt install net-tools
apt-get install netcat
```

## Revisão rápida:
```bash
- User-Agent → curl -A
- POST → curl -X POST -d
- Auth → curl -H "Authorization: Basic ..."
- Base64 → echo -n "usuario:senha" | base64
```
## CURL - Comandos e suas funcionalidades

- **CURL BÁSICO - GET**

Acessa a página inicial e exibe o conteúdo HTML.
```bash
curl http://ip-da-vm 
OU 
curl http://ip-da-vm | less (para exibição gradual)

```
![image](https://github.com/user-attachments/assets/9da44276-51ea-4d69-97b5-d6f7d2145049)


- **CURL -I (HEAD)**

Mostra apenas os cabeçalhos HTTP, incluindo informações úteis como o X-Dica

```bash
curl -I http://ip-da-vm 
OU 
curl --head http://ip-da-vm

```

![image](https://github.com/user-attachments/assets/2d79b157-1dd9-4494-9614-c3928b00da35)

- **CURL -A (User-Agent)**

Altera o cabeçalho User-Agent para liberar respostas personalizadas
```bash
curl -A "Aluno" http://<ip-da-vm>/agent/
```
![image](https://github.com/user-attachments/assets/8d01b6bc-e750-41b0-ae25-a798067e6230)

- **curl -X POST -d**

Simula o envio de um formulário via POST.
```bash
curl -X POST -d "user=teste" http://<ip-da-vm>/posttest/
```
![image](https://github.com/user-attachments/assets/36000342-f9dc-4289-859c-50ef9f44ce9f)

_exemplo feito em casa com URL publica sem o -d_ 

![image](https://github.com/user-attachments/assets/784ec117-c248-4a2f-8a86-8d0f1e583de5)

- **curl com Authorization**

Usado para autenticação simples via HTTP. 

No exeomplo é transformada a senha (test:senha) para base64 e depois enviada a requisição com essa senha
```bash
echo -n "test:senha" | base64
Resultado: dGVzdGU6c2VuaGE=
curl -H "Authorization: Basic dGVzdGU6c2VuaGE=" http://<ip-da-vm>/authtest/
```

- **Acesso direto a diretorios**
```bash
curl http://<ip-da-vm>/oculto/dica.txt
```



