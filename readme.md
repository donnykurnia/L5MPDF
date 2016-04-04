## mPDF Wrapper for Laravel 5
In development.
### License
[![License](https://poser.pugx.org/donnykurnia/l5mpdf/license)](https://packagist.org/packages/donnykurnia/l5mpdf)
[![Latest Stable Version](https://poser.pugx.org/donnykurnia/l5mpdf/v/stable)](https://packagist.org/packages/donnykurnia/l5mpdf)

## Instalation
Add:
```
"donnykurnia/l5mpdf": "dev-master@dev",
```
To your `composer.json`

or Run:
```
composer require donnykurnia/l5mpdf
```

Then add:
```php
'Servit\Mpdf\ServiceProvider',
```
To the `providers` array on your `config/app.php`

And

```php
'PDF'     => 'Servit\Mpdf\Facades\Pdf',
```
To the `aliases` array on yout `config/app.php` in order to enable the PDF facade

## Usage

```php
$router->get('/pdf/view', function() {
    $pdf = \App::make('mpdf.wrapper', [
        'mode'   => 'id+aCJK',
        'format' => 'A4-L',
    ]);
    $pdf->WriteHTML('<h1>Page 1</h1>');
    $pdf->AddPage('P');
    $pdf->WriteHTML('<h1>Page 2</h1>');
    $pdf->stream();
});
```

### Force download
```php
$router->get('/pdf/download', function() {
    $html = view('pdfs.example')->render();

    return PDF::load($html)->download();
});
```

### Output to a file
```php
$router->get('/pdf/output', function() {
    $html = view('pdfs.example')->render();

    PDF::load($html)
        ->filename('/tmp/example1.pdf')
        ->output();

    return 'PDF saved';
});
```
This mPDF Wrapper for Laravel5 is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)

## Default config

These default config can be overridden when creating the `mpdf.wrapper`.
```php
[
    'mode'                  => '',
    'format'                => 'A4',
    'defaultFontSize'       => '',
    'defaultFont'           => '',
    'marginLeft'            => 10,
    'marginRight'           => 10,
    'marginTop'             => 10,
    'marginBottom'          => 10,
    'marginHeader'          => 10,
    'marginFooter'          => 5,
    'orientation'           => 'P',
]
```
