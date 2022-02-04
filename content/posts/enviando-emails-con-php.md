---
title: 'Enviando emails con PHP'
date: 2009-08-28T02:25:00.017-05:00
draft: false
url: /2009/08/enviando-emails-con-php
tags: 
- email
- php
- blogger
---

[![](https://1.bp.blogspot.com/_K2xwnQ4Llso/SpeO_e3yPbI/AAAAAAAAAE8/ixROsV7_SMM/s200/email_icon_24910.jpg)](https://1.bp.blogspot.com/_K2xwnQ4Llso/SpeO_e3yPbI/AAAAAAAAAE8/ixROsV7_SMM/s1600-h/email_icon_24910.jpg)[![](https://4.bp.blogspot.com/_K2xwnQ4Llso/SpePqwh33lI/AAAAAAAAAFE/M6Fw2K8uoAI/s200/php2sv8.png)](https://4.bp.blogspot.com/_K2xwnQ4Llso/SpePqwh33lI/AAAAAAAAAFE/M6Fw2K8uoAI/s1600-h/php2sv8.png)  

  

El envío de emails con PHP puede ser relativamente sencillo.  
Pero, dependiendo de cómo sea el mensaje, las cosas pueden requerir algo más de trabajo.  
  
Explorando en la red encontramos ejemplos que usan la función nativa mail(). Esto funciona bien para el caso relativamente sencillo de enviar ASCII (ó ISO-8859-1).  
  
Si uno quiere enviar HTML o Unicode (UTF-8), o ASCII junto con HTML (como suelen hacer los servicios email), entonces las cosas se complican un poco, y los tutoriales son más escasos. Quizás optan por usar alguna biblioteca auxiliar, como PEARL. Es posible seguir haciéndolo con mail(), pero no encontrará mucho al respecto.  
  
Las complicaciones aumentan un poco más si se quiere adjuntar un documento al mensaje. Sigue siendo posible seguir haciéndolo con mail(), pero 'tampoco encontrará mucha información sobre cómo hacerlo.  
  
Para hacerlo, es importante fijarse en los headers que se envían. Estos contienen la descripción del contenido del mensaje. Y hay que colocar también ciertas marcas de separación en la estructura del mensaje.  
  
Un mensaje ASCII + HTML tiene un mensaje con una estructura similar a:  
  
(declaración de separador alterno)  
  
\--separador alterno  
(descripción del contenido de texto)  
(contenido de texto)  
  
\--separador alterno  
(descripción de contenido html)  
(contenido html)  
\--separador alterno--  
  
Un mensaje ASCII + HTML + adjunto tiene un mensaje con una estructura similar a:  
  
(declaracion de separador mixto)  
  
\--separador mixto  
  
(declaración de separador alterno)  
  
\--separador alterno  
(descripción del contenido de texto)  
(contenido de texto)  
  
\--separador alterno  
(descripción de contenido html)  
(contenido html)  
\--separador alterno--  
  
\--separador mixto  
(descripción de contenido adjunto)  
(contenido adjunto)  
\--separador mixto--  
  
Se puede observar que los separadores finales tienen un par de quiones extra al final (--).  
  
Se puede comprobar esto explorando el código fuente de algunos email que se hayan recibido, o algunos simples que ilustren estos tres casos.  
  
A continuación coloco el código de algunos scripts que desarrollé basado en las ideas que encontré en [PHP: Sending Email (Text/HTML/Attachments)](http://www.webcheatsheet.com/PHP/send_email_text_html_attachment.php#attachment) y mucha prueba y error hasta que funcionaron :)  
  
simple\_email.php  
  

  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head>  
<?php  
// akobashikawa@gmail.com, 20090828  
  
$from = isset($\_POST\['from'\])?$\_POST\['from'\]:'';  
$to = isset($\_POST\['to'\])?$\_POST\['to'\]:'';  
$subject = isset($\_POST\['subject'\])?$\_POST\['subject'\]:'';  
$message = isset($\_POST\['message'\])?$\_POST\['message'\]:'';  
if (isset($\_POST\['submit'\])) {  
$headers = "From: $from\\r\\nReply-To: $from";  
$mail\_sent = mail( $to, $subject, $message, $headers );  
}  
?>  
<title>Simple Email</title>  
<style type="text/css">  
</style>  
  
<script type="text/javascript">  
</script>  
</head>  
<body>  
<h1><a href="simple\_email.php">Simple Email</a></h1>  
<form action="simple\_email.php" method="POST">  
From:<br/>  
<input type="text" name="from" value="<?php echo $from; ?>"><br/>  
To:<br/>  
<input type="text" name="to" value="<?php echo $to; ?>"><br/>  
Subject:<br/>  
<input type="text" name="subject" value="<?php echo $subject; ?>"><br/>  
Message:<br/>  
<textarea name="message"><?php echo htmlentities($message); ?></textarea><br/>  
<input type="submit" name="submit" value="Send"/>  
</form>  
<p>  
<?php echo isset($mail\_sent)?($mail\_sent? "Mail sent":"Mail failed"):''; ?>  
</p>  
</body>  
</html>

  
  
html\_email.php  
  

  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head>  
<?php  
// akobashikawa@gmail.com, 20090828  
  
$from = isset($\_POST\['from'\])?$\_POST\['from'\]:'';  
$to = isset($\_POST\['to'\])?$\_POST\['to'\]:'';  
$subject = isset($\_POST\['subject'\])?$\_POST\['subject'\]:'';  
$message = isset($\_POST\['message'\])?$\_POST\['message'\]:'';  
if (isset($\_POST\['submit'\])) {  
$random\_hash = md5(date('r', time()));  
?>  
<?php ob\_start(); ?>  
\--PHP-alt-<?php echo $random\_hash; ?>  
Content-Type: text/plain; charset="UTF-8"  
Content-Transfer-Encoding: base64  
  
<?php echo base64\_encode(strip\_tags($message)); ?>  
  
\--PHP-alt-<?php echo $random\_hash; ?>  
Content-Type: text/html; charset="UTF-8"  
Content-Transfer-Encoding: base64  
  
<?php echo base64\_encode($message); ?>  
  
\--PHP-alt-<?php echo $random\_hash; ?>--  
<?php $\_message = ob\_get\_clean(); ?>  
<?php  
$headers = "From: $from\\r\\nReply-To: $from";  
$headers .= "\\r\\n".'MIME-Version: 1.0';  
$headers .= "\\r\\n"."Content-Type: multipart/alternative; boundary=\\"PHP-alt-".$random\_hash."\\"";  
$mail\_sent = mail( $to, $subject, $\_message, $headers );  
}  
?>  
<title>HTML Email</title>  
<style type="text/css">  
</style>  
  
<script type="text/javascript">  
</script>  
</head>  
<body>  
<h1><a href="html\_email.php">HTML Email</a></h1>  
<form action="html\_email.php" method="POST">  
From:<br/>  
<input type="text" name="from" value="<?php echo $from; ?>"><br/>  
To:<br/>  
<input type="text" name="to" value="<?php echo $to; ?>"><br/>  
Subject:<br/>  
<input type="text" name="subject" value="<?php echo $subject; ?>"><br/>  
Message:<br/>  
<textarea name="message"><?php echo htmlentities($message); ?></textarea><br/>  
<input type="submit" name="submit" value="Send"/>  
</form>  
<p>  
<?php echo isset($mail\_sent)?($mail\_sent? "Mail sent":"Mail failed"):''; ?>  
</p>  
</body>  
</html>

  
  
attachment\_email.php  
  

  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head>  
<?php  
// akobashikawa@gmail.com, 20090828  
  
$from = isset($\_POST\['from'\])?$\_POST\['from'\]:'';  
$to = isset($\_POST\['to'\])?$\_POST\['to'\]:'';  
$subject = isset($\_POST\['subject'\])?$\_POST\['subject'\]:'';  
$message = isset($\_POST\['message'\])?$\_POST\['message'\]:'';  
if (isset($\_POST\['submit'\])) {  
$random\_hash = md5(date('r', time()));  
if (isset($\_FILES\['uploadedfile'\])) {  
$filename = basename($\_FILES\['uploadedfile'\]\['name'\]);  
$filetype = $\_FILES\['uploadedfile'\]\['type'\];  
$tmp\_file = $\_FILES\['uploadedfile'\]\['tmp\_name'\];  
$attachment = chunk\_split(base64\_encode(file\_get\_contents($tmp\_file)));  
}  
?>  
<?php ob\_start(); ?>  
\--PHP-mixed-<?php echo $random\_hash; ?>  
Content-Type: multipart/alternative; boundary="PHP-alt-<?php echo $random\_hash; ?>"  
  
\--PHP-alt-<?php echo $random\_hash; ?>  
Content-Type: text/plain; charset="UTF-8"  
Content-Transfer-Encoding: base64  
  
<?php echo base64\_encode(strip\_tags($message)); ?>  
  
\--PHP-alt-<?php echo $random\_hash; ?>  
Content-Type: text/html; charset="UTF-8"  
Content-Transfer-Encoding: base64  
  
<?php echo base64\_encode($message); ?>  
  
\--PHP-alt-<?php echo $random\_hash; ?>--  
  
\--PHP-mixed-<?php echo $random\_hash; ?>  
Content-Type: <?php echo $filetype; ?>; name="<?php echo $filename; ?>"  
Content-Disposition: attachment; filename="<?php echo $filename; ?>"  
Content-Transfer-Encoding: base64  
  
<?php echo $attachment; ?>  
\--PHP-mixed-<?php echo $random\_hash; ?>--  
  
<?php $\_message = ob\_get\_clean(); ?>  
<?php  
$headers = "From: $from\\r\\nReply-To: $from";  
$headers .= "\\r\\n".'MIME-Version: 1.0';  
$headers .= "\\r\\n"."Content-Type: multipart/mixed; boundary=\\"PHP-mixed-".$random\_hash."\\"";  
$mail\_sent = mail( $to, $subject, $\_message, $headers );  
}  
?>  
<title>Attachment Email</title>  
  
<style type="text/css">  
</style>  
  
<script type="text/javascript">  
</script>  
</head>  
<body>  
<h1><a href="attachment\_email.php">Attachment Email</a></h1>  
<form enctype="multipart/form-data" action="attachment\_email.php" method="POST">  
<input type="hidden" name="MAX\_FILE\_SIZE" value="100000" />  
From:<br/>  
<input type="text" name="from" value="<?php echo $from; ?>"><br/>  
To:<br/>  
<input type="text" name="to" value="<?php echo $to; ?>"><br/>  
Subject:<br/>  
<input type="text" name="subject" value="<?php echo $subject; ?>"><br/>  
Message:<br/>  
<textarea name="message"><?php echo htmlentities($message); ?></textarea><br/>  
Attachment:<br/>  
<input type="file" name="uploadedfile"/><br />  
<input type="submit" name="submit" value="Send"/><br/>  
</form>  
<p>  
<?php echo isset($mail\_sent)?($mail\_sent? "Mail sent":"Mail failed"):''; ?>  
</p>  
</body>  
</html

  
  
Cada uno de estos scripts es una aplicación completa. Se presenta un formulario simple y se hace el envío de email.  
  
Algo que es importante tener en cuenta al enviar Unicode es usar base64 para codificar el mensaje.  
  
Y al enviar un adjunto es importante identificar el tipo de contenido, así como el nombre del archivo. Si no se coloca filename, además de name, en la descripción, el cliente email no reconocerá el adjunto (al menos no GMail).  
  
Recuerde que para que funcione el envío, PHP debe estar configurado para reconocer algún servicio email, usualmente en el servidor local.

_*Url archivado: [Enviando emails con PHP](https://akcdev.blogspot.com/2009/08/enviando-emails-con-php.html)*_
