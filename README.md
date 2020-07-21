### Doctrine entity to manipulate users

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
                dir: '%kernel.project_dir%/vendor/colvin/doctrine/src/Doctrine/Entity'
                prefix: 'Colvin\Doctrine\Entity'
                alias: Colvin
```