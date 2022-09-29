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