# Symfony

## Basico
- Symfony Flex es un pluging de composer para manejar las dependencias

**Instalar** 
- `wget https://get.symfony.com/cli/installer -O - | bash`
- `symfony check:requirements`

- `alias console="php bin/console"`
 
## Generar nueva App
- `symfony new --full my_project` Traditional web application
- `symfony new my_project` Microservice, console application or API
- `symfony server:start` Ejecutar servidor local

## Service Container
- `php bin/console debug:container` Ver los servicios cargados en el container  
- `php bin/console debug:autowiring` Ver asociaciones al del service container
- Simpre usar la inyeccion de dependencia con la interfaces

## Controllers
- `/** @Route("/blog") */` Definir modulo del controller
- `/** @Route("/{param}", name="") */` Definir la url
- El orden de los metodos en el controller les da prioridad
- Todos los controllers son services
- `class DefaultController extends AbstractController` 
    - `$this->getDoctrine()` Retorna la instancia del ORM
    - `$this->json($data, $status)`
    - `$this->render('index.html.twig', [])` Retorna la vista
    - `$this->getUser()` Retorna el usuario
- `php bin/console debug:router` Ver Routes disponibles
- `throw new NotFoundHttpException('')` Pantalla de error
- Se puede hacer typehint de una entidad con el id en la url como en laravel

## Vistas (Twig)
- Los archivos se llaman `base.html.twig`
- Pueden ser css, xml, json, csv
- Se puede usar simple PHP para la vista tambien
- `{% %}` Acciones
- `{{ }}` Imprimir contenido
- `{# #}` Comentarios
- `/_error/404` Muestra la pantalla de error
- `templates/bundles/TwigBundle/Exception/error404.html.twing` Generar pantalla de error
- `{{ path('NAME') }}` Imprimir URL

## Doctrine
- `php bin/console doctrine:database:create` Genera la base de datos
- `php bin/console maek:entity NOMBRE_SINGULAR` Generar `src/Entity/NOMBRE_SINGULAR.php` y `src/Repository/NOMBRE_SINGULARReposity.php`
- DDL: Data Definition Language (CREATE, ALRTER, DROP)
- `php bin/console doctrine:migration:diff` Gerar migraciones
- Repository es un patron de disenio, donde en una clase van todas las consultas de una entidad
- fixture es para generar data falsa, se guarda en src/DataFixture `composer require --dev orm-fixtures`
- `$manager->persist($entity);` Hacer el insert. `$manager->flush();` Para ejecutar el insert.
- 