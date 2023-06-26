**HOTFIX**: Added hardcoded `platformOptions` to the "expected table" definition in
`/lib/Doctrine/Migrations/Metadata/Storage/TableMetadataStorage.php`


```php
private function getExpectedTable(): Table
    {
        // ...

        $schemaChangelog->addColumn(
            $this->configuration->getVersionColumnName(),
            'string',
            ['notnull' => true, 'length' => $this->configuration->getVersionColumnLength()]
        );
        
        // ...  
    }
```

Added hardcoded options for MySQL 8.0 with `utf8mb4`

```php
private function getExpectedTable(): Table
    {
        // ...

        $schemaChangelog->addColumn(
            $this->configuration->getVersionColumnName(),
            'string',
            ['notnull' => true, 'length' => $this->configuration->getVersionColumnLength(),
            'platformOptions' => ['charset' => 'utf8mb4', 'collation' => 'utf8mb4_general_ci']     
            ]
        );
        
        // ...  
    }
```

# Doctrine Migrations

[![Build Status](https://github.com/doctrine/migrations/workflows/Continuous%20Integration/badge.svg)](https://github.com/doctrine/migrations/actions)
[![Code Coverage](https://codecov.io/gh/doctrine/migrations/branch/3.1.x/graph/badge.svg)](https://codecov.io/gh/doctrine/migrations/branch/3.1.x)
[![Packagist Downloads](https://img.shields.io/packagist/dm/doctrine/migrations)](https://packagist.org/packages/doctrine/migrations)
[![Packagist Version](https://img.shields.io/packagist/v/doctrine/migrations)](https://packagist.org/packages/doctrine/migrations)
[![GitHub license](https://img.shields.io/github/license/doctrine/migrations)](LICENSE)

## Documentation

All available documentation can be found [here](https://www.doctrine-project.org/projects/migrations.html).
