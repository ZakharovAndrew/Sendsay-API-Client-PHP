# Sendsay-API-Client-PHP
A simple Sendsay API Client for PHP.

# Пример

Не смотря на то, есть документация, тех поддержка может приводить не верные примеры. 

```php
include 'ApiClient.php';

try {
    echo '<pre>';
    // создаем клиент
    $ApiClient = new ApiClient('ЛОГИН', 'ПАРОЛЬ');
    
    
    // Создание группы
    var_dump($ApiClient->createGroup('list0004', 'list0004'));
    
    // добавить подписчика
    $params = array(
	    array(
	      "anketa.base.firstName",
        "set",
        "Иван"
	    ),
	    array(
	      "anketa.base.lastName",
        "set",
        "Иванов"
	    )
    );
    for ($i=0; $i<20; $i++) {
	    var_dump($ApiClient->addEmail('list0004', 'example'.$i.'@example.com', $params));
    }
    
    echo "Информация по группе \n";
    var_dump($ApiClient->getGroup('list0004'));
    
    // Удалить группу
    var_dump($ApiClient->deleteGroup('list0004'));
    
    // Получение статистики
    var_dump($ApiClient->getStatistics('4'));
    
    // Состояние асинхронного запроса
    var_dump($ApiClient->getTrack('10'));
    
    // Прочитать группу (* - все группы)
    var_dump($ApiClient->getGroup('*'));
    
    
    echo '</pre>';
} catch (Exception $e) {
    print $e->getLine() . ' : ' . $e->getMessage() . PHP_EOL;
    exit();
}
```
