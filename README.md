# Yii2 Basic Framework Remove the Web from url

> Main .htaccess

```
<IfModule mod_rewrite.c>
    Options +FollowSymlinks
    RewriteEngine On
</IfModule>

<IfModule mod_rewrite.c>
    RewriteCond %{REQUEST_URI} ^/.*
    RewriteRule ^(.*)$ web/$1 [L]

    RewriteCond %{REQUEST_URI} !^/web/
    RewriteCond %{REQUEST_FILENAME} !-f [OR]
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^.*$ web/index.php
</IfModule>
```

> /web/.htaccess

```
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . index.php
```

> config/web.php

```
'components' => [
  'request' => [
            'baseUrl' => '/aboutua',
        ....
  ]
  'urlManager' => [
            'enablePrettyUrl' => true,
            'showScriptName' => false,
            'rules' => [
            ],
        ],
   ...
]
```
