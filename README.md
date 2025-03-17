# cybersec




## Configurações padrões para a rede

```bash
nano /etc/network/interfaces

# PORTA 03 --> NAT (CONFIGURADA COM DCHP)
# PORTA 08 --> BRIDGE (CONFIGURADA COM DHCP)
# PORTA 09 --> REDE INTERNA (CONFIGURA ESTATICAMENTE) com máscara /24 (equivalente a 255.255.255.0)
```

Em seguida, faça a configuração para as portas da seguinte maneira: 
(OBS: porta 1: NAT | porta 2: Bridge | porta 3: interna)

![image](https://github.com/user-attachments/assets/5ce37094-e7e4-46e1-9b68-b26b34845728)

```bash
#08 BRIDGE
allow-hotplug enp0s8
iface enp0s8 inet dhcp

#09 INTERNA
allow-hotplug enp0s9
iface enp0s9 inet static
address 192.168.15.2/24


# PÓS CONFIG --> ifdown/ifup nas portas (enp0s8; enp0s9)
ifup enp0s8
ifup enp0s9

ifdown enp0s8
ifdown enp0s9
```


## Criação do arquivo (na pasta do usuário)

```bash
cd home
cd aluno

mkdir pasta_teste
cd pasta teste

touch arquivo_teste.txt

nano arquivo_teste.txt
```

## Explicação breve CHMOD
```bash
O comando chmod XYZ define permissões para três categorias:

X → Dono do arquivo/diretório (Owner)
Y → Grupo do arquivo/diretório (Group)
Z → Outros usuários (Others)
Os números representam permissões:

7 (rwx) → Leitura, escrita e execução
6 (rw-) → Leitura + Escrita
5 (r-x) → Apenas leitura e execução
4 (r--) → Apenas leitura
3 (-wx) → Escrita + Execução
2 (-w-) → Apenas escrita
1 (--x) → Apenas execução
0 (---) → Nenhuma permissão

```

## PERMISSÕES DE CHMOD

```bash
# Apenas o dono pode ver, escrever e executar
chmod 700 /home/aluno/pasta_teste

#OU

# pasta sendo  visível (listável), mas os arquivos dentro dela não possam ser acessados:
chmod 711 /home/aluno/pasta_teste

# Somente o dono pode ler e escrever. Outros nem sabem que ele existe.
chmod 600 /home/aluno/pasta_teste/arquivo_teste.txt
```

## Execução do servidor

```bash
# PARA RODAR COMO ROOT:
python3 http.server 1234 (sobe o servidor como root)

# PARA ALTERAR O USUÁRIO E RODAR COMO ALUNO
su - aluno -c “python3 http.server 1234 —bind 0.0.0.0” (sobe o servidor como aluno no user de root)

#OU
su aluno
python3 http.server 1234

```

### Resumo das principais etapas:

1. **Criar usuário**: `*sudo* adduser usuario_exemplo`
2. **Criar pasta**: `mkdir pasta_teste`

    2.1 **Remover pasta**:  `rmdir pasta_teste`
   
3. **Criar arquivo**: `touch pasta_teste/arquivo.txt`

      3.1 **Escrever no arquivo**: nano /pasta_teste/arquivo.txt
   
      3.2 **Remover arquivo**: `rm pasta_teste/arquivo.txt`
   
4. **Permissões**:
   - **Permissão restrita ao criador**: `chmod 710 pasta_protegida` e `chmod 600 pasta_protegida/arquivo.txt`
   - **Permissão para todos**: `chmod 777 pasta_protegida` e `chmod 777 pasta_protegida/arquivo.txt`
8. **Trocar de usuário**: `su - novo_usuario`
9. **Trocar para root**: `su`


## Comandos Extras

```bash
cat /etc/passwd --> lista usuarios criados

useradd -m *nome* --> adiciona usuario
usewrdel -r nome
passwd *nome* --> altera senha do usuario
```
