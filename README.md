# Mengenal apa itu SASS

> SASS singkatan dari Syntactically Awesome Stylesheet. Merupakan sebuah CSS pre-processor. Kita bisa akses disini https://sass-lang.com/

## Cara Install SASS

Ada beberapa cara yang bisa digunakan untuk menginstall SASS.
- Ekstension VS Code
- Terminal

### Visual Studio Code

Cara termudah adalah dengan menggunakan ekstension visual studio code. Caranya:
- Masuk ke menu pluggin
- Insall `Live Sass Compile`

### Command Line

Gunakan sintaks seperti berikut:

```shell
sass source/stylesheets/index.scss build/stylesheets/index.css
```

## Sintaks Dasar

Ini adalah sintaks dasar dari penggunaan SASS atau CSS pre-processor

```scss
$primary-color: red;
$text-color: green;

body {
    background: $primary-color;
    h1 {
        color: $text-color;
    }
}
```

Maka hasil ketika diubah ke CSS adalah
```css
body {
    background: red;
}
body h1 {
    color: green;
}
```

## Sass Variable

Ada beberapa aturan penulisan variable:
- Variabel $primary-color dengan $primary_color ini akan tetap terbaca
- Variabel diluar element akan terbaca secara global
- Variabel yang kita simpan di dalam sebuah element, tidak akan terbaca secara global namun terbaca secara nesting. Tetapi, jika ingin terbaca maka tambahkan `!global` dibelakan value

```scss
$primary-color: red;
$text-color: green;

body {
    background: $primary-color;
    $text-color: orange;
    h1 {
        color: $text-color; // orange
    }
}
p {
    color: $text-color; // green
}
```

### Sass like Object Javascript

> Disini kita akan membuat sebuah elemen `alert` tergantung apa yang tampil.

```scss
$alert: (
    'danger': red,
    'success': green,
    'warning': orange
);

h1 {
    color: map-get($alert, 'success');
}
```

## Mixin

> Kumpulan style yang dapat kita gunakan berulang-ulang. Seperti halnya function yang bisa kita pakai berulang.

```scss
@mixin inline-list {
    margin: 0;
    padding: 0;
    list-style: none;
    li {
        display: inline-block;
    }
}

.header ul {
    @include inline-list();
    li {
        background-color: black
        padding: 0.5em;
        a {
            color: white;
        }
    }
}

.footer ul {
    @include inline-list();
    li {
        padding: 0.4em;
        background-color: salmon;
    } a {
        color: white;
        text-decoration: none;
    }
}
```

# Daftar Pustaka

> Sumber belajar: https://www.w3schools.com/sass/default.php