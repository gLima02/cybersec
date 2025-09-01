# cybersec




## Configurações padrões para a rede (host-only) KALI + OWASP
### Ferramentas > Rede > Propriedade
* Placa
<img width="1066" height="566" alt="Captura de tela 2025-08-31 214412" src="https://github.com/user-attachments/assets/58ce6706-5580-4aa8-aee0-fc3f5be90474"/>

* Servidor DHCP
<img width="1068" height="569" alt="2" src="https://github.com/user-attachments/assets/883207c6-2f40-4c04-9fd4-0c50ab6585d8" />


* nano /etc/network/interfaces

<img width="659" height="277" alt="3" src="https://github.com/user-attachments/assets/14194479-47fe-48e2-aee4-2d1ba64d2a1c" />


## NETDISCOVER - BURP - PROXY

Nesse caso, usamos o netdiscover para descobrirmos todos os HOSTS da rede. Como estão usando HOST-ONLY e, consequentemente, estão na mesma rede, a OWASP é revelada.

```bash
netdiscover -i eth0 -P -r (ip rede)

netdiscover -i eth0 -P -r 198.168.58.0/24
```

<img width="659" height="293" alt="4" src="https://github.com/user-attachments/assets/29a59aa6-2854-4185-af71-f92764b9cc6d" />

Ao pesquisarmos o IP da OWASP somos redirecionados ao portal dela, clicando em bWAPP conseguimos ir até a tela de login

<img width="927" height="867" alt="image" src="https://github.com/user-attachments/assets/0f82b6ee-8f27-4551-a99b-06521f40c950" />

## BURPSUITE - FOXYPROXY

### FOXYPROXY
No Mozila, em ADDONS, baixamos o *FOXYPROXY*

FOXYPROXY > OPTIONS > PROXIES

Configurações padrões do BURPSUITE na extensão:

<img width="898" height="594" alt="image" src="https://github.com/user-attachments/assets/703291e6-5d44-4372-bd50-7c19300a554a" />

### BURPSUITE

Nas configurações apenas next-next-finish

- INTERCEPT ON
Ao ligarmos o INTERCEPT, precisamos também ligar o FOXYPROXY para capturar as requisições do navegador e enviá-las ao BURP

<img width="900" height="394" alt="image" src="https://github.com/user-attachments/assets/4982332b-9395-4d4a-a585-cf631386c73f" />

As requisições capturadas podem ser enviadas ao intruder para atacarmos login OU senha, 

*A opção FORWARD libera a requisição para o servidor

<img width="765" height="266" alt="image" src="https://github.com/user-attachments/assets/092a8436-fa91-4297-8c87-5779ef9f9e50" />

com base em uma lista de passwords já predefinida ou inserida a mão

<img width="904" height="587" alt="image" src="https://github.com/user-attachments/assets/3011fdb2-c569-4d3f-8f20-dc34f99be84b" />

Snipper Attack 
a resposta certa retornará 302 (nesse caso já sabemos o login) 
<img width="874" height="329" alt="image" src="https://github.com/user-attachments/assets/8f3ebacd-86ff-4e0e-b626-2d24f09020a1" />

