---
sidebar_position: 2
---

# Module
## Modulo Aplicacion Principal


 En este parte del código se encarga de la configuración y organización de los componentes de la aplicación, como los **Controladores, Servicios y Proveedores** en `src/app.module.ts`

```jsx title="src/app.module.ts"
// Importaciones nesesarias
import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { BibliotecaModule } from './biblioteca/biblioteca.module';
import { ActivoModule } from './activo/activo.module';

@Module({   //Creamos un decorador para configurar el modulo
  imports: [MongooseModule.forRoot(   //Configuración del módulo MongooseModule
    'mongodb://fundation:freefundation221@10.10.214.219:27017/',    //URL de conexión a la base de datos MongoDB, se usa la base de datos del servidor
      {
        dbName:'htm-pdf'    //Nombre de la Base de Datos
      }),
  BibliotecaModule, 
  ActivoModule],  //importación del modulo
  controllers: [],   //Controlador que es utilizado en el modulo
  providers: [],    //Proveedores de servicios que se utiliza en el modulo
})
export class AppModule {}   //Iniciamos la aplicación
```
### Explicacion Detallada
**import { Module } from '@nestjs/common';**: Importa la clase **Module** del paquete **@nestjs/common**. Esta clase se utiliza para definir un módulo en NestJS.

**import { MongooseModule } from '@nestjs/mongoose';**: Importa el módulo **MongooseModule** del paquete **@nestjs/mongoose**. Este módulo proporciona integración con MongoDB utilizando Mongoose como ODM **(Object-Document Mapper)**.

**import { BibliotecaModule } from './biblioteca/biblioteca.module';**: Importa el módulo **BibliotecaModule** desde el archivo **biblioteca.module.ts**. Este módulo contiene los controladores, servicios y otros componentes relacionados con la gestión de bibliotecas.

**import { ActivoModule } from './activo/activo.module';**: Importa el módulo **ActivoModule** desde el archivo **activo.module.ts**. Este módulo contiene los controladores, servicios y otros componentes relacionados con la gestión de activos.

**@Module({ ... })**: Anotación de decorador que define una clase como un módulo de NestJS. Dentro de las llaves se configuran los metadatos del módulo.

**MongooseModule.forRoot(...)** : Configuración del módulo **MongooseModule** utilizando el método **forRoot()**. Aquí se especifica la URL de conexión a la base de datos **MongoDB** y se proporcionan opciones adicionales, como el nombre de la base de datos.

**BibliotecaModule, ActivoModule**: Se agregan los módulos **BibliotecaModule** y **ActivoModule** al arreglo de importaciones. Esto indica que estos módulos son dependencias de **AppModule** y deben ser inicializados y utilizados por la aplicación.

**controllers: [], providers: []**: Arreglos vacíos para los controladores y proveedores del módulo principal. Aquí se pueden agregar controladores y proveedores personalizados si es necesario.