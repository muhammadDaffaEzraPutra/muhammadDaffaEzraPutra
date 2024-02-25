import os


def clear_screen():
    if os.name == 'nt':
        _ = os.system('cls')

clear_screen()


class Parkiran:
    def __init__(self, nama, jenis, plat, jam_masuk, jam_keluar):
        self.nama = nama
        self.jenis = jenis
        self.plat = plat
        self.jam_masuk = jam_masuk
        self.jam_keluar = jam_keluar

    def display_info(self):
        print(f"Nama kendaraan: {self.nama}")
        print(f"Jenis kendaraan: {self.jenis}")
        print(f"Plat: {self.plat}")
        print(f"Jam masuk: {self.jam_masuk}")
        print(f"Jam keluar: {self.jam_keluar}")
        print()


class Parkiran:
    def __init__(self):
        self.daftar_kendaraan = []

    def cari_kendaraan(self, plat):
        for kendaraan in self.daftar_kendaraan:
            if kendaraan.plat == plat:
                print(f"Kendaraan dengan plat '{plat}' ditemukan.")
                return kendaraan
        print(f"Kendaraan dengan plat '{plat}' tidak ditemukan.")
        return None

    def tambah_kendaraan(self, kendaraan):
        self.daftar_kendaraan.append(kendaraan)
        print(f"Kendaraan dengan plat '{kendaraan.plat}' berhasil ditambahkan.")

    def update_kendaraan(self, plat, kendaraan_baru):
        kendaraan_lama = self.cari_kendaraan(plat)
        if kendaraan_lama:
            index = self.daftar_kendaraan.index(kendaraan_lama)
            self.daftar_kendaraan[index] = kendaraan_baru
            print(f"Kendaraan dengan plat '{plat}' berhasil diperbarui.")
        else:
            print(f"Kendaraan dengan plat '{plat}' tidak ditemukan.")

    def hapus_kendaraan(self, plat):
        kendaraan = self.cari_kendaraan(plat)
        if kendaraan:
            self.daftar_kendaraan.remove(kendaraan)
            print(f"Kendaraan dengan plat '{plat}' berhasil dihapus.")
        else:
            print(f"Kendaraan dengan plat '{plat}' tidak ditemukan.")

    def tampilkan_katalog(self):
        print("Daftar Kendaraan:")
        for kendaraan in self.daftar_kendaraan:
            kendaraan.display_info()


# Fungsi untuk menampilkan menu
def tampilkan_menu():
    print("Menu:")
    print("1. Tambah Kendaraan")
    print("2. Tampilkan Katalog Kendaraan")
    print("3. Perbarui Kendaraan")
    print("4. Hapus Kendaraan")
    print("5. Keluar")
    print()


# Contoh penggunaan:
parkiran = Parkiran()

while True:
    tampilkan_menu()
    pilihan = input("Pilih menu: ")

    if pilihan == "1":
        nama = input("Nama Kendaraan: ")
        jenis = input("Jenis Kendaraan: ")
        plat = input("Plat Kendaraan: ")
        jam_masuk = input("Jam Masuk: ")
        jam_keluar = input("Jam Keluar: ")
        kendaraan_baru = Parkiran(nama, jenis, plat, jam_masuk, jam_keluar)
        parkiran.tambah_kendaraan(kendaraan_baru)

    elif pilihan == "2":
        parkiran.tampilkan_katalog()

    elif pilihan == "3":
        plat = input("Masukkan plat kendaraan yang ingin diperbarui: ")
        kendaraan_baru = Parkiran("Avanza", "Mobil", "B 5678 CD", "08:00", "13:00")
        parkiran.update_kendaraan(plat, kendaraan_baru)

    elif pilihan == "4":
        plat = input("Masukkan plat kendaraan yang ingin dihapus: ")
        parkiran.hapus_kendaraan(plat)

    elif pilihan == "5":
        print("Program berakhir.")
        break

    else:
        print("Pilihan tidak valid. Silakan pilih menu yang sesuai.")
