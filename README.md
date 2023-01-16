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

Sama seperti fungsi skalar matematika, kita juga bisa mengecek fungsi - fungsi skalar text di dokumentasi postgresql: https://www.postgresql.org/docs/9.1/functions-string.html; dan dokumentasi mysql: https://dev.mysql.com/doc/refman/8.0/en/string-functions.html. 

Untuk bahan praktik, kita akan mencoba beberapa fungsi saja yang sering digunakan.
<img width="517" alt="image" src="https://user-images.githubusercontent.com/110078907/212652701-f0d59c24-3ac2-42f2-b179-2d39a242e17a.png">

## Fungsi Text - CONCAT()
Syntax:

        SELECT CONCAT(ColumnName1, ColumnName2, ColumnNameN)  
        FROM TableName; 
        
        select studentid, concat(firstname, lastname) as name, semester1, semester2, markgrowth
        from students;
        
Output:

<img width="317" alt="image" src="https://user-images.githubusercontent.com/110078907/212653228-d8b104d4-3b33-49c7-8788-9484ae3cbaa7.png">

## Fungsi Text - SUBSTRING_INDEX()
Syntax: 

        SELECT SUBSTRING_INDEX(column, delimiter, index to return)  
        FROM TableName; 
        
        select studentid, substring_index(email,'@',1) as name
        from students;
        
 Output:
 
 <img width="144" alt="image" src="https://user-images.githubusercontent.com/110078907/212653564-42637989-9211-4511-b142-dba7d7993e5c.png">

## Fungsi Text - SUBSTR()
Syntax:

        SELECT SUBSTR(columnName, Start Index, Number of string to be extract)
        FROM TableName;
        
        select studentid, substr(firstname, 2, 3) as initial 
        from students;

Output:

<img width="114" alt="image" src="https://user-images.githubusercontent.com/110078907/212653971-71657d64-8b46-45ca-8c05-29b2238a1958.png">

## Fungsi Text - LENGTH()
Syntax:

        SELECT LENGTH(ColumnName)
        FROM TableName; 
        
        select StudentID, FirstName, length(firstname) as Total_Char
        from students;
        
Output:

<img width="189" alt="image" src="https://user-images.githubusercontent.com/110078907/212655303-268a02ab-0761-411a-9c25-c97e0ccc9061.png">

## Fungsi Text - REPLACE()
Syntax:

        SELECT REPLACE(ColumnName, Character/String to be change, New String/Character)
        FROM TableName; 
        
        select StudentID, Email, REPLACE(email,'yahoo','gmail') as New_Email
        from students;
        
Output:

<img width="317" alt="image" src="https://user-images.githubusercontent.com/110078907/212655605-1f503fe1-82f4-4038-839e-f08e4957531c.png">

## Fungsi UPPER() & LOWER()
UPPER() untuk mengubah kolom FirstName menjadi seluruhnya kapital dan LOWER() untuk mengubah kolom LastName menjadi seluruhnya non-kapital.

Syntax:

        select StudentID, upper(firstname) as FirstName , lower(lastname) as LastName 
        from students;

Output:

<img width="176" alt="image" src="https://user-images.githubusercontent.com/110078907/212723751-5f70413e-4ac6-4b05-9280-ddb8562ddd6e.png">

## Fungsi Aggregate
Fungsi aggregate digunakan untuk melakukan perhitungan pada sekelompok nilai. penggunaan fungsi aggregate di SQL yang umum digunakan

<img width="433" alt="image" src="https://user-images.githubusercontent.com/110078907/212724276-c32c477b-805b-4fa9-ad94-04c83bb57949.png">

## Fungsi Aggregate - SUM()
Syntax:

    SELECT SUM(ColumnName)  
    FROM TableName;
    
    select sum(semester1) as Total_1, sum(semester2) as Total_2
    from students;
    
Output: 

<img width="105" alt="image" src="https://user-images.githubusercontent.com/110078907/212724661-70680563-9f34-4318-8ee3-42f45c82b722.png">

## Fungsi Aggregate - COUNT()
Syntax:

    SELECT COUNT(ColumnName)  
    FROM TableName;
    
    select count(firstname) as Total_Student
    from students;
    
Output:

<img width="73" alt="image" src="https://user-images.githubusercontent.com/110078907/212725153-87f5e11b-0716-4cd6-b448-d6056660297e.png">

## Fungsi Aggregate - AVG()
Syntax: 

    SELECT AVG(ColumnName)  
    FROM TableName;
    
    select avg(semester1) as AVG_1, avg(semester2) as AVG_2
    from students;
    
Output:

<img width="122" alt="image" src="https://user-images.githubusercontent.com/110078907/212725467-42bc28a2-c099-43c5-a2da-5182959c1ec6.png">

## Fungsi MIN() & MAX()
contoh menggunakan fungsi MIN() dan MAX() untuk menghitung nilai dari kolom Semester1 dan Semester2.

Syntax:

    select min(semester1) as Min1, max(semester1) as Max1, min(semester2) as Min2, max(semester2) as Max2
    from students;
    
Output:     

<img width="137" alt="image" src="https://user-images.githubusercontent.com/110078907/212725963-ef908448-180e-4b3f-9b59-9f557c1f5670.png">

## Pengenalan GROUP BY
Untuk mengelompokkan data di SQL kita menggunakan GROUP BY Statement. GROUP BY statement akan mengelompokkan data yang bernilai sama ke dalam satu group, dan dengan menggunakan fungsi aggregate seperti (COUNT, MAX, MIN, SUM, AVG) kita bisa melakukan agregasi untuk untuk setiap group atau kelompok yang terbentuk.

Syntax:

    SELECT column_name(s)
    FROM table_name
    WHERE condition
    GROUP BY column_name(s)
    ORDER BY column_name(s)
    
Hal penting yang perlu diperhatikan adalah: 

1. GROUP BY digunakan dengan SELECT, artinya kolom yang digunakan di GROUP BY statement, juga perlu ditempatkan di SELECT.

2. GROUP BY ditempatkan setelah WHERE, tetapi jika tidak menggunakan WHERE maka langsung ditempatkan setelah FROM. 

3. Jika menggunakan ORDER BY, maka GROUP BY ditempatkan sebelum ORDER BY. 

Group by bisa dilakukan dengan single column ataupun multiple column. Seperti ini contohnya:

* Group by Single Column, data dikelompokkan menggunakan kriteria dari satu kolom saja, misalnya mengelompokkan data berdasarkan provinsi saja. 

* Group by Multiple Column, data dikelompokkan menggunakan kriteria dari dua kolom atau lebih, misalnya mengelompokkan data berdasarkan province dan brand.

## Group by Single Column
Fungsi Group by Single Column memastikan data dapat dikelompokkan menggunakan kriteria dari satu kolom saja, misalnya mengelompokkan data berdasarkan provinsi saja.

Syntax: 

    select province,
    count(distinct order_id) as total_order,
    sum(item_price) as total_price
    from sales_retail_2019
    group by province;
    
Output:

<img width="209" alt="image" src="https://user-images.githubusercontent.com/110078907/212727870-66a92412-aeaa-4766-91a9-359177b59169.png">

