# PHP Unit

- **TDD:** Test -> Code -> Refactor
- **Unit:** Testear unidad, funcionalidad puntual de una clase, se simulan ambientes
- **Integration:** Es como un Unit Test, pero se usa el ambiente real
- **Functional Test:** Testear desde el browser

## Instalar
```bash
composer require --dev phpunit/phpunit
```

## Configurar

### composer.json
```json
{
    "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/"
        }
    },
    "require-dev": {
        "phpunit/phpunit": "8.4.1",
    },
    "scripts": {
        "test": [
            "phpunit --testdox --colors=always --cache-result-file=.phpunit.result.cache"
        ],
        "test:unit": [
            "phpunit --testsuite unit --testdox --colors=always --cache-result-file=.phpunit.result.cache"
        ],
        "test:integration": [
            "phpunit --testsuite integration --testdox --colors=always --cache-result-file=.phpunit.result.cache"
        ],
        "test:coverage": [
            "phpunit --dump-xdebug-filter xdebug-filter.php && phpunit --prepend xdebug-filter.php --log-junit phpunit.report.xml --coverage-clover phpunit.coverage.xml --cache-result-file=.phpunit.result.cache"
        ]
    }
}
```

### phpunit.xml.dist
```xml
<?xml version="1.0" encoding="UTF-8"?>

<phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="http://schema.phpunit.de/4.1/phpunit.xsd"
         backupGlobals="false"
         colors="true"
         stopOnFailure="true"
         bootstrap="tests/bootstrap.php"
         convertWarningsToExceptions="false"
>
    <php>
        <ini name="error_reporting" value="-1" />
        <ini name="intl.default_locale" value="en" />
        <ini name="intl.error_level" value="0" />
        <ini name="memory_limit" value="-1" />
    </php>

    <testsuites>
        <testsuite name="unit">
            <directory>./src/*/*/Tests/Unit</directory>
            <directory>./tests/Unit</directory>
        </testsuite>
        <testsuite name="integration">
            <directory>./src/*/*/Tests/Integration</directory>
            <directory>./tests/Integration</directory>
        </testsuite>
    </testsuites>

</phpunit>

```

## Ejecutar
```bash
# Ejecutar todos los test
./vendor/bin/phpunit

# Ejecutar un solo test
./vendor/bin/phpunit --filter nombreDelTest

# Completo
./vendor/bin/phpunit --testdox --colors=always --cache-result-file=.phpunit.result.cache

```

### Desde Composer
```bash
composer test
composer test:unit
composer test:coverage
composer test:integration
```

## Tests Ejemplo

### TestCase
```php
<?php

namespace Test\Integration;

use Tests\TestCase;

class EjemploTest extends TestCase
{
    public function testEjemplo(): void
    {
        $this->assertTrue(false, 'Mensaje de error');
    }
}
```

### Test Hooks
- `setUp()` Ejecuta antes de cada test
- `tearDown()` Ejecuta despues de cada test
- `setUpBeforeClass()` Ejecuta por clase
- `tearDownAfterClass()` Ejecuta por clase
- `onNotSuccessfulTest ()`  Ejecuta en error

### Data Providers
```php
<?php

use Tests\TestCase;

class EjemploTest extends TestCase
{
    /**
     * @dataProvider getSpecificationTests
     */
    public function testEjemplo(string $param1, string $paramN): void
    {

    }

    public function getSpecificationTests(): array{
        return [ 'Nombre' => ['param1', 'paramN'] ];
    }

}
```

### Mocks
```php

/** @var PHPUnit_Framework_MockObject_MockObject */
private $mock;

public function setUp(){
    $this->mock = $this->createMock(Clase::class);
}

public function testEjemplo(): void
{
    $this->mock
        ->expects($this->once())
        ->method('funtionName')
        ->with() 
        ->willReturn();
}

```



