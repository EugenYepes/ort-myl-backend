# 🧙 Backend Mitos y Leyendas

Este proyecto es un **backend Java** construido con **Hibernate**, **Firebase** y **AWS S3** para gestionar las cartas del juego **Mitos y Leyendas**. Permite almacenar, consultar y actualizar cartas, además de subir imágenes a un bucket en AWS S3, generando automáticamente su URL pública. La autenticación está integrada con **Firebase**, y la base de datos principal utilizada es **MySQL**.

Utilizado desde la app de android: https://github.com/EugenYepes/ort-myl-app

DTOs comunes en: https://github.com/EugenYepes/ort-myl-dtos

## 🚀 Tecnologías utilizadas

- Java 17+
- Hibernate (JPA)
- MySQL 8
- Firebase Admin SDK (autenticación)
- AWS SDK for Java (S3)
- Gradle Kotlin DSL
- Jetty / HttpServer embebido
- Jackson / Gson
- Lombok
- JUnit (para tests)

## 🧩 Funcionalidades principales

- CRUD completo de cartas (`Card`)
- Subida de imágenes a AWS S3
- Generación automática del `imageUrl` al subir la imagen
- Autenticación con tokens de Firebase
- Asociaciones entre entidades: cartas, formatos, razas, rarezas, colecciones, etc.
- Soporte para relaciones bidireccionales y herencia con Hibernate


## ☁️ Integración con AWS S3

Las imágenes de las cartas se almacenan en un bucket de S3. Al subir una imagen, se genera una URL accesible públicamente.

### Ejemplo de flujo:

1. El usuario hace un `POST /cards/{id}/image` con una imagen.
2. El backend sube la imagen a S3 bajo una clave como `cards/{id}.jpg`.
3. Se actualiza la entidad `Card` con el campo `imageUrl`.
4. La imagen se puede acceder desde:


## 🔐 Firebase Authentication

La autenticación se realiza mediante tokens de Firebase. Los endpoints protegidos requieren enviar el token en el encabezado `Authorization`.

```http
Authorization: Bearer <firebase_id_token>


aws.accessKey=TU_ACCESS_KEY
aws.secretKey=TU_SECRET_KEY
aws.region=us-east-1
aws.bucket.name=mitosyleyendas-cards

firebase.credentials.path=./serviceAccountKey.json

hibernate.connection.url=jdbc:mysql://localhost:3306/myldb
hibernate.connection.username=root
hibernate.connection.password=tu_password
```
Desarrollado por:
- Eugenio Yepes
- Malena Raiteri
- Damian Cozzani
- Sofia Laveihle
- Ignacio Garcia Godoy
