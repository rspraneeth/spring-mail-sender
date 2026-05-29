# Spring Mail Sender

Two small Spring Boot projects demonstrating how to send email with
`spring-boot-starter-mail` (JavaMailSender + SMTP).

## Modules

### `MailSender`
A minimal example exposing an `EmailSenderService` that sends a plain-text email
through a configured SMTP server. Good as a copy-paste starting point.

### `ContactMail`
A "Contact Us" web form built with Thymeleaf. Visitors fill in a subject and
message; the app emails it to the configured company address.

- `GET  /contact` — show the contact form
- `POST /contact/send/mail/user` — send the submitted message by email

## Tech stack

- Java 17, Spring Boot 3.2
- `spring-boot-starter-mail`
- `spring-boot-starter-web` + `spring-boot-starter-thymeleaf` (ContactMail)

## Configuration

Configure SMTP in `src/main/resources/application.properties`. For Gmail, use an
**app password**, never your real password, and prefer environment variables:

```properties
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=${MAIL_USERNAME}
spring.mail.password=${MAIL_APP_PASSWORD}
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

## Running

```bash
cd ContactMail   # or MailSender
./mvnw spring-boot:run
```

For `ContactMail`, open `http://localhost:8080/contact`.
