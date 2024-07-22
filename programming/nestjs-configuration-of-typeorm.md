---
id: "1721191453"
aliases:
  - NestJS configuration of TypeORM
tags: [javascript, nestjs, typeORM, typescript, code, own-code]
---

# NestJS configuration of TypeORM

To separate and decouple the TypeORM configuration in NestJS, you can create a module dedicated exclusively to the TypeORM configuration and entities, and then import that module into other modules that need it. This approach makes it easier to change the underlying technology in the future without affecting the rest of the code.

example:

Create a module with all the database connection configurations using the forRoot method.

```typescript
@Module({
  imports: [
    ConfigModule.forRoot({ isGlobal: true }),
    TypeOrmModule.forRootAsync({
      useFactory: (configService: ConfigService) => ({
        type: "postgres",
        host: configService.get<string>("DB_HOST"),
        port: configService.get<number>("DB_PORT"),
        username: configService.get<string>("DB_USER"),
        password: configService.get<string>("DB_PASSWORD"),
        database: configService.get<string>("DB_NAME"),
        entities: [UserEntityTypeORM],
        synchronize: true,
        logging: true,
      }),
      inject: [ConfigService],
    }),
  ],
  providers: [TransactionProvider],
  exports: [TransactionProvider],
})
export class ConnectionTypeOrmModule {}
```

Configure all repositories to be used in the dependency injection of services.

```typescript
import { Module } from "@nestjs/common";
import { TypeOrmModule } from "@nestjs/typeorm";
import { ConnectionTypeOrmModule } from "./persistence/connection.module";
import { UserEntityTypeORM } from "./persistence/models/userEntity.typeorm";
import { ConfigModule, ConfigService } from "@nestjs/config";

@Module({
  imports: [
    ConnectionTypeOrmModule,
    TypeOrmModule.forFeature([UserEntityTypeORM]),
  ],
  exports: [TypeOrmModule],
})
export class TypeormModule {}
```

WARNING
is importan export the typeOrm or you could get an error like this
Error: Nest can't resolve dependencies of the UserAdapter (?). Please make sure that the argument "UserEntityTypeORMRepository" at index [0] is available in the InfrascructureModule context.

Now you can import the configuration and use it in your own module.

```typescript
@Module({
  imports: [TypeormModule],
  providers: [UserAdapter],

  exports: [UserAdapter],
})
export class InfrascructureModule {}
```

By following these steps, you can separate and decouple the TypeORM configuration in your NestJS application. This modular approach allows for easier changes to the underlying technology without impacting other parts of your code

## References

<https://docs.nestjs.com/techniques/database#subscribers>

<https://blog.entrostat.com/setting-up-a-database-module-in-nest-js/>
