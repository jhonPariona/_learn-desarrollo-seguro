# 🏆 learning Desarrollo Seguro de Apps

## Conceptos

_"reducir los riesgos a un nivel que resulte aceptable"_

🦜 **Ciclo de vida software**

![pasos del ciclo de vida del software](img/ciclo-vida-soft.png)

🦜 **Ciclo de vida de desarrollo seguro (SDLC Secure Software DEvelopment Life Cycle)**

- Si se detecta una vulnerabilidad durante los inicios del desarrollo es menos costoso.

![pasos del desarrollo seguro](img/ciclo-desarrollo-seguro.png)

🦜 **Vulnerabilidad**

Debilidad que puede ser explotada por una o más amenazas.

🦜 **Common Vulnerability Score System ([CVSS](https://www.welivesecurity.com/la-es/2014/08/04/vulnerabilidades-que-es-cvss-como-utilizarlo/)).**

sistema de puntaje(0 al 10) que permite estimar el impacto de una vulnerabilidad en base a 3 métricas.

![métricas base, temporales y de entorno ](https://www.welivesecurity.com/wp-content/uploads/2014/08/metricas.jpg)

## Entorno de práctica [WebGoat](https://github.com/WebGoat/WebGoat)

🦜 Tener instalado docker y docker-compose

```bash
$ curl https://raw.githubusercontent.com/WebGoat/WebGoat/master/docker-compose.yml |
docker-compose -f - up
```

🦜 Ingresar url `http://localhost:8080/WebGoat/login`

🦜 crearse una cuenta e ingresar

### Burp Suite

🦜 Ya viene instaldo dentro de Kali

[Crea un proxi](https://docs.google.com/presentation/d/1EF2_YMJFK8c0dIIST0ovcp32x9YRdETE/edit#slide=id.p1) para ver las cabeceras que se están enviando o recibiendo y activar el proxi en el navegador.

- si queremos capturar el trafico de una app con https debemos instalar un certificado; para ello burp suite nos da un certificado para ello entrar a la dirección de nuestro proxi e instalar el certificado.

## OWASP TEN

### SQL INJECTION

- Validación es mejor en el backend en el frontend podria ser por usabilidad pero no es seguro ya que el user puede desactivarlas.
- Usar ORMS ya que ya contienen soluciones frente a estos problemas.
- Usar Querys parametrizadas, ..
- siempre usar inputs validation nunca confiar en lo que el usuario nos podria enviar

### Broken Authentication

- usar frameworks como spring security
- Forzar la autenticación para todas las urls
- No es recomendable las preguntas seguras
- No admitir jwt sin firmar
- El secreto compartido de jwt debe de ser muy seguro sino se puede romper con jhon the ripper

### Sensitive Data Exposure

- Se debe de usar https
- no es recomendado MD5, mejor es sha256
- pbkdf2 es mejor para guardar contraseñas

### XML External Entities

- Usar mejor JSON(No tiene Entity)
- Si usamos XML y no usamos Entity desactivarlos.

### CSRF Cross site request forgery

- caad vez que se haga una peticion usar un nuevo token
- no usar token statico
- usar frameworks que ya implementas estas soluciones

### Broken access control

- No devolver informacion que no se va a pintar en el front

### Enumeración de usuarios

- autenticar para poder enumerar usuarios(proteger quien puede enumerar usuarios o el tiempo en q se hace esaas peticiones)

### Modificar accesos

- quien tiene autorizacion de hacer aciones en nuestros enpoints

### Fuzzing

- programas para dar entradas aleatorias y buscar fllos en nuestras app
- Dejar solo lo neesario para la producción
- Controlar accesos, numero de logins que pueden hacer los usuarios
