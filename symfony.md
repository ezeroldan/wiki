# Symfony

## Instalar
- `wget https://get.symfony.com/cli/installer -O - | bash`
- `symfony check:requirements`

## Generar nueva App
- `symfony new NOMBRE` Microservice, console application or API -> symfony/skeleton
- `symfony new --full NOMBRE` Traditional web application -> symfony/website-skeleton
- `symfony new NOMBRE --version=5.0` Indicar una version
- `symfony new NOMBRE --version=4.4 --full` Indicar una version

**Local Dev**
```bash
symfony console make:docker:database
docker-compose up -d
symfony console doctrine:migrations:migrate
symfony console doctrine:fixtures:load
symfony serve -d
yarn install
yarn encore dev
```

## Servidor local
- `symfony server:ca:install` Instalar certificado ssl
- `symfony server:start` Ejecutar servidor local
- `symfony server:start -d` Ejecutar en segundo plano.
- `symfony open:local` Abrir URL de ejecucion
- `symfony server:log` Ver log de peticiones http

## General
- `php bin/console` = `symfony console` Atajo para ejecutar la console en un proyecto
- `symfony composer` Ejecuta composer sin limite de momoria
- Entornos: `dev`, `prod`, `test`
- `.env.local` sobrescribe `.env`, se usa para trabajo local
- `dd()` y `dump()` Funciones de debug

## Bundles
- `symfony composer require logger` Logeo de errores
- `symfony composer require debug --dev` Pantallas de errores
- `symfony composer require profiler --dev` Tambien llamado `web_profiler` es la barra de Debug
- `symfony composer require maker-bundle --dev` Comandos para generar
- `symfony composer require annotations` Para usar anotaciones en las clases
- `symfony composer require doctrine-bundle` Doctrine ORM
- `symfony composer require easyadmin-bundle` Admin para symfony
- `symfony composer require security`
- `symfony composer require asset` Para manejo de assets
- `symfony composer require encore` Para manejo de webpack
- `symfony composer require sec-checker --dev` Validador de seguridad
- `symfony composer require orm-fixtures --dev` Data Fixtures (Seeding)
- `symfony composer require zenstruck/foundry --dev` Factory Entity
- `symfony composer require stof/doctrine-extensions-bundle` Plugins para Doctrine
- `symfony composer require messenger` Queue Async

## Service Container
- `symfony console debug:container [<name>]` Ver los servicios cargados en el container
- `symfony console debug:autowiring [<search>]` Ver asociaciones al del service container
    - `search` filtro
    
## Config
- `symfony console config:dump-reference [<name> [<path>]]` Ver ejemplo de archivo de config
    - `name` Bundle o alias. EJ: FrameworkBundle
    - `path` The configuration option path


## Controllers
- `synfony consule make:controller` Generar un controlador y template
- `/** @Route("/blog") */` Definir modulo del controller
- `/** @Route("/{param}", name="") */` Definir la url
- `public function(string $param)` Obtener el param de la url
- El orden de los metodos en el controller les da prioridad
- Todos los controllers son services
- `class DefaultController extends AbstractController` 
    - `$this->getDoctrine()` Retorna la instancia del ORM
    - `$this->json($data, $status)`
    - `$this->render('index.html.twig', [])` Retorna la vista
    - `$this->getUser()` Retorna el usuario
    - `throw $this->createNotFoundException();` 404 error
- `symfony console debug:router` Ver Routes disponibles
- `throw new NotFoundHttpException('')` Pantalla de error
- Se puede hacer typehint de una entidad con el id en la url como en laravel
- `$request->query->get('key')` Obtener param del query string

## Vistas (Twig)
- En todas las vistas hay una varible `app`
- `{% %}` Acciones
- `{{ }}` Imprimir contenido
- `{# #}` Comentarios
- `/_error/404` Muestra la pantalla de error
- `templates/bundles/TwigBundle/Exception/error404.html.twing` Generar pantalla de error

## Encore
- `yarn run encore dev --watch` Compilar cambios a demanada
- `yarn run encore dev-server` Ejecutar hot reload 

## Doctrine
- `symfony console doctrine:database:create` Genera la base de datos
- `symfony console make:entity NOMBRE_SINGULAR` Generar los archivos
- `symfony console doctrine:migration:diff` Gerar migraciones

- `$manager = $this->getDoctrine()->getManager();`
- `$manager->persist($entity);` Hacer el insert.
- `$manager->flush();` Para ejecutar el insert.


## Message
- `symfony console messenger:consume async -vv` Ejecutar el consumer
- `symfony open:local:rabbitmq` Ver colas

## Eventos
- `symfony console make:subscriber` Generar una clase para un evento: ClaseEventSubscriber

## Forms
- `symfony console make:form` Generar un formulario
- `'form' => $form->createView()`
- `{{ form(from) }}`
 
## FlashMesages
- `FlashBagInterface $bag`
- `$bag->add('name')`
- `{% for menssage in app.flashes('name')%}`

## Redis
- `redis-cli KEYS *` Ver todas los keys almancenados
- `redis-cli GET [NAME]` Ver el contenido en el key [NAME]

## Test
- `symfony console make:unit-test` Generar un Test
- `vendor/bin/simple-phpunit` Ejecutar el los Test

## phpStorm
- Symfony Plugin
- PHP Anotations
- PHP Toolbox

- PHP > Composer > Synchronize IDE Setting with composer.json
- PHP > Symfony > Enable Plugin for this Project
  - Translation: app/cache/dev/translation
  - App: app
  - Web: public


## Deploy
- `symfony console cache:clear` Borrar la cache para produccion


