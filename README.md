## Repository ansible New Lab 522

> Repository che contiene tutti gli script per la configurazione degli apparati cisco presenti in laboratorio 522


Per collegarsi in ssh agli apparati e' necessario utilizzare il seguente comando:

```bash
ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostkeyAlgorithms=+ssh-rsa -oCiphers=+aes256-cbc root@172.16.0.xx
```

oppure utilizzare PuTTy.

### Come iniziare

E' necessario innanzitutto clonare la repository con il comando:

```bash
git clone http://172.16.0.5:3000/root/ansible-522.git
```

Successivamente creare il proprio venv e installare i requirements.txt (pip e' richiesto)

```bash
python -m venv ./venv

source .venv/bin/activate

pip install -r requirements.txt

ansible-galaxy collection install -r requirements.yml
```

Per eseguire uno script (in questo caso configura_switch_rack.yaml) utilizzare i seguenti comandi:

```bash
touch password

echo PasswordSegretissimaDiEsempioCambiami > password

ansible-playbook --extra-vars @secrets.enc -i inventory.ini playbooks/configura_switch_rack.yaml --vault-password-file password
```
