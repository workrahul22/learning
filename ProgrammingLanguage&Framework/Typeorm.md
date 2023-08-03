#### What is the active record pattern?

The active record pattern is an approach to accessing data in a database. A database table or view is wrapped into a class. Thus, an object instance is tied to a single row in the table. After creation of an object, a new row is added to the table upon save. Any object loaded gets its information from the database. when an object is updated, the corresponding row in the table is also updated. The wrapper class implements accessor methods or properties for each column in the table or view.

Using the active record approach, you define all your query methods inside a model itself, and you save, remove, and load objects using model methods.

Simply said, the active Record pattern is an approach to access your database within your models.

Example
```Javascript
    import { BaseEntity, Entity, PrimaryGeneratedColumn, Column} from "typeorm"

    @Entity()
    export class User extends BaseEntity {
        @PrimaryGeneratedColumn()
        id: number;

        @Column()
        firstName: string;

        @Column()
        lastName: string;

        @Column()
        isActive: boolean;
    }
```

All active-record entities must extend the BaseEntity class, which provides methods to work with the entity. Example of how to work with such entity

```Javascript
    const user = new User()
    user.firstName = "Timber"
    await user.save()

    await user.remove()

    const users = await User.find({ skip: 2, take: 5})
    const newUsers = await User.findBy({ isActive: true})
    const timber = await User.findOneBy({ firstName: "Timber"})
```
```Javascript
    import { BaseEntity, Entity, PrimaryGeneratedColumn, Column} from "typeorm"

    @Entity()
    export class User extends BaseEntity {
        @PrimaryGeneratedColumn()
        id: number

        @Column()
        firstName: string;

        @Column()
        lastName: string;

        @Column()
        isActive: boolean;

        static findByName(firstName: string, lastName: string) {
            return this.createQueryBuilder("user)
                .where("user.firstName = :firstName", {firstName})
                .andWhere("user.lastName = :lastName", {lastName})
                .getMany()
        }
    }

    const timber = await User.findByName("Timber", "Saw");
```

#### what is data mapper pattern?

A data mapper is a Data Access Layer that performs bidirectional transfer of data between a persistent data store (often a relational database) and an in-memory data representation (the domain layer). The goal of the pattern is to keep the in-memory representation and the persistent data store independent of each other and the data mapper itsefl. This is useful when one needs to model and enforce strict business on data in the domain layer that do not map neatly to the persistent data store. the layer is composed of one or more mappers (or Data Access Objects), performing the data transfer. Mapper implementation vary in scope. Generic mappers will handle many different domain entity types, dedicated mappers will handle one or a few.

Using the Data Mapper approach, you can define all your query methods in separate classes called repositories, and you save, remove, and load objects using repositories. In data mapper your entities are very dumb - they just define their properties and may have some dummy methods.

```Javascript
    import { Entity, PrimaryGeneratedColumn, Column} from "typeorm"

    @Entity()
    export class User {
        @PrimaryGeneratedColumn()
        id: number;

        @Column()
        firstName: string;

        @Column()
        lastName: string;

        @Column()
        isActive: boolean;
    }
```

Example how it works
```Javascript
    const userRepository = dataSource.getRepository(User)

    const user = new User()
    user.firstName = "Timber"
    await userRepository.save(user)

    await userRepository.remove(user)

    const user = await userRepository.find({ skip: 2, take: 5})
    const newUsers = await userRepository.findBy({isActive: true})
    const timber = await userRepository.findOneBy({
        firtsName: "Timber"
    })
```

In order to extend standard repository with custom methods, use custom repository pattern

#### which one should i choose
One thing we should always keep in mind with software developement is how we are going to maintain our application. The Data Mapper approach helps with maintainability, which is more effective in large apps. The Active Record approach helps keeping things simple which works well in smaller apps. And simplicity is always a key to better maintainability.

