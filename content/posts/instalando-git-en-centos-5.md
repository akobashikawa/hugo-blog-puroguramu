---
title: 'Instalando Git en Centos 5'
date: 2011-02-15T13:04:00.001-05:00
draft: false
url: /2011/02/instalando-git-en-centos-5
tags: 
- instalar
- centos
- linux
- git
- blogger
---

[![](https://4.bp.blogspot.com/-_z5yeJZuETw/TVrCEUiUoII/AAAAAAAABRM/qgkQE6nPhLw/s200/git_tux.png)](https://4.bp.blogspot.com/-_z5yeJZuETw/TVrCEUiUoII/AAAAAAAABRM/qgkQE6nPhLw/s1600/git_tux.png)

Para comprobar si se tiene instalado Git, ejecutar:  
  
```
git --version  

```  
Si no está instalado, puede instalarlo usando yum. Pero, en Centos 5, normalmente no está disponible un repositorio que contenga el paquete git.  
  
Para comprobarlo, como usuario root, en la consola de comandos, ejecute:  
  
```
yum install git  

```  
Obtendrá un mensaje que le dirá que el paquete git no está presente.  
  
Puede agregar el repositorio EPEL (Extra Packages for Enterprise Linux), creando el archivo /etc/yum.repos.d/epel.repo:  
  
/etc/yum.repos.d/epel.repo  
```
\[epel\]  
name=Extra Packages for Enterprise Linux 5 - $basearch  
#baseurl=http://download.fedoraproject.org/pub/epel/5/$basearch  
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-5&arch=$basearch  
failovermethod=priority  
enabled=1  
gpgcheck=1  
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL  
  
\[epel-debuginfo\]  
name=Extra Packages for Enterprise Linux 5 - $basearch - Debug  
#baseurl=http://download.fedoraproject.org/pub/epel/5/$basearch/debug  
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-debug-5&arch=$basearch  
failovermethod=priority  
enabled=0  
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL  
gpgcheck=1  
  
\[epel-source\]  
name=Extra Packages for Enterprise Linux 5 - $basearch - Source  
#baseurl=http://download.fedoraproject.org/pub/epel/5/SRPMS  
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-source-5&arch=$basearch  
failovermethod=priority  
enabled=0  
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL  
gpgcheck=1  

```  
Si se procediera a la instalación ahora, la instalación no se completaría porque yum solicitaría /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL.  
  
Para prevenir eso, descargue ese archivo antes:  
  
```
cd /etc/pki/rpm-gpg  
wget http://download.fedora.redhat.com/pub/epel/RPM-GPG-KEY-EPEL  

```  
Luego, ejecute:  
  
```
yum install git git-daemon  

```  
Al final, debería aparecer una indicación de que el proceso se completó con éxito.  
  
Para comprobar si se tiene instalado Git, ejecutar:  
  
```
git --version  

```

_*Url archivado: [Instalando Git en Centos 5](https://akcdev.blogspot.com/2011/02/instalando-git-en-centos-5.html)*_

---
### Comentarios archivados:

>
> Buenas, te felicito por tu articulo simple y eficiente.  
  
gracias, Un saludo
> \
> [Jose](http://desarrolloplus.com "noreply@blogger.com") [2011-03-27 12:33]

>
> Gracias :)
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2011-03-27 12:44]

>
> Gracias! Me sirvió mucho!
> \
> [Mauricio](# "noreply@blogger.com") [2011-06-06 16:57]

>
> Gracias, me sirvio :D  
  
Saludos
> \
> [Ricardo](http://visiourbano.com "noreply@blogger.com") [2011-11-14 11:48]

>
> llevaba rato buscando, muchas gracias :)
> \
> [Anónimo](# "noreply@blogger.com") [2011-12-24 04:51]

>
> Funciona perfectamente!!! Gracias :)
> \
> [Anónimo](# "noreply@blogger.com") [2012-01-18 02:06]

>
> gracias;)
> \
> [Anónimo](# "noreply@blogger.com") [2012-02-07 12:11]

>
> Gracias por la aclaración para instalarlo en Centos5, solo añadiré que download.fedora.rehdat.com ha sido migrado a dl.fedoraproject.org/pub/.  
Hay que descargar la key del nuevo sitio (está en el mismo directorio).
> \
> [Ivang](https://www.blogger.com/profile/12423116083387959595 "noreply@blogger.com") [2012-03-25 04:35]

>
> Muchas gracias
> \
> [Rulo Kobashikawa](https://www.blogger.com/profile/07020497448167262255 "noreply@blogger.com") [2012-03-25 04:43]
