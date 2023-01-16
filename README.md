# Fundamental SQL Using FUNCTION and GROUP BY

You will understand the concept of using scalar functions and aggregate functions in string and numeric operations in SQL databases, Understand the concept of using GROUP BY in grouping data, Understand the concept of combining GROUP BY with aggregate functions, Understand the use of CASE Statements to structure decision making.

## Fungsi Scalar vs Fungsi Aggregate
Fungsi adalah metode yang digunakan untuk melakukan operasi data di database. Operasi ini bisa berupa kalkulasi numerik seperti sum, count, avg, etc; atau operasi non-numerik seperti string concatenations dan sub-strings. SQL Function dapat dibagi ke dalam 2 kategori, yaitufungsi scalar dan fungsi aggregate.

Bedanya fungsi skalar dan fungsi aggregate?

Fungsi skalar dalam SQL digunakan untuk mengembalikan nilai tunggal (single value) dari suatu nilai input yang diberikan, sedangkan fungsi agregat dalam SQL digunakan untuk melakukan perhitungan pada sekelompok nilai dan kemudian mengembalikan nilai tunggal. Nah, biar lebih mudah dipahami mari kita bahas dan praktekkan fungsi-fungsi dari kedua kategori ini.

## Fungsi Skalar Matematika
fungsi skalar pertama yang akan kita bahas adalah fungsi skalar untuk numerik value. Fungsi ini umumnya digunakan jika kita ingin melakukan operasi matematika di SQL secara cepat dan efektif. Di SQL sendiri ada banyak fungsi matematika, Untuk mengecek fungsi-fungsi apa saja yang bisa dilakukan di SQL, kita bisa membuka dokumentasi fungsi SQL di sini: https://www.postgresql.org/docs/9.5/functions-math.html, untuk postgresql database dan di sini: https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html, untuk mysql database. Nah, sebagai bahan praktik kamu agar lebih paham kamu bisa coba beberapa fungsi saja yang umumnya digunakan seperti ini

<img width="580" alt="image" src="https://user-images.githubusercontent.com/110078907/212645982-7fc794e0-b1bc-4684-b4a1-9d23e023ed19.png">

Contoh tabel dummy berisi nilai siswa semester 1 dan 2 di suatu sekolah. Berikut contoh penggunaan fungsi skalar dengan menggunakan tabel Students:

<img width="626" alt="image" src="https://user-images.githubusercontent.com/110078907/212646677-8f23b605-5484-412e-b2e5-c8999ffaf346.png">

## Fungsi Skalar Matematika - ABS()
Syntax:

    SELECT ABS(ColumnName)  
    FROM TableName;
    
    SELECT StudentID, FirstName, LastName, Semester1, Semester2, ABS(MarkGrowth) as MarkGrowth
    FROM students;
    
Output:

<img width="395" alt="image" src="https://user-images.githubusercontent.com/110078907/212647578-73a0dcfc-5639-412b-b22a-eaa92de151f7.png">

## Fungsi Skalar Matematika - CEILING()
Syntax:

    SELECT CEILING(ColumnName)  
    FROM TableName;
    
    SELECT StudentID, FirstName, LastName, CEILING(Semester1) as Semester1, CEILING(Semester2) as Semester2, MarkGrowth
    FROM students;
    
Output:

<img width="394" alt="image" src="https://user-images.githubusercontent.com/110078907/212648182-953465e4-cdfd-4f03-9d03-98c9aafb88fc.png">

## Fungsi Skalar Matematika - FLOOR()
Syntax:

    SELECT FLOOR(ColumnName)  
    FROM TableName;
    
    SELECT StudentID, FirstName, LastName, FLOOR(Semester1) as Semester1, FLOOR(Semester2) as Semester2, MarkGrowth
    FROM students;
    
Output:

<img width="394" alt="image" src="https://user-images.githubusercontent.com/110078907/212648719-3a5aca09-3252-47e9-a47c-3c1c8a055ca5.png">

## Fungsi Skalar Matematika - ROUND()
Syntax:

    SELECT ROUND(ColumnName)  
    FROM TableName; 
    
    SELECT StudentID, FirstName, LastName, ROUND(Semester1,1) as Semester1, ROUND(Semester2,0) as semester2, MarkGrowth
    FROM students;
    
Output:

<img width="395" alt="image" src="https://user-images.githubusercontent.com/110078907/212649433-75411ce5-4d89-4a13-96a1-d988cacd5b3a.png">

## Fungsi Skalar Matematika - SQRT()
Syntax:

    SELECT SQRT(ColumnName)  
    FROM TableName; 
    
    SELECT StudentID, FirstName, LastName, SQRT(Semester1) as Semester1, Semester2, MarkGrowth
    FROM students;
    
Output:

<img width="395" alt="image" src="https://user-images.githubusercontent.com/110078907/212649993-2ee64bbe-5762-47b4-9141-59288c5f0ee8.png">

## Fungsi MOD() & EXP()
Contoh penggunaan kedua fungsi dalam satu SELECT-Statement. fungsi MOD() untuk menghitung nilai sisa jika nilai Semester1 dibagi 2 dan fungsi EXP() untuk menghitung nilai eksponensial dari nilai MarkGrowth

Syntax:

    SELECT StudentID, FirstName, LastName, MOD(Semester1, 2) as Semester1, Semester2, EXP(MarkGrowth)
    FROM students;

Output:

<img width="407" alt="image" src="https://user-images.githubusercontent.com/110078907/212651238-cb268b72-1ee0-42a7-9517-0b6e1c9680b5.png">

## Fungsi Text



