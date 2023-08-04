---
sidebar_position: 1
---

# Main
## Inicio de la Aplicación

Aquí configuraremos el **Inicio de la Aplicación**  en `src/main.ts` 

```jsx title="src/main.ts"
import { NestFactory } from '@nestjs/core';   
import { AppModule } from './app.module';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';   
//Importación de las dependencias necesarias 

async function bootstrap() {
  const app = await NestFactory.create(AppModule,{cors:true});    //Creación de la aplicación
  const config = new DocumentBuilder() //Configuración de la documentación Swagger
    .setTitle('API Convert')    //Establecemos el titulo
    .setDescription('Convert HTML to PDF')  //La descripción
    .setVersion('1.0')  //La versión
    .addTag('biblioteca')  //La etiqueta de la API biblioteca
    .addTag('activo')   //La etiqueta de la API activo
    .build();   //Construcción de la configuración del documento Swagger

  const document = SwaggerModule.createDocument(app, config); //Creamos la documentación de Swagger
  SwaggerModule.setup('api', app, document);  //Configuración del Swagger utilizando el método estático

  await app.listen(3000); //Iniciamos la aplicación en el puerto 3000
}
bootstrap(); //Inicia la aplicación
```

### Explicacion Detallada
**import { NestFactory } from '@nestjs/core';**: Importa la función **NestFactory** del paquete **@nestjs/core**, que se utiliza para crear una instancia de la aplicación NestJS.

**import { AppModule } from './app.module';**: Importa la clase **AppModule** del archivo **app.module.ts**. **AppModule** es el módulo raíz de la aplicación NestJS y define la estructura y configuración general de la aplicación.

**import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';**: Importa las clases **DocumentBuilder y SwaggerModule** del paquete **@nestjs/swagger**. Estas clases se utilizan para generar y configurar la documentación de la API utilizando Swagger.

**async function bootstrap() { ... }**: Define una función asincrónica llamada **bootstrap**, que es el punto de entrada principal de la aplicación.

**const app = await NestFactory.create(AppModule,{cors:true});**: Crea una instancia de la aplicación NestJS utilizando la clase **NestFactory.create**. Se pasa **AppModule** como argumento para indicar qué módulo se utilizará como módulo raíz de la aplicación. **{cors:true}** habilita la configuración de CORS **(Cross-Origin Resource Sharing)** para permitir solicitudes desde diferentes dominios.

**const config = new DocumentBuilder() ... .build();**: Crea una instancia de **DocumentBuilder** para construir la configuración de la documentación de Swagger. Se establecen detalles como el título, la descripción y la versión de la API, y se agregan etiquetas para categorizar los endpoints. El método **build()** finaliza la construcción y devuelve la configuración.

**const document = SwaggerModule.createDocument(app, config);**: Crea un documento **Swagger** utilizando la función **createDocument** de **SwaggerModule**. Se pasa la instancia de la aplicación app y la configuración de Swagger config para generar el documento.

**SwaggerModule.setup('api', app, document);**: Configura la ruta y el punto final donde se servirá la documentación de Swagger. En este caso, se utiliza la ruta **/api** y se asocia al documento Swagger generado.

**await app.listen(3000);**: Inicia el servidor de la aplicación NestJS en el puerto **3000**. La aplicación comenzará a escuchar las solicitudes entrantes en ese puerto.

**bootstrap();**: Llama a la función bootstrap para iniciar la aplicación.