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

Use the User class as a security provider:

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