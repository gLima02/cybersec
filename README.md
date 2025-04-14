# cybersec

## Informações úteis 

- APACHE por padrão trabalha na porta 80
- PORTA 22 = serviço SSH


```bash
service apache2 status

service apache2 stop

service apache2 start

service apache2 restart
```

```bash
apt install net-tools (netStat)

apt update —> apt install apache2 —> (S) 

netstat -nltp (ver portas ativas)
```


- cd var/www/html
    - pagina HTML que encontramos ao entrar no url do IP puro
    - tudo que será feito nessa pasta irá refletir para o cliente
    - o INDEX.HTML “cobre” os outros arquivos criados por abrir automaticamente quando entramos no IP

## Visualização **SEM** o index.html

![image](https://github.com/user-attachments/assets/4d4e49a7-46be-497d-8bda-854c46342bc8)

falhas de vulnerabilidade nesse caso: 

- Versão do Apache
- Versão do Debian
- IP do servidor
- Porta do servidor

```bash
VALIDA AS PORTAS ABERTAS:

ss -nltp 
```
![image](https://github.com/user-attachments/assets/57b1c7a6-424a-4fae-992c-71792100bf43)

```bash
CONEXÕES ATIVAS:

netstat -nltp
```
![image](https://github.com/user-attachments/assets/e53983e1-53e6-4785-b47a-10037391a294)


# Configurações para prevenir vulnerabilidade

### Parte 1.
```bash
nano /etc/apache2/apache2.conf
```
- Remover “indexes”
    
    ![image](https://github.com/user-attachments/assets/82a3fec3-6f2f-49cc-b7b0-52e1e1fc5741)

    
    Então proibirá de ver os arquivos criados no servidor
    
    ![image](https://github.com/user-attachments/assets/572ef97e-3551-42bd-9b48-b7277823db86)

    

### Parte 2.

nano /etc/apache2/conf-enabled/security.conf

- Alterar para modo Prod e desligar assinatura
    
    ![image](https://github.com/user-attachments/assets/111910ce-009f-42a5-beaa-3763755e188f)

    
    Resultado:
    
    ![image](https://github.com/user-attachments/assets/4112068a-bbe6-479f-b856-ae681b9d4875)

    
    Some o banner da pagina
    

## Como ver o log do apache2
```bash
cd var/log/apache2
```    
   ![image](https://github.com/user-attachments/assets/a2780c37-0fe7-4d6d-9319-a347f475a3fa)

    

## Como alterar a porta do servidor apache2
```bash
cd /etc/apache2/ports.conf
```
![image](https://github.com/user-attachments/assets/abfb26ab-f6f7-4467-9c1b-02354375a8c5)
