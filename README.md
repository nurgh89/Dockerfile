# FinalTest_dibimbing

# NURHAYATI - FINAL TEST DATA WAREHOUSING

## tools
- Postgres SQL
- Python
- Collab 

## ETL- Essay 1
## Essay 1 - ETL
Sebagai seorang Data Engineer, kamu diberikan tugas untuk melakukan Web Scraping kumpulan berita dari suatu API.
API URL: https://berita-indo-api-next.vercel.app/api/cnn-news/teknologi
API Return Example:
{
"message": "Result of type teknologi news in CNN News",
"total": 100,
"data": [
{
"title": "Oppo Bocorkan Find N3, Ponsel Lipat Saingan Samsung Fold",
"link": "https://www.cnnindonesia.com/teknologi/20231106202324-206-1020734/oppo-bocorkan-find-n3-ponsel-lipat-saingan-samsung-fold",
"contentSnippet": "Penampakan Oppo Find N3, potensial saingan Samsung Galaxy Fold, dibocorkan ke publik. Intip spesifikasinya.",
"isoDate": "2023-11-06T14:29:47.000Z",
"image": {
"small": "https://akcdn.detik.net.id/visual/2023/11/06/oppo-find-n3-6_169.jpeg?w=360&q=90",
"large": "https://akcdn.detik.net.id/visual/2023/11/06/oppo-find-n3-6_169.jpeg?w=360&q=100"
}
}
]
}
Tasks:
1. Buatlah API request untuk mendapatkan data return API berupa JSON seperti contoh di atas dengan menggunakan Python
2. Ambil value dari key ‘data’ dalam JSON, dan transformasi menjadi sebuah DataFrame. Contoh:

3. Transformasi data kolom ‘isoDate’ menjadi tipe data datetime

## Essay 1 - ETL 2
4. Aggregasi data berdasarkan kolom ‘creator’, serta urutkan berdasarkan jumlah berita terbanyak. Contoh:

## Essay 1 - ETL 3
Notes:
Jumlah data dari contoh - contoh terlampir bisa berbeda dengan jumlah data yang kamu dapat
Gunakan Google Colab untuk mengerjakan assignment ini
Kamu bisa menggunakan library: requests, pandas

# Essy 2 - SQL - Data Warehousing with pyton
## Essay 2 - Data Warehouse

Use Case Description
We have raw data from a social media platform that includes information about users,
posts, and likes. We want to create a data warehouse to enable analytics on the
performance of posts over time.
Raw Data Tables
raw_users - Contains user profile information
user_id (PK)
user_name
country
raw_posts - Contains posts created by users
post_id (PK)
post_text
post_date
user_id (FK to raw_users)
raw_likes - Records which users liked which posts
like_id (PK)
user_id (FK to raw_users)
post_id (FK to raw_posts)
like_date

## Essay 2 - Data Warehouse 2
### Questions
1. Please create dimension tables dim_user , dim_post , and dim_date to store
normalized data from the raw tables
2. Populate the dimension tables by inserting data from the related raw tables
3. Create a fact table called fact_post_performance to store metrics like post views and
likes over time
4. Populate the fact table by joining and aggregating data from the raw tables
5. Please create a fact_daily_posts table to capture the number of posts per user per
day
6. Also populate the fact table by joining and aggregating data from the raw tables
Notes
We use PostgreSQL as the database
Create and populate raw tables:

### Create raw tables

CREATE TABLE raw_users (
user_id INT,
user_name VARCHAR(100),
country VARCHAR(50)
);
CREATE TABLE raw_posts (
post_id INT,
post_text VARCHAR(500),
post_date DATE,
user_id INT
);
CREATE TABLE raw_likes (
like_id INT,
user_id INT,
post_id INT,
like_date DATE
);

### Insert sample data
INSERT INTO raw_users
VALUES

## Essay 2 - Data Warehouse 3

(1, 'john_doe', 'Canada'),
(2, 'jane_smith', 'USA'),
(3, 'bob_johnson', 'UK');


INSERT INTO raw_posts
VALUES
(101, 'My first post!', '2020-01-01', 1),
(102, 'Having fun learning SQL', '2020-01-02', 2),
(103, 'Big data is cool', '2020-01-03', 1),
(104, 'Just joined this platform', '2020-01-04', 3),
(105, 'Whats everyone up to today?', '2020-01-05', 2),
(106, 'Data science is the future', '2020-01-06', 1),
(107, 'Practicing my SQL skills', '2020-01-07', 2),
(108, 'Hows the weather where you are?', '2020-01-08', 3),
(109, 'TGI Friday!', '2020-01-09', 1),
(110, 'Any big plans for the weekend?', '2020-01-10', 2);

INSERT INTO raw_likes
VALUES
(1001, 1, 101, '2020-01-01'),
(1002, 3, 101, '2020-01-02'),
(1003, 2, 102, '2020-01-03'),
(1004, 1, 103, '2020-01-04'),
(1005, 3, 104, '2020-01-05'),
(1006, 2, 104, '2020-01-06'),
(1007, 1, 105, '2020-01-07'),
(1008, 2, 106, '2020-01-08'),
(1009, 3, 107, '2020-01-09'),
(1010, 1, 108, '2020-01-10'),
(1011, 2, 109, '2020-01-11'),
(1012, 3, 110, '2020-01-12');



