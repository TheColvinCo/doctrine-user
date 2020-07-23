### Doctrine entity to manipulate users on Symfony

Install the package:

`composer req colvin/doctrine-user`

Define the mapping in `doctrine.yaml`:

```
doctrine:
    orm:
        mappings:
            Colvin:
                is_bundle: false
                type: annotation
                dir: '%kernel.project_dir%/vendor/colvin/doctrine-user/src/Doctrine/Entity'
                prefix: 'Colvin\Doctrine\Entity'
                alias: Colvin
```

Configure the `User` class as a security provider in `security.yaml`:

```
security:
    encoders:
        Colvin\Doctrine\Entity\User:
            algorithm: argon2i
    providers:
        app_user_provider:
            entity:
                class: Colvin\Doctrine\Entity\User
                property: username
```

Register the `UserRepository` as a service in `services.yaml`:

```
services:
    Colvin\Doctrine\Repository\UserRepository:
        tags: ['doctrine.repository_service']
```