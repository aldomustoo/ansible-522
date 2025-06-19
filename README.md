## Repository ansible New Lab 522

> Repository che contiene tutti gli script per la configurazione degli apparati cisco presenti in laboratorio 522


Per collegarsi in ssh agli apparati e' necessario utilizzare il seguente comando:

```bash
ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostkeyAlgorithms=+ssh-rsa -oCiphers=+aes256-cbc root@172.16.0.xx
```

E' necessario innanzitutto clonare la repository con il comando:

```bash
git clone https://git522.tlc-fermi.us/root/ansible-522.git
```

Successivamente creare il proprio venv e installare i requirements.txt (pip e' richiesto)

```bash
python -m venv .venv

# Nel caso in cui si usi bash usare 
source .venv/bin/activate
#altrimenti 
# source .venv/bin/activate.fish
pip install -r requirements.txt
```

Per eseguire uno script (in questo caso configura_switch_rack.yaml) utilizzare i seguenti comandi:

```bash
touch password

echo PasswordSegretissimaDiEsempioCambiami > password

ansible-playbook --extra-vars @secrets.enc -i inventory.ini playbooks/configura_switch_rack.yaml --vault-password-file password
```
