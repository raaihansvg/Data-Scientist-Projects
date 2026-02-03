## Rangkuman Permasalahan
- Dataset terdiri dari 74.681 baris dan 4 kolom
- Dataset tidak terdapat nama kolom dan harus dilakukan penamaan pada kolom
- Kolom : 1. Tweet_Id
          2. Topic
          3. Sentiment
          4. Text
- Bahasa informal dan agresif : 1. i will kill you all
                                2. i will murder you all
                               |- kedua bahasa ini bukan ancaman, akan tetapi ekspresi emosi / slang

- Model harus memahami konteks, bukan literal kata
- Banyak variasi kalimat dengan makna yang sama, contoh  : 1. I am coming to the borders and I will kill you all
                                                           2. im getting on borderlands and i will murder you all
                                                           3. im getting into borderlands
                                                           |- 3 kata tsb termasuk paraphrase dan noise, dan cocok untuk
                                                           |- n-gram, TF-IDF
  - Sentimen tidak selalu sesuai, contoh ada kata kill dan murder di label positive
  - Dataset kontekstual, tidak bisa pake keywords sentiment biasa, negasi dan konteks game sangat dominan
  - ada data kosong: 1. Kolom text memiliki 686 baris NaN dan wajib dibersihkan atau di drop
  - Distribusi label : Positve, Negative, Neutral, Irrelevant
  - Label termasuk multi class, bukan binary accuracy tidak cukup anj, jadi pake f1 per class sama cf matrix
  - Masalah gede: Sarkasm dan hiperbola,kata kasar belum tentu negatif, negasi implisit seperti not bad, cant stop playing, topic bisa data leakage, class imbalance, duplicate semantics, banyak tweet beda teks tapi makna sama
    
Weakness NLP:
1. Train data Visual (mantepin lagi)
2. Train data cleaning khusus nya untuk regex,
