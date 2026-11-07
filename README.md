# -royal-uc
ROYAL UC – PUBG Mobile UC satış platformu

"use client";

import { useState } from "react";

const packages = [
  { uc: "60 UC", price: "Fiyat yakında" },
  { uc: "325 UC", price: "Fiyat yakında" },
  { uc: "660 UC", price: "Fiyat yakında" },
  { uc: "1800 UC", price: "Fiyat yakında" },
  { uc: "3850 UC", price: "Fiyat yakında" },
  { uc: "8100 UC", price: "Fiyat yakında" },
];

export default function Home() {
  const [selected, setSelected] = useState("660 UC");
  const [playerId, setPlayerId] = useState("");
  const [contact, setContact] = useState("");
  const [message, setMessage] = useState("");

  function createOrder() {
    if (!playerId.trim() || !contact.trim()) {
      setMessage("Lütfen oyuncu ID ve iletişim bilgilerini gir.");
      return;
    }

    setMessage(
      "Talep bilgilerin alındı. Bu bir test ekranıdır; henüz ödeme alınmıyor ve UC gönderilmiyor."
    );
  }

  return (
    <main className="min-h-screen bg-[#090909] text-white">
      <header className="border-b border-yellow-600/30 px-6 py-5">
        <div className="mx-auto flex max-w-6xl items-center justify-between">
          <h1 className="text-2xl font-black tracking-widest text-yellow-400">
            ROYAL UC
          </h1>
          <span className="text-xs text-gray-400">PREMIUM STORE</span>
        </div>
      </header>

      <section className="mx-auto max-w-6xl px-6 py-20 text-center">
        <p className="mb-4 text-sm font-bold tracking-[0.3em] text-yellow-500">
          ROYAL UC STORE
        </p>
        <h2 className="text-4xl font-black md:text-6xl">
          OYUNUNDA <span className="text-yellow-400">GÜCÜNÜ</span> ARTIR
        </h2>
        <p className="mx-auto mt-5 max-w-xl text-gray-400">
          PUBG Mobile Global UC mağazası. Premium alışveriş deneyimi
          ROYAL UC ile başlıyor.
        </p>
      </section>

      <section className="mx-auto grid max-w-6xl gap-8 px-6 pb-20 md:grid-cols-2">
        <div className="rounded-2xl border border-yellow-500/20 bg-[#141414] p-7">
          <h3 className="mb-6 text-2xl font-bold">UC Paketleri</h3>
          <div className="grid grid-cols-2 gap-3">
            {packages.map((item) => (
              <button
                key={item.uc}
                onClick={() => setSelected(item.uc)}
                className={`rounded-xl border p-5 text-left transition ${
                  selected === item.uc
                    ? "border-yellow-400 bg-yellow-400/10"
                    : "border-gray-700 bg-[#1b1b1b]"
                }`}
              >
                <span className="block text-xl font-black text-yellow-400">
                  {item.uc}
                </span>
                <span className="mt-2 block text-xs text-gray-400">
                  {item.price}
                </span>
              </button>
            ))}
          </div>
        </div>

        <div className="rounded-2xl border border-yellow-500/20 bg-[#141414] p-7">
          <h3 className="mb-2 text-2xl font-bold">Sipariş Oluştur</h3>
          <p className="mb-6 text-sm text-gray-400">
            Seçilen paket: {selected}
          </p>

          <label className="mb-2 block text-sm text-gray-300">
            PUBG Oyuncu ID
          </label>
          <input
            value={playerId}
            onChange={(e) => setPlayerId(e.target.value)}
            placeholder="Oyuncu ID bilgini gir"
            className="mb-5 w-full rounded-lg border border-gray-700 bg-black p-4 outline-none focus:border-yellow-400"
          />

          <label className="mb-2 block text-sm text-gray-300">
            Telefon veya e-posta
          </label>
          <input
            value={contact}
            onChange={(e) => setContact(e.target.value)}
            placeholder="İletişim bilgin"
            className="mb-6 w-full rounded-lg border border-gray-700 bg-black p-4 outline-none focus:border-yellow-400"
          />

          <button
            onClick={createOrder}
            className="w-full rounded-lg bg-yellow-400 p-4 font-black text-black transition hover:bg-yellow-300"
          >
            SİPARİŞ TALEBİ OLUŞTUR
          </button>

          {message && (
            <p className="mt-5 rounded-lg bg-black p-4 text-sm text-yellow-300">
              {message}
            </p>
          )}
        </div>
      </section>

      <footer className="border-t border-gray-800 px-6 py-8 text-center text-xs text-gray-500">
        ROYAL UC © 2026 — Bağımsız mağaza konsepti.
        PUBG Mobile ile resmi bağlantısı yoktur.
      </footer>
    </main>
  );
}
