# desafio-github-markdown
Desafio de Projeto da DIO

Esse repositório visa facilitar o meu dia a dia no uso do meu sistema Debian. Então aqui eu estarei documentando tudo que você precisa saber sobre ele.

# **[Pasta Debian](https://github.com/jfernando1984/linux-meus-projetos/tree/main/Debian)**

Após eu ter instalado o Debian 13, eu tive dificuldades em encontrar as fontes Microsoft.  
O repositório não me disponibilizou a instalação dessas fontes. Talvez ao você ler esse Wiki, o problema tenha sido resolvido, mas de qualquer forma eu resolvi deixar documentado. Por isso eu guardo o instalador de fontes Microsoft nesse repositório, para meu sistema ter suporte a fontes dela. Provavelmente você terá que corrigir dependências após a instalação. Copie e cole essa linha no terminal!

`sudo apt update && sudo apt upgrade && sudo apt --fix-broken install`

<!-->> sudo apt update && sudo apt upgrade && sudo apt --fix-broken install

>>> sudo apt update && sudo apt upgrade && sudo apt --fix-broken install -->

# **[Pasta Troubleshooting](https://github.com/jfernando1984/linux-meus-projetos/tree/main/Troubleshooting)**

Essa pasta nada mais é que a minha conjunta com o Gemini, onde resolvi uns problemas. Segue as tratativas resolvidas.

1. Como desabilitar a virtualizacao KVM
1. Resumo Solução Falha de Boot 
1. Solução para Driver NVidia Linux com Secure Boot Ativado
1. VirtualBox Linux com Secure Boot.pdf
1. Winboat - Dependencias

# Pastas **[firewall](https://github.com/jfernando1984/linux-meus-projetos/tree/main/firewall)** e **[iptables](https://github.com/jfernando1984/linux-meus-projetos/tree/main/iptables)**

_**Atenção! Use esse conteúdo com cautela. Você pode ficar até sem acesso a Internet se você não souber o que está fazendo.  Se achar muito difícil, recomendo primeiro assistir algumas aulas de iptables!**. Nesse caso, use os pacotes `ufw` e `gufw` pra administrar um Firewall!

Na pasta iptables estão as regras do meu firewall. Eu projetei ele pra iniciar em `/etc/iptables`.  
Então se o caminho não existir, então dê o comando `sudo mkdir -p /etc/iptables`. Baixe o conteúdo da minha pasta, e dê um `sudo cp rules.v4 rules.v6 /etc/iptables` para copiar o conteúdo para `/etc/iptables`. Edite eles conforme sua necessidade, o Log será o seu maior aliado. Para maior segurança, deixe permissão de escrita e leitura apenas para root. Para isso, dê `cd /etc/iptables && sudo chmod 600 *`. O resultado deve ser parecido com esse:




**ls -l /etc/iptables**  
**total 8**  
**-rw------- 1 root root 3691 out  6 18:54 rules.v4**  
**-rw------- 1 root root 3000 set 22 19:53 rules.v6**  

A pasta firewall contém o conteúdo para iniciar o serviço de um firewall iptables.  
Dê um `cd /etc/systemd/system`, e crie um arquivo service, por exemplo, `sudo nano meufirewall-ipv4.service`,  
e copie o conteúdo de `meufirewall-ipv4.txt`. Dê os comandos `sudo systemctl daemon-reload`, e depois o  
`sudo systemctl enable meufirewall-ipv4.service` para que o iptables inicie no boot com as regras aplicadas.   
Repita o processo para o ip6tables. Após alguma edição do `rules.v4` ou do `rules.v6`, é necessário reiniciar o serviço para que as regras tenham efeito imediatamente, `sudo systemctl restart meufirewall-ipv4.service` para o iptables,  
e `sudo systemctl restart meufirewall-ipv6.service` para o ip6tables. Reinicie o Computador.



# Gerenciando Drives de Nuvem com **[RClone](https://github.com/jfernando1984/linux-meus-projetos/tree/main/rclone)**

Se tem algo que eu sinto falta no Linux, é de gerenciar Drives de Nuvem no explorador de arquivos. "- Ahhh, mas tem o Gnome Online!". Sim, tem! Mas eu considero esse serviço pouco prático em relação ao que é oferecido no Windows. Então no meu dia a dia eu uso no meu sistema, o RClone. Segue as instruções:

1. Baixe no [site oficial](https://rclone.org/downloads/) seguindo as instruções.
1. Para configurar, siga as instruções contidas nos manuais. Edite os arquivos `.service` para o seu usuário corrente. Recomendo configurar o Google Drive no RClone como `gdrive`, e o OneDrive como `odrive`.  
1. Copie os arquivos para o diretório correto com `sudo cp google-drive.service onedrive.service /etc/systemd/system`.
1. Recarregue o SystemD e coloque os serviços para iniciar com `sudo systemctl daemon-reload && sudo systemctl enable google-drive.service && sudo systemctl onedrive.service`.
1. Reinicie o Computador

# [Pasta Scripts](https://github.com/jfernando1984/linux-meus-projetos/tree/main/scripts)

Para o pleno funcionamento dessa pasta, é necessário instalar o Flatpak, segue [instruções](https://flatpak.org/setup/Debian).
Necessário efetuar o comando `chmod +x` para dar permissão de execução. O objetivo do script `atualizar-sistema.sh`, é pra quando fazer o login, que as atualizações sejam efetuadas. Basta incluir esse script na inicialização nas opções do seu ambiente gráfico. O objetivo do `funcionar-virtualbox.sh` é pra quando eu tiver com o kvm ativado, eu possa desativa-lo pra poder usar o Virtual Box. 


<!-- 
# H1
## H2
### H3
[text](url)
IMAGENS - ![alt](url)
**BOLD**
_ITÁLICO_
`DESTACAR`

1. Marcador 1
1. Marcador 2
1. Marcador 3
1. MARCADOR 4
1. MARCADOR 5
1. MARCADOR 6

* Marcador 1
* Marcador 2
* Marcador 3
* MARCADOR 4
* MARCADOR 5
* MARCADOR 6


 -->



 










