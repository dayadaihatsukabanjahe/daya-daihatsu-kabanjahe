import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Carousel } from "@/components/ui/carousel";
import { motion } from "framer-motion";
import { FaStar, FaWhatsapp, FaCarSide, FaMapMarkerAlt, FaCarCrash, FaFilter, FaPhoneAlt, FaFileDownload, FaCalculator, FaNewspaper } from "react-icons/fa";

export default function Showroom() {
  const [form, setForm] = useState({ nama: "", nohp: "", pesan: "" });
  const handleChange = (e) => setForm({ ...form, [e.target.name]: e.target.value });

  return (
    <div className="bg-gray-50 min-h-screen p-4 md:p-10 font-sans">
      {/* Header */}
      <header className="text-center mb-10">
        <motion.h1
          className="text-4xl font-bold text-gray-800"
          initial={{ opacity: 0, y: -30 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
        >
          Daya Daihatsu Kabanjahe
        </motion.h1>
        <p className="text-gray-500 mt-2">Dealer Resmi Mobil Daihatsu Wilayah Kabanjahe</p>
      </header>

      {/* Hero Section */}
      <section className="mb-12 relative rounded-2xl overflow-hidden shadow-xl">
        <img src="/empty-floor-modern-architectural-passageway-1.png" alt="hero" className="w-full h-64 object-cover brightness-75" />
        <div className="absolute inset-0 flex flex-col items-center justify-center text-white text-center px-4">
          <h2 className="text-3xl md:text-4xl font-bold mb-2">Promo Khusus Bulan Mei</h2>
          <p className="text-lg md:text-xl">DP Rendah & Cicilan Ringan untuk Semua Tipe Mobil Daihatsu</p>
        </div>
      </section>

      {/* Fitur Tambahan */}
      <section className="mb-12 grid md:grid-cols-3 gap-6 text-center">
        <div className="bg-white rounded-xl shadow p-6 flex flex-col items-center">
          <FaCalculator className="text-3xl text-blue-600 mb-2" />
          <h3 className="font-semibold">Simulasi Kredit</h3>
          <p className="text-sm text-gray-500">Hitung angsuran dan DP secara cepat.</p>
        </div>
        <div className="bg-white rounded-xl shadow p-6 flex flex-col items-center">
          <FaFileDownload className="text-3xl text-blue-600 mb-2" />
          <h3 className="font-semibold">Download Brosur</h3>
          <p className="text-sm text-gray-500">Unduh brosur PDF semua tipe mobil Daihatsu.</p>
        </div>
        <div className="bg-white rounded-xl shadow p-6 flex flex-col items-center">
          <FaNewspaper className="text-3xl text-blue-600 mb-2" />
          <h3 className="font-semibold">Artikel & Tips</h3>
          <p className="text-sm text-gray-500">Informasi, tips otomotif, dan berita Daihatsu.</p>
        </div>
      </section>

      {/* Simulasi Kredit (Form) */}
      <section className="mb-12">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Kalkulator Kredit</h2>
        <Card className="max-w-2xl mx-auto bg-white">
          <CardContent className="p-4 grid grid-cols-1 md:grid-cols-2 gap-4">
            <Input placeholder="Harga Mobil (Rp)" type="number" />
            <Input placeholder="Uang Muka (Rp)" type="number" />
            <Input placeholder="Bunga (% per tahun)" type="number" />
            <Input placeholder="Tenor (bulan)" type="number" />
            <Button className="md:col-span-2 w-full">Hitung Angsuran</Button>
          </CardContent>
        </Card>
      </section>

      {/* Filter Mobil */}
      <section className="mb-12">
        <div className="flex items-center justify-between mb-4">
          <h2 className="text-2xl font-semibold text-gray-800">Filter Unit Mobil</h2>
          <Button className="flex items-center gap-2"><FaFilter /> Filter Mobil</Button>
        </div>
        <p className="text-sm text-gray-500">Pilih jenis mobil berdasarkan tipe atau kebutuhan Anda.</p>
      </section>

      {/* Galeri Foto/Video */}
      <section className="mb-12">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Galeri Promo & Mobil</h2>
        <Carousel images={["/1.png", "/2.png"]} video="/PROMO.mp4" />
      </section>

      {/* Unit Mobil */}
      <section className="mb-12">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Unit Mobil Tersedia</h2>
        <div className="grid md:grid-cols-4 gap-6">
          {["ROCKY", "TERIOS", "GRANDMAX", "XENIA"].map((unit, index) => (
            <Card key={index} className="shadow-md">
              <CardContent className="p-4 space-y-2">
                <img src={`/${unit.toUpperCase()}-1.png`} alt={unit} className="w-full h-40 object-contain" />
                <h3 className="font-semibold text-lg">{unit}</h3>
                <p className="text-sm text-gray-500">Promo spesial bulan ini. Cicilan ringan & DP minim!</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Form Pemesanan */}
      <section className="mb-12">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Form Pemesanan Langsung</h2>
        <Card className="max-w-xl mx-auto bg-white">
          <CardContent className="p-4 space-y-4">
            <Input placeholder="Nama" name="nama" value={form.nama} onChange={handleChange} />
            <Input placeholder="Nomor HP" name="nohp" value={form.nohp} onChange={handleChange} />
            <Textarea placeholder="Pesan atau mobil yang diminati" name="pesan" value={form.pesan} onChange={handleChange} />
            <Button className="w-full">Kirim Pemesanan</Button>
          </CardContent>
        </Card>
      </section>

      {/* Kontak WhatsApp */}
      <section className="text-center mb-12">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Hubungi Kami via WhatsApp</h2>
        <div className="flex flex-col md:flex-row justify-center gap-4">
          <a href="https://wa.me/6281370031289" className="flex items-center gap-2 bg-green-500 text-white px-4 py-2 rounded-full hover:bg-green-600" target="_blank">
            <FaWhatsapp /> Sales 1
          </a>
          <a href="https://wa.me/6281262309281" className="flex items-center gap-2 bg-green-500 text-white px-4 py-2 rounded-full hover:bg-green-600" target="_blank">
            <FaWhatsapp /> Sales 2
          </a>
        </div>
      </section>

      {/* Lokasi Dealer */}
      <section className="mb-12 text-center">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Alamat Dealer</h2>
        <div className="flex justify-center">
          <a href="https://www.google.com/maps?q=Daya+Daihatsu+Kabanjahe" target="_blank" className="inline-flex items-center gap-2 text-blue-600 hover:underline">
            <FaMapMarkerAlt /> Lihat di Google Maps
          </a>
        </div>
      </section>

      {/* Testimoni */}
      <section className="mb-10">
        <h2 className="text-2xl font-semibold text-gray-800 mb-4">Testimoni Pelanggan</h2>
        <div className="grid md:grid-cols-2 gap-4">
          {[1, 2].map((id) => (
            <Card key={id} className="bg-white shadow-xl">
              <CardContent className="p-4">
                <div className="flex items-center gap-1 text-yellow-400 mb-2">
                  {[...Array(Math.floor(Math.random() * 2) + 4)].map((_, i) => <FaStar key={i} />)}
                </div>
                <p className="text-gray-700 italic">“Pelayanan cepat, mobil langsung dikirim. Terima kasih Daihatsu!”</p>
                <p className="text-right text-sm text-gray-500">- Pelanggan {id}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Footer */}
      <footer className="text-center text-sm text-gray-500 border-t pt-4">
        © {new Date().getFullYear()} Daya Daihatsu Kabanjahe. All rights reserved.
      </footer>
    </div>
  );
}
