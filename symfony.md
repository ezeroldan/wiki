# Symfony

## Basico

**Instalar** 
- `wget https://get.symfony.com/cli/installer -O - | bash`
- `symfony check:requirements`
 
## Generar

**Traditional web application:**
- `symfony new --full my_project`

**Microservice, console application or API:**
- `symfony new my_project`
- `symfony server:start`

## Service Container
- `php bin/console debug:container` Ver los servicios cargados en el container  
- `php bin/console debug:autowiring` Ver asociaciones al del service container

## Controllers
- `/** @Route("/blog") */` Definir modulo del controller
- `/** @Route("/{param}", name="") */` Definir la url
- Todos los controllers son services
- `class BlogController extends AbstractController` 
    - usa `ControllerTrait` que tiene todos los metodos utiles
    - Limita solo el llamado a algunos services
- `class BlogController extends Controller` 
    - Tiene uso de todo los services del container
    - No se recomienda
- `php bin/console debug:router` Ver Routes disponibles
- `throw new NotFoundHttpException('')` Pantalla de error

## Vistas (Twig)
- Los archivos se llaman `base.html.twig`
- Pueden ser css, xml, json, csv
- Se puede usar simple PHP para la vista tambien
- `{% %}` Acciones
- `{{ }}` Imprimir contenido
- `{# #}` Comentarios
- `/_error/404` Muestra la pantalla de error
- `templates/bundles/TwigBundle/Exception/error404.html.twing` Generar pantalla de error

## Doctrine
- ``

