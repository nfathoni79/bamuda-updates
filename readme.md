# 2021.10.24

## FishOn

**Modified**
- *Manifest*: Tambah `BuyHistoryActivity`
- *DashboardActivity*: Bypass BNI (temp)
- *BillingAddressActivity*: Refaktor `ButterKnife` -> `ViewBinding`
- *BuyActivity*:
  * Refaktor `ButterKnife` -> `ViewBinding`
  * Tambah pilihan ambil sendiri/dikirim
  * Refresh address
- *DetailProductActivity*: Fix infinite loading ketika tidak mengisi quantity
- *FishMartActivity*:
  * Refaktor `ButterKnife` -> `ViewBinding`
  * Tambah menu history
- *MarketApi*: Fix message di dialog terpotong
- *FishMartApi*: Tambah `getBuyHistory`
- *Cart*: Tambah constructor
- *Product*:
  * Tambah constructor hanya untuk `id`, `title`, `price`
  * Tambah `getShortTitle`
- *activity_billing_address*: Rename ID
- *activity_buy*: Refaktor ke `ConstraintLayout`
- *activity_fish_mart*: Tambah menu history
- *strings*: Tambah `info_hist_empty`, dll

**New**
- *BuyHistoryActivity*
- *BuyHistoryAdapter*
- *BuyHistoryListener*
- *BuyHistory*
- *ic_baseline_history_24.xml*: Icon untuk menu riwayat belanja
- *activity_buy_history*
- *item_buy_history*

## fishOnServer

**Modified**
- *fishMart/models/store_model*: Hilangkan primary key pada `OsposSalesItems.sale`
- *fishmart/serializer*: Tambah `HistorySerializer`, `HistoryItemSerializer`
- *fishMart/urls*: Tambah URL history
- *fishMart/views*:
  * Rename `array` -> `array_cart` di `DoPurchase.create`
  * Tambah comment
  * Bypass BNI (temp)
  * Tambah `get_purchase_history`

## fishMart

**Modified**
- *application/models/Pesan_barang*:
  * Restruktur query
  * Fix harga belum dikali quantity
  * Update reject -> `is_dilivery = -1`
  * Tambah `get_alamat`
- *application/views/pesanbarang/manage*: Ubah tampilan alamat yang kosong

---

# 2021.11.16

## TPI Online

**Modified**
- *lelang/models*: Tambah field `min_bidding`
- *lelang/views*:
  * Tambah kondisi harga penawaran (minimal bidding, kelipatan 100)
  * Cek saldo sebelum bidding (uncomment code yang sudah ada)

**New**
- *lelang/migrations/0019_auto_20211116_2226*: Tambah field `min_bidding`

## E-TPI

**Modified**
- *main/store_models*: Tambah field `min_bidding`
- *sikka/views*: Set harga minimal bidding
- *sukabumi/views*: Set harga minimal bidding
- *trenggalek/views*: Set harga minimal bidding

---

# 2022.5.20

## FishOn

**Modified**
- *app/build.gradle*: Tambah `buildConfigField` `AES_KEY`
- *FishFinderActivity*:
  * Ambil titik ikan dari cache di mode satelit
  * Fix crash ketika kembali
  * Sembunyikan tombol Download Maps
- *DashboardActivity*:
  * Reorder fungsi
  * Nonaktifkan get profile
  * Nonaktifkan get & update location di mode satelit
  * Nonaktifkan get balance di mode satelit
  * Menambahkan komentar
  * Refaktor `isSatMode`
- *ProfilActivity*:
  * Refaktor `isSatMode`
  * Nonaktifkan get profile di mode satelit
  * Ambil profil dari cache di mode satelit
  * Tambahkan +62 di depan nomor ponsel dari cache
  * Set foto profil default ketika gagal fetch
- *activity_fish_finder*: Refaktor `onClick` pada tombol back

**New**
- */api/netra/NetraApi*
- */api/netra/NetraClient*
- */entity/netra/Message*
- */util/AesUtil*

---

# 2022.5.21

## FishOn

**Modified**
- *LogBookNewActivity*: Ubah algoritma unggah Logbook
- *DetailProductApi*: Refaktor parameter method refresh
- *MarketApi*: Refaktor parameter method refresh
- *BuyCartApi*: Refaktor parameter method refresh
- *ChatAPI*: Refaktor parameter method refresh
- *FishFinderApi*: Refaktor parameter method refresh
- *FishMartApi*: Refaktor parameter method refresh
- *JualIkanApi*: Refaktor parameter method refresh
- *LogBookApi*: Refresh token saat unggah Logbook jika token tidak valid
- *PurchaseOrderAPI*: Refaktor parameter method refresh
- *ProfileApi*: Refaktor parameter method refresh
- *FcmApi*: Refaktor parameter method refresh
- *RefreshInterface*: Refaktor parameter method refresh
- *SignApi*: Refaktor parameter method refresh
- *SosAPI*: Refaktor parameter method refresh
- *Feedback*: Tambah konstruktor untuk parameter kirim Logbook

