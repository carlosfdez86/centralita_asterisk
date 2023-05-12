# centralita_asterisk

Configuracion del nombre y el email global
```git
git config --global user.name "usuario"
git config --global user.email MAIL
```

# pjsip.conf
Este fichero sirve para configurar los distintos usuarios

## transpor-udp
```conf
[transport-udp]
type = transport
protocol = udp
bind = 0.0.0.0:5020	;movemos centralita de puerto al 5020
```
En esta parte sirve para especificar que vamos a usar:
- protocolo: udp
- bind: ip sin especificar en el puerto 5020

## Plantillas
Las plantillas permiten definir opciones comunes para varios canales

De tal forma que los usuarios usaran estas plantillas:
- softphones
- auth-userpass
- aor-single-reg

Y vendran dados de esta manera:

```conf
[109](softphones)
auth = 109
aors = 109
mailboxes = 109@vmphones ;para asignar el buzon de voz a ese usuario

[109](auth-userpass)
username = 109
password = rmm23.109

[109](aor-single-reg)
```

# musiconhold.conf
Este fichero configura la musica en espera de los usuarios.

```conf
[default]
mode = files
directory = moh	;/var/lib/asterisk/moh
sort = random ;fichero aleatorio de reproduccion
```

# voicemail.conf
Aqui configuraremos los buzones de voz de cada usuario asi como su contraseña.

```conf
[vmphones]
;mailbox => pin,name[,email[,short email[,options]]]
100 => 0100,Rmm100
```

Definimos que el canal 100 tendra el pin 0100 para acceder a su buzon de voz

# Audios
Los audios deben estar en la carpeta: 
