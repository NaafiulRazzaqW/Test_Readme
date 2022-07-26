#### M Naafiul Razzaq W
#### Absen: 12 Kelas: XII RPL 2
##### Modul 1

###### 1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing
```
composer create-project laravel/laravel penjualan

```
##### Modul 2
###### Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam
modul ini

Langkah Pertama: 

```
php artisan make:migration create_kategori_table
```

Langkah Kedua:
Ubah isi dalam **public function up()** seperti dibawah

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};

```

Lalu selanjutnya jalankan kode dibawah pada terminal

```
php artisan migrate
```

Langkah Selanjutnya membuat model kategori

```
php artisan make:model Kategori
```

lalu buatlah seeder untuk mengisi tabel dengan column,jalankan kode dibawah pada terminal:

```
php artisan make:seeder kategoriTableSeeder
```

setelah itu isi **public function run()** seperti dibawah

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert (array(

            [
                'nama' => 'Perlengkapan Sekolah',
            ],
            [
                'nama' => 'Komputer',
            ],
            [
                'nama' => 'Sabun',
            ],
            [
                'nama' => 'Accesories',
            ],
            [
                'nama' => 'ATK',
            ],


        ));
    }
}

```

lalu buka seeder file bernama **DatabaseSeeder** lalu isi **public function run()** seperti dibawah:

```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        
        $this->call(kategoriTableSeeder::class);
    }
}

```

lalu jalankan kode berikut pada terminal:
```
php artisan db:seed
```

setelah itu cek pada database apakah kolom sudah terisi atau belum
