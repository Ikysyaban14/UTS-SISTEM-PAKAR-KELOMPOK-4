# UTS-SISTEM-PAKAR-KELOMPOK-4
class ExpertSystem:
    def __init__(self):
        # 1. DATA KERUSAKAN (Goals)
        self.kerusakan = {
            "K01": "Kerusakan LED/LCD",
            "K02": "Kerusakan IC Power",
            "K03": "Kerusakan VGA",
            "K04": "Kerusakan RAM",
            "K05": "Kerusakan Harddisk",
            "K06": "Kerusakan Motherboard",
            "K07": "Kerusakan Keyboard",
            "K08": "Kerusakan DVD Drive",
            "K09": "Kerusakan Port USB",
            "K10": "Kerusakan Touchpad",
            "K11": "Kerusakan Wifi",
            "K12": "Kerusakan Sistem Operasi/Software"
        }

        # 2. DATA GEJALA (Evidence) - Sesuaikan dengan gambar
        self.gejala = {
            "G01": "Tidak ada tampilan sama sekali",
            "G02": "Ada tampilan tapi gelap (no backlight)",
            "G03": "Layar blank putih",
            "G04": "Terdapat garis warna-warni",
            "G05": "Ada spot-spot putih (panuan) pada layar",
            "G06": "Layar laptop terbalik",
            "G07": "Jika tersenggol layar laptop bergoyang",
            "G08": "Lampu charger laptop tidak menyala",
            "G09": "Lampu baterai charger berkedip tak menentu lalu mati",
            "G10": "Laptop Mati Total",
            "G11": "Tegangan di tombol on/off tidak ada",
            "G12": "Baterai tidak terisi saat di cas",
            "G13": "Laptop Not Responding",
            "G14": "Driver sering stopped working",
            "G15": "VGA tidak berjalan sama sekali",
            "G16": "BSOD (Blue Screen Of Death)",
            "G17": "Suara kipas yang lebih berisik",
            "G18": "Resolusi tidak mencapai ukuran maksimal",
            "G19": "Laptop Cepat Panas",
            "G20": "Tidak dapat masuk ke sistem operasi",
            "G21": "Laptop Restart Sendiri",
            "G22": "BIOS tidak berfungsi normal",
            "G23": "Muncul bunyi bip",
            "G24": "Kapasitas RAM yang terbaca kurang",
            "G25": "Performa laptop melemah",
            "G26": "Tidak bisa meng-install apl baru",
            "G27": "Laptop overheat",
            "G28": "Tidak muncul tampilan apapun di monitor",
            "G29": "Mengeluarkan kode-kode aneh",
            "G30": "Gagal booting",
            "G31": "Tidak bisa meng-copy atau reading file",
            "G32": "Permintaan gagal",
            "G33": "Harddisk sangat lama untuk loading",
            "G34": "Error pada harddisk berurutan",
            "G35": "Parameter tidak benar",
            "G36": "Adanya bad shadow pada harddisk",
            "G37": "Kipas processor tidak beroperasi",
            "G38": "Sering terjadi hang",
            "G39": "Ada bau terbakar",
            "G40": "Keyboard laptop terdeteksi, tapi windows tidak terdeteksi",
            "G41": "Saat windows berjalan, keyboard berhenti merespon",
            "G42": "Semua tombol tidak berfungsi",
            "G43": "Hanya satu atau beberapa tombol yang tidak berfungsi",
            "G44": "Keyboard mengetik tidak sesuai yang diinginkan",
            "G45": "Ada suara aneh dalam laptop",
            "G46": "Laptop tidak bisa membaca CD maupun DVD",
            "G47": "Drive DVD tidak muncul di my computer",
            "G48": "Pemutar CD/DVD lambat membaca data",
            "G49": "Semua USB port laptop berhenti",
            "G50": "Laptop berhenti mengenali perangkat USB",
            "G51": "Muncul notifikasi USB not recognized",
            "G52": "Kursor pada laptop yang melompat-lompat sendiri",
            "G53": "Kursor bergerak sendiri",
            "G54": "Sensitivitas mouse/touchpad melambat",
            "G55": "Touchpad pada laptop tidak berfungsi",
            "G56": "Pointer tidak bergerak",
            "G57": "Laptop tidak bisa mendeteksi sinyal wifi",
            "G58": "Icon wireless ada tanda seru kuning",
            "G59": "Icon wireless ada tanda x",
            "G60": "Laptop booting dan beroperasi dengan lambat",
            "G61": "Windows explorer tidak dapat dijalankan",
            "G62": "Booting terhenti setelah berhasil melakukan post",
            "G63": "Start menu tidak dapat dijalankan",
            "G64": "Prosedur shutdown tidak dapat dijalankan",
            "G65": "Prosedur shutdown berhenti sebelum komputer mati"
        }

        # 3. BASIS ATURAN (Rules)
        self.rules = {
            "K01": ["G01", "G02", "G03", "G04", "G05", "G06", "G07"],
            "K02": ["G08", "G09", "G10", "G11", "G12"],
            "K03": ["G13", "G14", "G15", "G16", "G17", "G18", "G19", "G20", "G21", "G22"],
            "K04": ["G13", "G23", "G24", "G25", "G26", "G27", "G28"],
            "K05": ["G16", "G29", "G30", "G31", "G32", "G33", "G34", "G35", "G36"],
            "K06": ["G37", "G38", "G39"],
            "K07": ["G23", "G40", "G41", "G42", "G43", "G44"],
            "K08": ["G45", "G46", "G47", "G48"],
            "K09": ["G49", "G50", "G51"],
            "K10": ["G52", "G53", "G54", "G55", "G56"],
            "K11": ["G57", "G58", "G59"],
            "K12": ["G38", "G60", "G61", "G62", "G63", "G64", "G65"]
        }

        self.user_responses = {}

    def ask_question(self, gejala_id):
        if gejala_id not in self.user_responses:
            # Mengambil deskripsi gejala dari dictionary self.gejala
            nama_gejala = self.gejala.get(gejala_id, "Gejala tidak diketahui")
            print(f"Pertanyaan [{gejala_id}]: Apakah {nama_gejala}?")
            choice = input("Jawab (y/n): ").lower()
            self.user_responses[gejala_id] = (choice == 'y')
        return self.user_responses[gejala_id]

    def backward_chaining(self, target_k):
        gejala_list = self.rules.get(target_k, [])
        for g in gejala_list:
            if not self.ask_question(g):
                return False
        return True

    def diagnose(self):
        print("="*50)
        print("SISTEM PAKAR DIAGNOSA KERUSAKAN LAPTOP")
        print("="*50)
        print("Jawab 'y' jika YA dan 'n' jika TIDAK\n")
        
        hasil_diagnosa = []

        for k_id, k_nama in self.kerusakan.items():
            if self.backward_chaining(k_id):
                hasil_diagnosa.append(f"{k_id} - {k_nama}")

        print("\n" + "="*50)
        if hasil_diagnosa:
            print("HASIL DIAGNOSA:")
            for hasil in hasil_diagnosa:
                print(f"Terdeteksi: {hasil}")
        else:
            print("Hasil: Tidak ditemukan kerusakan yang sesuai.")
        print("="*50)

if __name__ == "__main__":
    app = ExpertSystem()
    app.diagnose()
