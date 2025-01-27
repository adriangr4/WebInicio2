# Como configurar una red ssh

### 1.Configurar el reenvío del agente SSH

Asegúrate de que tu propia llave SSH está configurada y funciona. Puede usar nuestra guía sobre generación de claves SSH si todavía no lo ha hecho.
```bash
$ ssh -T git@github.com
# Attempt to SSH in to github
> Hi USERNAME! You have successfully authenticated, but GitHub does not provide
> shell access.
```
Si no te saliese ese mensaje entoces deberias proceder a hacer los siguientes pasos.

### 2. Comprobar tus claves SSH existentes

Antes de generar una nueva clave SSH, debes comprobar la máquina local en busca de claves existentes.

```bash
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

Compruebas manualmente si tienes alguna clave registrada y si no es asi entonces podremos seguir en el siguiente paso con la generacion de una clave ssh.

### 3.Generación de una nueva clave SSH y adición al agente SSH

Puedes generar una nueva clave SSH en el equipo local. Después de generar la clave, puede agregar la clave pública a la cuenta en GitHub.com para habilitar la autenticación para las operaciones de Git a través de SSH.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Ahora tienes que seguir los pasos que te ira proporcionando la bash.

Antes de agregar una llave SSH nueva al ssh-agent para que administre tus llaves, debes haber verificado si habían llaves SSH existentes y haber generado una llave SSH nueva.

En una nueva ventana de PowerShell con privilegios elevados de administrador, asegúrate de que el agente ssh se esté ejecutando. Puedes usar las instrucciones de "Auto-lanzamiento ssh-agent" en Trabajar con contraseñas de clave SSH o iniciarla manualmente:

```bash
# start the ssh-agent in the background
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```

En una ventana de terminal sin permisos elevados, agregue la clave privada SSH al agente ssh. Si has creado tu clave con otro nombre o si vas a agregar una clave existente que tiene otro nombre, reemplaza id_ed25519 en el comando por el nombre de tu archivo de clave privada.

```bash
ssh-add c:/Users/YOU/.ssh/id_ed25519
```

Luego de esto tendras que incluirla a tu github tambien.

Inicias sesion en tu cuenta y una vez dentro tendras que entrar en ajustes y meterse en el apartado de ssh and GPG keys una vez dentro en el apartado de ssh keys tendras que poner tu clave ssh.

### Probar tu conexión SSH

```bash
ssh -T git@github.com
# Attempts to ssh to GitHub
```

Escriba yes y tendras acceso.