---

# 2022.5.22

## FishOn

**Modified**
- *LogBookNewActivity*: Nonaktifkan tombol Unggah Logbook di mode satelit
- *LogBookNewDetailActivity*: Langsung mengunggah Logbook di mode satelit
- *NetraApi*: Refaktor parameter context
- *LogBookDBHelper*:
  * Mengubah `getColumnIndex` ke `getColumnIndexOrThrow`
  * Menambah method `getFeedback`
- *Feedback*: menambah method `getEpochCreatedAt`, `getEpochUpdatedAt`, `createDelimitedString`, `getNoteInt`
- *strings*: Menambah string tombol Unggah (Logbook tunggal)

---

# 2022.6.14

## FishOn

**Modified**
- *FishFinderActivity*:
  * Tambah fungsi get titik ikan di mode satelit
  * Tambah button refresh
  * Tambah `autoCheckStatus` untuk memastikan eksekusi auto refresh 1 kali
  * Refaktor `isSatMode` -> `PrefUtil.isSatMode`
- *DashboardActivity*:
  * Refaktor request permission ->  `REQUEST_CODE_LOCATION_CAMERA`
  * Update listener NetraApi
  * Refaktor `isSatMode` -> `PrefUtil.isSatMode`
  * Refaktor inisialisasi `mGpsTracker` -> `initGps`
  * Cek `mGpsTracker != null` sebelum kirim SOS
  * Update fungsi kirim SOS di mode satelit
  * Cek apakah sedang request sebelum ubah mode internet
- *ModeActivity*: Refaktor `isSatMode` -> `PrefUtil.isSatMode`
- *LogBookNewActivity*:
  * Tambah `NetraApi` untuk cek status pengiriman
  * Tambah tombol refresh
  * Refaktor `isSatMode` -> `PrefUtil.isSatMode`
- *LogBookNewDetailActivity*:
  * Update fungsi unggah Logbook di mode satelit
  * Refaktor `isSatMode` -> `PrefUtil.isSatMode`
- *FeedbackAdapter*: Ubah tampilan item Logbook
- *ProfilActivity*: Refaktor `isSatMode` -> `PrefUtil.isSatMode`
- *NetraApi*:
  * Tambah `deleteDown` & `DeleteDownListener`
  * Fix listener di loop
- *NetraClient*:
  * Tambah `BASE_URL` untuk test
  * Tambah `delete`
- *LogBookDBHelper*:
  * Fix beberapa warning
  * Tambah beberapa doc
  * Tambah `updateFeedbackOngoing`
- *Feedback*:
  * Tambah `isOngoing`
  * Hilangkan `id` dan `updatedAt` di `createDelimitedString`
- *FishModel*: Tambah konstruktor dengan parameter `lat` dan `lon`
- *AesUtil*: Tambah `ecbDecrypt` dan `hexToText`
- *PrefUtil*: Tambah beberapa fungsi yang berkaitan dengan pengiriman ke satelit
- *activity_fish_finder*: Tambah tombol refresh
- *activity_log_book_new*: Refaktor `CoordinatorLayout` -> `LinearLayout`
- *item_logbook_new*: Ubah tampilan
- *strings*: Tambah beberapa string yang berkaitan dengan Netra dan Logbook 

**New**
- *ic_baseline_refresh_24.xml*
- *menu_refresh*

---

# 2022.7.5

## Perindo Nelayan

**Modified**
- *FishSellActivity*: Tambah `clearFish` di `ssStoreName`
- *FishSellFragment*: Nonaktifkan tombol add jika sudah menambah 1 ikan di cabang dengan `oneFish`
- *FishMartApi*: Tambah `setOneFish` di `getStore` `onSuccess`
- *Store*: Tambah field `oneFish`

## fishOnServer

**Modified**
- *fishMart/core_models*: Reformat, tambah field `active` dan `one_fish` di `Store`
- *fishMart/models/store_models*: Hilangkan import yang tidak perlu
- *fishMart/serializer*: Reformat
- *fishMart/urls*: Hilangkan import yang tidak perlu
- *fishMart/views*: Reformat, update query `getStoreList`

## Database fishMartCore, Tabel store

- Ubah nama kolom `is_active` jadi active
- Ubah tipe kolom `active` jadi `tinyint(1) unsigned, default 0`
- Tambah kolom `one_fish`, `tinyint(1) unsigned, default 0`

---

# 2022.7.7

## Perindo Nelayan

**Modified**
- *FishSellFragment*: Fix tombol add tidak aktif kembali setelah jual ikan

## fishOnServer

