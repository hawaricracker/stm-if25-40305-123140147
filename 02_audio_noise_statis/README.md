Catatan Analisis Audio
Berkas
`audio_original.wav` — rekaman asli berita + noise (44100 Hz, ~16.7 detik)
`audio_downsampled_naive.wav` — hasil downsampling ke 8000 Hz tanpa anti-aliasing (decimation langsung, `audio[::M]`)
`audio_downsampled_clean.wav` — hasil downsampling ke 8000 Hz dengan anti-aliasing (`scipy.signal.resample_poly`)
Perangkat Rekaman
Sample rate asli: 44100 Hz
Jumlah sample: 737307
Durasi: 16.7190 detik
Rentang amplitudo: -0.6700 s.d. 0.7012
Sumber Noise
Dari analisis FFT pada segmen tanpa suara (0–2 detik dan 14.5–16 detik) dibandingkan segmen berisi suara (6–13 detik):
Noise statis terkonsentrasi di dua pita frekuensi: 0–1500 Hz dan 5000–10000 Hz, konsisten muncul di seluruh durasi rekaman (terlihat jelas di spektrogram STFT sebagai pita yang selalu menyala).
Suara manusia (berita) menempati pita 1500–5000 Hz.
Pola noise low-frequency yang terus-menerus dan cukup stabil ini (dominan di bawah ~1500 Hz, dengan komponen tambahan di 5000–10000 Hz) khas untuk noise kipas (fan noise) — mesin berputar menghasilkan noise broadband dengan energi kuat di frekuensi rendah, ditambah harmonik/turbulensi udara di frekuensi lebih tinggi.
Efek Downsampling
Naive decimation (tanpa filter anti-aliasing): pada spektrogram muncul artefak berupa magnitude tambahan di area frekuensi tinggi hasil pantulan (aliasing) dari komponen di atas Nyquist frequency baru (4000 Hz).
Resampling dengan anti-aliasing (`resample_poly`): area frekuensi tinggi tampak lebih bersih karena komponen di atas Nyquist sudah difilter sebelum di-downsample, sehingga tidak terjadi aliasing.
Kesimpulan Singkat
Noise dominan pada rekaman kemungkinan besar berasal dari kipas (fan) di lingkungan perekaman, ditandai energi kuat dan konsisten di frekuensi rendah (0–1500 Hz) sepanjang durasi audio, terpisah dari pita frekuensi suara manusia (1500–5000 Hz).
