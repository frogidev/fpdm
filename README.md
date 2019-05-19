# Form filling
The FPDM class allows to fill out PDF forms, i.e. populate fields of a PDF file. It is **developed by Olivier Plathey**, author of the [FDPF Library](http://www.fpdf.org/), 
and has been released as [Skript 93](http://www.fpdf.org/en/script/script93.php).  
Initial adaptation for Composer was from [codeshell](https://github.com/codeshell/fpdm) and this was adapted for Laravel 5.
The follow adaptation for Composer was from [shihjay2] (https://github.com/shihjay2/fpdm) adapted for PHP 7.

I created this repository for the following reasons:
- Fix compatibility with Laravel 5.6 and foward

This repository only contains the separate php class written for form filling. 
If you are looking for a repository containing the main FPDF Library for Laravel 5, please head over to [github.comcaioladislau/FPDF](https://github.com/caioladislau/FPDF).

Once again, all credits to Olivier Plathey for providing an easy to use extension to his FPDF library! And to Michael Chen to bring it to composer!

# Version
Based on version 2.9 (2017-05-11) available from [fpdf.org/en/script/script93.php](http://www.fpdf.org/en/script/script93.php).


# Installation

Just run the following line:

```php
composer require frogidev/fpdm
```

# Original Info Page
## Information
Author: Olivier

License: FPDF

## Description
This script allows to merge data into a PDF form. Given a template PDF with text fields, it's
possible to inject values in two different ways:
- from a PHP array
- from an <abbr title="Forms Data Format">FDF</abbr> file

The resulting document is produced by the Output() method, which works the same as for FPDF.

Note: if your template PDF is not compatible with this script, you can process it with
[PDFtk](https://www.pdflabs.com/tools/pdftk-server/) this way:

`pdftk modele.pdf output modele2.pdf`

Then try again with modele2.pdf.

## Example
This example shows how to merge data from an array:

```php
<?php

/***************************
  Sample using a PHP array
****************************/

$fields = array(
    'name'    => 'My name',
    'address' => 'My address',
    'city'    => 'My city',
    'phone'   => 'My phone number'
);

$pdf = new FPDM('template.pdf');
$pdf->Load($fields, false); // second parameter: false if field values are in ISO-8859-1, true if UTF-8
$pdf->Merge();
$pdf->Output();
?>
```

View the result [here](http://www.fpdf.org/en/script/ex93.pdf).
