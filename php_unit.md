* Минимальный тест
```php
<?php
use PHPUnit\Framework\TestCase;

final class ExampleTest extends TestCase
{
    public function testOneIsOne()
    {
        $this->assertEquals(
            "1",
            "1"
        );
    }
}
```
* Настройка xml
```xml
<phpunit bootstrap="./bootstrap.php">
    <testsuites>
        <testsuite name="example">
            <file>test_test.php</file>
        </testsuite>
    </testsuites>
</phpunit>
```
* Запуск одного конкретного теста
```cmd
./phpunit --filter testOneIsOne
```