**Modified**
- *LogBook/admin*: Update tampilan admin `IkanAdmin`
- *LogBook/models*: Tambah field `Ikan.max_price`
- *LogBook/serializer*: Tambah field `IkanSerializer.max_price`
- *LogBook/urls*: Reformat
- *LogBook/views*:
  * Reformat
  * Urutkan list ikan berdasarkan ID di `ListIkan`

**New**
- *LogBook/migrations/0011_ikan_max_price*

## Perindo Pabrik

**Modified**
- *ListBiddingAdapter*: Update tampilan last bidding jadi total dan per kg
- *DetailFragment*:
  * Update tampilan min bidding jadi per kg
  * Kalikan harga bidding dengan berat ketika disubmit
  * Update tampilan harga di timeline jadi per kg
  * Buat method `calculatePricePerKg`
- *Lelang*: Refaktor nama field jadi camelCase
- *strings*: Update label harga minimal dan penawaran jadi per kg

## TPI Online

**Modified**
- *User/serializer*: Reformat
- *lelang/lib*: Update comment status di `cariPemenang2`
- *lelang/models*:
  * Ubah field `LelangIkan.created_at` jadi `auto_now_add`
  * Tambah field `LelangIkan.updated_at`
  * Tambah field `LelangIkan.max_bidding`
  * Tambah method `LelangIkan.get_wilayah_name`
- *lelang/serializer*: Tambah field `wilayah` di LelangSerializer dan MyLelangSerializer
- *lelang/store_model*: Tambah field `active` dan `one_fish` di `Store`, reformat
- *lelang/urls*: Reformat
- *lelang/views*:
  * Refaktor response
  * Tambah kondisi lelang tidak ditemukan di `Menawar`
  * Tambah kondisi lelang melebihi batas waktu di `Menawar`
  * Ubah pesan ketika penawaran di bawah harga minimal
  * Tambah kondisi harga penawaran melebihi maksimal
  * Reformat

**New**
- *lelang/migrations/0020_auto_20220706_1606*

## Perindo Lelang

**Modified**
- *bacan/views*
  * Tambah `max_price` di `accept_transaction`
  * Langsung tutup lelang jika autobid
- *main/store_models*:
  * Tambah field di `TpiOnline_LelangIkan` sesuai TPI Online
  * Tambah field di `Fishon_Ikan` sesuai fishOnServer
- *muarabaru/views*:
  * Tambah `max_price` di `accept_transaction`
  * Langsung tutup lelang jika autobid

---

# 2022.8.5

## TPI Online

**Modified**
- *lelang/models*: Tambah default di field `LelangIkan.last_bidding`
- *lelang/serializer*: Tambah field `id` di `LelangPfxSerializer`
- *lelang/urls*: Refaktor viewset `Lelang`
- *lelang/views*: Update `list_pfx`
- *tpi_online/settings*: Tambah CORS

**New**
- *lelang/migrations/0022_alter_lelangikan_last_bidding.py*

## Perindo Lelang

**Modified**
- *main/store_models*: Tambah default di field `TpiOnline_LelangIkan.last_bidding`

---

# 2022.8.12

## BNI API

**Modified**
- *BankAccountController*: Tambah sort dan filter OGP di `index`
- *BniController*: Tambah `doPayment`
- *BniService*: Tambah `doPayment`
- *routes/api*: Tambah API `transfers`

**New**
- *TransferController*
- *Transfer*
- *2022_08_11_130400_create_transfers_table*

## BNIX

**Modified**
- *router/index*: Tambah `Transfers`
- *BniService*: Tambah sort & OGP di `getAccounts`, tambah `getTransfers`, `transfer`
- *views/Accounts*:
  * Tambah trailing comma
  * Tambah sort & OGP di `getAccounts`
- *views/Base*: Tambah navigasi `Transfers`

**New**
- *views/Transfers*

---

# 2022.8.16

## fishOnServer

**Modified**
- *LogBook/serializer*: Tambah `required=False` di `FeedbackSerializer.lap_id`
- *LogBook/views*: Tambah try except ketika get `PointLapan` by `lap_id`

## FishOn

**Modified**
- *FishFinderApi*: cek `lap_id == null` di `getLimitedPoints`
- *activity_dashboard*: Sembunyikan mode internet
- *app/build.gradle*: Update versi 2.3.2

---

# 2022.8.19

## Perindo Nelayan

**Modified**
- *DashboardActivity*: Update `setupBottomNav`
- *BuyActivity*: Hapus bottom nav, update tampilan
- *ProfilActivity*: Hilangkan bottom nav, update tampilan
- *activity_buy*: Hilangkan bottom nav, update tampilan
- *activity_buy_history*: Update warna spinner
- *activity_profil*: Hilangkan bottom nav, update tampilan
- *item_home_menu*: Kecilkan teks deskripsi
- *layout_btm_nav*: Hilangkan Home dan Notifikasi, beri efek ripple
- *order_list_item*: Update warna button plus minus
- *strings*: Tambah deskripsi toko dan placeholder toko

