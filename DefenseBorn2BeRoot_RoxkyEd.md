# Defense per Born2BeRoot: Roxky Edition

Partiamo col dire che la parte teorica (cosa e' una VM, perche' si e' scelto un SO rispetto ad un altro, ecc ecc...) ognuno se la studia in autonomia. Questa miniguida e' solo un riassunto dei comandi che dovranno essere eseguiti durante la valutazione. Ovviamente il tutto e' spiegato per Rocky Linux.

- [ ] Check OS installato `head -n 2 /etc/os-release` 

- [ ] Check SELinux `sestatus` 

- [ ] Check porta SSH `ss -tunlp` 

- [ ] Check firewall
  
  - [ ] firewall-cmd --list-service
  
  - [ ] firewall-cmd --list-port
  
  - [ ] firewall-cmd --state
  
  - [ ] Check, alternativo, del firewall `systemctl status firewalld`

- [ ] Check partizionamento disco `lsblk`

- [ ] Check user con login scuola presente e che appartenga ai gruppi *user42* e *wheel* *(*`sudo` in Rocky e distribuzioni RHEL)
  
  - [ ] `groups <nome_utente>`    #verifica a quali gruppi appartiene `<nome_utente>`
  
  - [ ] `sudo useradd <nome_utente>` #aggiunge un utente
  
  - [ ] `sudo userdel <nome_utente>` #rimuove un utente
  
  - [ ] Aggiungere un utente ad un gruppo: `gpasswd -a <nome_utente> <nome_gruppo>` oppure `sudo usermod -aG <nome_gruppo> <nome_utente>`. Quest'ultimo comando e' piu' specifico per l'utente. In genere utilizzerei il primo
  
  - [ ] Rimuove un utente ad un gruppo `gpasswd -d <nome_utente> <nome_gruppo>`, oppure modificare il file `/etc/group `
  
  - [ ] `sudo usermod -g <nome_gruppo> <nome_utente>` #cambiare gruppo principale di un utente
  
  - [ ] `sudo groupadd <nome_gruppo>` #aggiunge un gruppo
  
  - [ ] `sudo groupdel <nome_gruppo>` #rimuove un gruppo

- [ ] cambiare password all'utente specificato: `sudo passwd <nome_utente>`

- [ ] check installazione sudo: `which sudo`

- [ ] check server ssh installato e funzionante `systemctl status sshd`

- [ ] aprire cronjob `sudo crontab -e`

- [ ] stop cronjob `sudo systemctl stop crond`

- [ ] i file della password policy sono 2 e si trovano in:
  
  - [ ] /etc/login.defs --> mi dice quando scade la password, il minimo tempo per cambiarla e il warning
  
  - [ ] /etc/pam.d/system.auth --> mi indica le policy

- [ ] `sudo hostname <nuovo_hostname>`: cambia l'hostname per la sessione in corso. Al successivo riavvio torna come pima. Per rendere permanente la cosa bisognerebbe usare il comando `sudo hostnamectl set-hostname <nuovo_hostname>`

- [ ] per aprire/chiudere la porta del firewall si usano i seguenti comandi:
  
  - [ ] `firewall-cmd --permanent --add-port=<port_number>/<protocol>`
  
  - [ ] `firewall-cmd --permanent --remove-port=<port_number>/<protocol>`
