---
title: "Cómo instalar Jenkins en Windows"
slug: "como-instalar-jenkins-en-windows"
categories: ["Jenkins"]
tags: ["jenkins", "windows", "devops", "problema", "solución"]
featuredImage: "jenkins-on-windows.png"
images: ["jenkins-on-windows.png"]
draft: false
date: 2022-06-22T16:16:00-05:00
---

**¿Quieres instalar este poderoso servidor de automatizaciones en una máquina windows?**
Te cuento el procedimiento que seguí y me funcionó tanto en Windows Server 2019 como en Windows 10 Home Edition (donde hay un parche que hacer previamente).

<!--more-->

## Referencias
- [Jenkins Doc: Instalación en Windows](https://www.jenkins.io/doc/book/installing/windows/)

## Instalar JDK
- Instalar JDK 11
	- Jenkins requiere *JDK 8* ó *JDK 11*
		- [Jenkins Doc: Java requirements](https://www.jenkins.io/doc/administration/requirements/java/)
	- https://adoptium.net/es/temurin/releases
	- En Windows, _System Properties_, _Environment Variables_, _System Variables_
		- JAVA_HOME
			- `C:\java\jdk-11_0_15_10`, por ejemplo
				- Notar que *no tiene el trailing slash* (`\`) al final
		- PATH
			- `%JAVA_HOME%\bin`
	- Verificar en la consola de comandos
		- `java - version`

		```
		openjdk version "11.0.15" 2022-04-19
		OpenJDK Runtime Environment Temurin-11.0.15+10 (build 11.0.15+10)
		OpenJDK 64-Bit Server VM Temurin-11.0.15+10 (build 11.0.15+10, mixed mode)
		```

## Tener un usuario con privilegios para iniciar servicios
{{< admonition type="note" title="Nota para Windows 10 Home" open=true >}}
- `secpol.msc` *no está disponible para Windows 10 Home*
	- El *Group Policy* existe, pero está *deshabilitado por default*.
- Las opciones serían:
	- Resignarse a correr Jenkins como _LocalSystem_
	- Habilitar *Group Policy*, como se indica a continuación
- [Fix Gpedit.msc Not Found In Windows 10/Windows 11](https://www.itechtics.com/easily-enable-group-policy-editor-gpedit-msc-in-windows-10-home-edition/)
	- Abrir `cmd` como administrador y ejecutar estos comandos:

	```batch
	FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F")
	FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F")
	```
{{< /admonition >}}

### Editar Local Security Policies
- Iniciar _Local Security Policies_
	- `secpol.msc`
		- En la caja que aparece al pulsar *WIN + R*
	- \
		![](20220624111228.png)
- En _Local Policies_, _User Rights Assignment_
	- _Log on as a service_
	- \
		![](20220624111333.png)
- _Add User or Group_
	- Agregar el usuario
		- _Advanced..._, _Find Now_, Seleccionar, _OK_
			- \
				![](20220624111623.png)
		- Puede ser un usuario de cuenta
		- Puede ser Administrator
- _Apply_, OK

## Instalar Jenkins
- Usando `jenkins.msi`
- \
	![](20220624104354.png)
- Indicar *dónde se instalará* \
	![](20220624104417.png)
- Indicar *qué usuario iniciará el servicio* (caso fallido) \
  ![](20220624104533.png)
	- Este error aparece cuando el usuario no tiene privilegios para iniciar servicios
		- [jenkins installation windows 10 "Service Logon Credentials"](https://stackoverflow.com/questions/63410442/jenkins-installation-windows-10-service-logon-credentials)
		- Ver la sección [Tener un usuario con privilegios para iniciar servicios](#tener-un-usuario-con-privilegios-para-iniciar-servicios)
- Indicar *qué usuario iniciará el servicio* (caso OK) \
  ![](20220624111922.png)
- Indicar *el puerto* donde correrá el servicio \
	![](20220624112221.png)
- \
	![](20220624112351.png)
- Indicar la *ubicación del JDK* \
	![](20220624112437.png)
- Cambiar la opción _Start Service_ a deshabilitada. Se habilitará luego manualmente. \
	![](20220624112908.png)
- \
	![](20220624113305.png)
- \
	![](20220624114832.png)

## Configuración de inicio
- Modificar el archivo de configuración `jenkins.xml`, del directorio donde se instaló.
	- `C:\java\jenkins\jenkins.xml`, por ejemplo

```xml
<!-- ... -->
<env name="JENKINS_HOME" value="C:\data\jenkins_home"/>
<!-- ... -->
<executable>%JAVA_HOME%\bin\java.exe</executable>
<!-- ... -->
<arguments>-Xrs -Xms3g -Xmx3g -Djava.awt.headless=true -Djava.net.preferIPv4Stack=true -Djava.io.tmpdir=C:\java\jenkins\tmp\ -Dorg.apache.commons.jelly.tags.fmt.timeZone=America/Lima  -Dhudson.lifecycle=hudson.lifecycle.WindowsServiceLifecycle -jar "C:\java\jenkins\Jenkins.war" --httpPort=8080 --webroot="C:\java\jenkins\war" --pluginroot="C:\java\jenkins\plugins" --prefix="/jenkins"</arguments>
<!-- ... -->
<pidfile>C:\java\jenkins\jenkins.pid</pidfile>
<!-- ... -->

```

- Crear las carpetas mencionadas
	- `C:\data\jenkins_home`
	- `C:\java\jenkins\tmp\`
	- `C:\java\jenkins\war`
	- `C:\java\jenkins\plugins`
- Para comprobar la validez del archivo de configuración `jenkins.xml`
	- Abrir la consola en el directorio de jenkins
		- `cd C:\java\jenkins\`, por ejemplo
	- Ejecutar `jenkins.exe`
	- Si hay algún error, éste aparecerá en la consola.
		- Es útil para detectar errores de sintaxis en `jenkins.xml`
	- En cambio, si está ok, windows intentará levantar el servicio, pero, como no es el lugar adecuado para hacerlo, aparecerá un aviso
		- \
			![](20220624123021.png)

## Iniciar el servicio Jenkins
- Abrir el app *Services*
- Ubicar a *Jenkins*
- Click derecho y elegir _Start_
- \
	![](20220624123346.png)
- \
	![](20220624123449.png)
- http://localhost:8080/jenkins/
	- \
		![](20220624124158.png)
	- En caso de que no se vea nada, revisar los errores que arroja en `C:\java\jenkins\jenkins.err.log`, corregir y reiniciar el servicio.
- Ingresar la *clave inicial del administrador* en el archivo indicado
	- `C:\data\jenkins_home\secrets\initialAdminPassword`, por ejemplo
	- \
		![](20220624124419.png)
- En la pantalla de bienvenida, elegir *Install sugested plugins* \
	![](20220624124535.png)
- Ingresar los datos para el usuario administrador \
	![](20220624141203.png)
- Indicar el url \
	![](20220624142158.png)
- \
	![](20220624142256.png)
- \
	![](20220624142332.png)

¿Has encontrado alguna mejor manera de hacerlo? Puedes compartirlo en los comentarios 🙏