**New**
- *ic_baseline_location_on_24*
- *ic_baseline_store_24*
- *layout_btm_nav_0*: Bottom nav lama

---

# 2022.8.22

## Perindo Nelayan

**Modified**
- *FishFinderActivity*: Fix crash ketika back saat navigasi
- *activity_fish_finder*: Refaktor back button
- *LogBookNewActivity*: Update algoritma unggah Logbook
- *FeedbackAdapter*: Update tampilan item Logbook
- *item_logbook_new*: Update tampilan item Logbook
- *strings*: Tambah string untuk Logbook
- *FishSellActivity*: Tambah `initStoreList`, update tampilan
- *BuyActivity*: Ubah `initStoreList` ke private, ubah warna teks Spinner
- *activity_buy*: Update tampilan Spinner
- *activity_fish_sell*: Update tampilan

---

# 2022.9.2

## BNI API

**Modified**
- *AuthController*:
  * Tambah ability di `createToken`
  * Tambah method `user`
- *Kernel*: Tambah middleware `abilities` & `ability`
- *User*: Tambah relationship `role`
- *routes/api*: Kelompokkan berdasarkan ability

**New**
- *Role*
- *2022_09_01_103915_create_roles_table*
- *2022_09_01_104449_add_role_to_users_table*

## BNIX

**Modified**
- *services/BniService*: Tambah `getCurrentUser`
- *views/Base*:
  * Tambah prop `user` di `router-view`
  * Tambah method `getCurrentUser`
- *views/Login*: Hapus `localStorage` nama dan email di `submitLogin`
- *views/Transfers*: Hilangkan tombol Transfer jika bukan `supe`

---

# 2022.9.12

## TPI Online

**Modified**
- *User/models*: Tambah field `buy_area_code`
- *lelang/views*: Filter lelang list dan home sesuai `buy_area_code`

**New**
- *0004_userprofile_buy_area_code*

---

# 2022.9.28

## Coba Netrahub

**Modified**
- *coba_netrahub/settings*: Ubah database ke PostgreSQL
- *db.sqlite3*: Hapus
- *main/models*: Tambah `InboxMessage`, `OutboxMessage`
- *main/serializers*: Tambah `OngoingSerializer`, `InboxSerializer`, `FromDevSerializer`, `ToDevSerializer`
- *main/views*: Update dari hardcode ke database

---

# 2022.9.30

## FishOn

**Modified**
- *LogBookNewDetailActivity*: Tambah parameter status di message unggah logbook

## fishOnServer

**Modified**
- *netra/utils*: Fix exception di fungsi `decrypt`

---

# 2022.10.28

## Perindo Fishmart/Gerai

**Modified**
- *config/config*: Ubah versi aplikasi, ubah `sess_save_path`
- *config/database*: Fix `hostname`
- *views/configs/manage*: Tambah margin atas
- *views/home/office*: Tambah margin atas, ubah warna teks menu
- *views/login*: Ubah title, favicon, logo, icon kode gerai, teks Sign In
- *views/partial/header*: Ubah title, favicon, logo
- *views/partial/header_sales*: Ubah logo
- *bin/server.sh*: Ubah php ke versi 7.3
- *public/css/style.css*: Tambah style navigasi office, `#required_fields_message`
- *public/images/favicon.ico*: Ubah favicon
- *public/index.php*: Muat file `.env` sebelum `config`

**Deleted**
- *public/images/fishMart-warna.png*
- *public/images/fishMart-white.png*

**New**
- *public/images/perindo-gerai-white.png*
- *public/images/perindo-gerai.png*
- *public/images/store.png*: Icon login kode gerai

---

# 2022.11.2

## Perindo Fishmart/Gerai

**Modified**
- *controllers/Home*: Load model `Home_chart`, tambah fungsi `get_chart_data`
- *views/home/home*: Update script `echarts`
- *views/partial/footer*: Fix fungsi `numberWithCommas` jika `x == false`

**New**
- *models/Home_chart*: Model untuk mendapatkan data penjualan di home

---

# 2022.11.21

## E-TPI

**Modified**
- *main/store_models*:
  * Update field `last_bidding`, `created_at` di `TpiOnline_LelangIkan`
  * Tambah field `updated_at`, `max_bidding` di `TpiOnline_LelangIkan`
  * Tambah field `max_price` di `Fishon_Ikan`
- *trenggalek/views*: Reformat, update fungsi `accept_transaction`

---

# 2022.11.23

## TPI Online

**Modified**
- *lelang/lib*: Tambah nomor rekening operator dan fishon