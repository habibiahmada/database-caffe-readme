
# Struktur Basis Data Kafe
![Untitled Workspace](https://github.com/user-attachments/assets/ac925bad-7590-4fb2-91d5-75cfbf821328)

Basis data kafe ini memiliki beberapa tabel utama yang saling berhubungan. Setiap tabel memiliki Primary Key (PK) dan beberapa tabel memiliki Foreign Key (FK) yang mengacu ke tabel lain. Berikut adalah penjelasan detailnya.

## Tabel dan Atribut

### Pelanggan (Customer)
- **CustomerId** (PK): ID unik untuk setiap pelanggan.
- **FirstName**: Nama depan pelanggan.
- **LastName**: Nama belakang pelanggan.
- **Email**: Alamat email pelanggan.
- **Phone**: Nomor telepon pelanggan.

### Pegawai (Employee)
- **EmployeeId** (PK): ID unik untuk setiap pegawai.
- **FirstName**: Nama depan pegawai.
- **LastName**: Nama belakang pegawai.
- **Email**: Alamat email pegawai.
- **Phone**: Nomor telepon pegawai.
- **Title**: Jabatan pegawai.

### Kategori (Category)
- **CategoryId** (PK): ID unik untuk setiap kategori.
- **CategoryName**: Nama kategori produk.

### Produk (Product)
- **ProductId** (PK): ID unik untuk setiap produk.
- **ProductName**: Nama produk.
- **Price**: Harga produk.
- **CategoryId** (FK): ID kategori produk, mengacu ke tabel Kategori.

### Pembayaran (Payment)
- **PaymentId** (PK): ID unik untuk setiap pembayaran.
- **PaymentType**: Jenis pembayaran (misalnya, tunai, kartu kredit).
- **Amount**: Jumlah pembayaran.
- **PaymentDate**: Tanggal pembayaran.

### Pesanan (Order)
- **OrderId** (PK): ID unik untuk setiap pesanan.
- **OrderDate**: Tanggal pesanan.
- **CustomerId** (FK): ID pelanggan yang melakukan pesanan, mengacu ke tabel Pelanggan.
- **EmployeeId** (FK): ID pegawai yang menangani pesanan, mengacu ke tabel Pegawai.
- **PaymentId** (FK): ID pembayaran yang digunakan, mengacu ke tabel Pembayaran.

### Detail Pesanan (OrderDetail)
- **OrderDetailId** (PK): ID unik untuk setiap detail pesanan.
- **OrderId** (FK): ID pesanan, mengacu ke tabel Pesanan.
- **ProductId** (FK): ID produk yang dipesan, mengacu ke tabel Produk.
- **Quantity**: Jumlah produk yang dipesan.
- **Subtotal**: Total harga untuk jumlah produk yang dipesan.

## Relasi Antar Tabel

### Pelanggan ke Pesanan (Customer to Order) (1:M)
- **CustomerId** di tabel **Order** sebagai **FK** mengacu ke **CustomerId** di tabel **Customer** sebagai **PK**.
- Satu pelanggan dapat memiliki banyak pesanan, tapi satu pesanan hanya dapat dimiliki oleh satu pelanggan.

### Pegawai ke Pesanan (Employee to Order) (1:M)
- **EmployeeId** di tabel **Order** sebagai **FK** mengacu ke **EmployeeId** di tabel **Employee** sebagai **PK**.
- Satu pegawai dapat menangani banyak pesanan, tapi satu pesanan hanya dapat ditangani oleh satu pegawai.

### Kategori ke Produk (Category to Product) (1:M)
- **CategoryId** di tabel **Product** sebagai **FK** mengacu ke **CategoryId** di tabel **Category** sebagai **PK**.
- Satu kategori dapat memiliki banyak produk, tapi satu produk hanya dapat termasuk dalam satu kategori.

### Pesanan ke Detail Pesanan (Order to OrderDetail) (1:M)
- **OrderId** di tabel **OrderDetail** sebagai **FK** mengacu ke **OrderId** di tabel **Order** sebagai **PK**.
- Satu pesanan dapat memiliki banyak detail pesanan, tapi satu detail pesanan hanya terkait dengan satu pesanan.

### Produk ke Detail Pesanan (Product to OrderDetail) (1:M)
- **ProductId** di tabel **OrderDetail** sebagai **FK** mengacu ke **ProductId** di tabel **Product** sebagai **PK**.
- Satu produk bisa muncul di banyak detail pesanan, tapi satu detail pesanan hanya bisa memiliki satu produk.

### Pesanan ke Pembayaran (Order to Payment) (1:1)
- **PaymentId** di tabel **Order** sebagai **FK** mengacu ke **PaymentId** di tabel **Payment** sebagai **PK**.
- Satu pesanan hanya memiliki satu pembayaran, dan satu pembayaran hanya terkait dengan satu pesanan.

## Diagram ERD dalam Bentuk Teks

```plaintext
[ Pelanggan ]
- CustomerId (PK)
- FirstName
- LastName
- Email
- Phone

[ Pegawai ]
- EmployeeId (PK)
- FirstName
- LastName
- Email
- Phone
- Title

[ Kategori ]
- CategoryId (PK)
- CategoryName

[ Produk ]
- ProductId (PK)
- ProductName
- Price
- CategoryId (FK)

[ Pembayaran ]
- PaymentId (PK)
- PaymentType
- Amount
- PaymentDate

[ Pesanan ]
- OrderId (PK)
- OrderDate
- CustomerId (FK)
- EmployeeId (FK)
- PaymentId (FK)

[ DetailPesanan ]
- OrderDetailId (PK)
- OrderId (FK)
- ProductId (FK)
- Quantity
- Subtotal
```

Setiap entitas ditandai dengan Primary Key (PK) yang unik dan relasi antara entitas ditandai dengan Foreign Key (FK). Relasi ini menunjukkan bagaimana tabel-tabel tersebut saling berhubungan, memastikan integritas referensial dalam basis data.
```
```
# Tujuan dan Manfaat Database Kafe

Database kafe ini dibuat untuk mengelola dan menyimpan data yang berhubungan dengan operasi sehari-hari dari sebuah kafe. Berikut adalah tujuan dan manfaat dari database ini:

## Tujuan Database Kafe

1. **Mengelola Data Pelanggan**:
   - Menyimpan informasi kontak pelanggan seperti nama, email, dan nomor telepon.
   - Melacak pesanan yang dilakukan oleh setiap pelanggan.
   - Meningkatkan layanan pelanggan dengan memberikan informasi yang cepat dan akurat.

2. **Mengelola Data Pegawai**:
   - Menyimpan informasi tentang pegawai termasuk nama, jabatan, email, dan nomor telepon.
   - Melacak pesanan yang ditangani oleh setiap pegawai.
   - Membantu dalam penjadwalan dan pengelolaan tugas pegawai.

3. **Mengelola Data Produk**:
   - Menyimpan informasi produk yang dijual di kafe termasuk nama, harga, dan kategori produk.
   - Mengelompokkan produk berdasarkan kategori untuk memudahkan manajemen inventaris.
   - Memantau stok dan penjualan produk.

4. **Mengelola Data Kategori**:
   - Menyimpan dan mengelompokkan produk ke dalam kategori yang sesuai.
   - Mempermudah pencarian dan penyusunan menu produk.

5. **Mengelola Data Pesanan**:
   - Menyimpan informasi detail tentang setiap pesanan yang dibuat, termasuk tanggal pesanan, pelanggan yang memesan, dan pegawai yang menangani pesanan.
   - Melacak status pesanan dan memantau aliran pesanan dari pembuatan hingga penyelesaian.

6. **Mengelola Data Detail Pesanan**:
   - Menyimpan rincian produk yang dipesan dalam setiap pesanan, termasuk jumlah dan subtotal untuk setiap produk.
   - Memastikan keakuratan dalam perhitungan total pesanan dan stok produk.

7. **Mengelola Data Pembayaran**:
   - Menyimpan informasi tentang pembayaran yang diterima untuk setiap pesanan, termasuk jenis pembayaran, jumlah, dan tanggal pembayaran.
   - Memastikan bahwa semua pesanan telah dibayar dan memantau aliran pendapatan.

## Manfaat Database Kafe

- **Efisiensi Operasional**: Dengan database ini, proses pengelolaan pesanan, produk, pelanggan, dan pegawai menjadi lebih terstruktur dan efisien, mengurangi kesalahan manual dan mempercepat layanan.
- **Analisis Data**: Memungkinkan analisis data untuk pengambilan keputusan yang lebih baik, seperti menentukan produk terlaris, memahami kebiasaan pelanggan, dan mengevaluasi kinerja pegawai.
- **Peningkatan Layanan Pelanggan**: Dengan memiliki informasi yang terorganisir, kafe dapat memberikan layanan yang lebih personal dan responsif kepada pelanggan.
- **Penyimpanan Terpusat**: Semua data tersimpan di satu tempat yang terorganisir, sehingga memudahkan pencarian dan pembaruan data.
- **Keamanan Data**: Database memberikan mekanisme untuk melindungi data sensitif pelanggan dan transaksi kafe, memastikan integritas dan privasi data.

Dengan demikian, database kafe ini dirancang untuk mengoptimalkan manajemen operasional kafe, meningkatkan kepuasan pelanggan, dan mendukung pertumbuhan bisnis melalui pengelolaan data yang efektif dan efisien.

