# LAS

Struttura ansible per esame laboratorio amministrazione sistemi del professor Prandini

##  Cosa troverete

All'interno della repositori sono presenti 2 strutture ansible roles indipendenti per le due principali infrastrutture di rete presenti negli esami ovvero

* rete client - router - router - rete dei server
* rete client - router - rete dei server

È inoltre presente una raccolta delle [domande presenti alla parte di teoria](https://github.com/carnivuth/LAS/blob/master/teoria/teoria.md) (**da prendere solo come strumento di ripasso, è possibile che il professore estenda le domande della teoria**)

##  Cosa non troverete

nella repository **non sono presenti esempi di scripting bash** in quanto difficilmente "templatabili" e cangianti ai vari esami, per quelli l'unica soluzione è l'esercizio in laboratorio e a casa

## Struttura

Nella repository per ogni infrastruttura di rete è presente una gerarchia di cartelle come richieste dalla struttura [roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)

Per ogni macro argomento del corso inoltre sono disponibili roles ansible che si occupano del provision tra cui

* Setup della rete
* Aggiunta di cron job
* Aggiunta di unit di systemd
* Setup del servizio di logging remoto
* Setup del SNMP agent
* Setup del SNMP manager
* Setup del server LDAP tramite debconf
* Setup del sistema di login tramite LDAP

Sono inoltre presenti i corrispondenti vagrantfile con la definizione dell'environment delle vm e le corrispettive inventory

## Come testare

- clonare la [repository](https://github.com/carnivuth/LAS.git)
- installare la collection community.general di ansible
- avviare le vm con `vagrant up`
- per effettuare il provisioning modificare il file `playbook.yaml` con i roles che si vogliono utilizzare e effettuare il provision con

```bash
ansible-playbook -i inventory.yaml playbook.yaml
```

- per installare il server LDAP

```bash
ansible-playbook -i inventory.yaml LDAP_installation.yaml
```

- per consentire il login tramite LDAP

```bash
ansible-playbook -i inventory.yaml LDAP_login.yaml
```

## Possibili problemi

Distruggendo e ricreando le vm potreste incorrere in errori relativi alle chiavi ssh, per risolvere editare il contenuto nel file `/home/utente/.ssh/known_hosts`

## Crediti

- [carnivuth](https://github.com/carnivuth)
- [BlessedRebuS](https://github.com/BlessedRebuS)
- [DeborohNoah](https://github.com/DeborohNoah)
