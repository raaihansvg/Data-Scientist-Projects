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
2. Train data cleaning khusus nya untuk regex (feature),fix missing values, fix target jika data rusak(Regex Implementation)
3. Modeling : 1. Tfidf (sebelum modeling)
              2. Model (Implementasi model dan pemilihan model)

refisi : ada missing values ketika cleaning di implementasi (netral sentiment mostly)

Debug Regex:
- dlvr. From it / e RMTrgF
- @ mompou _ mumpow (_ mumpow)
- @ mompou _ mumpow (_ mumpow)
- . twitch.tv/punnisenpai
- di baris 55 ada haven't ga ke handle : why does practically every man in France have slicked back hair haven’t you heard of bangs the greedy assholes (Sebelum), practically every man france slicked back hair heard bang greedy asshole (sesudah)
- buff. ly / to 2WmmiP5.. to Say
- di baris 86 ada wont't ga ke handle : I hate that this easy mayhem modifier event on mayhem won't last forever (sebelum), hate easy mayhem modifier event mayhem last forever (sesudah)
- di baris 87 ada wont't ga ke handle : I hate saying this easy day 9 event on mayhem won’t last forever (Sebelum), hate saying easy day event mayhem last forever(sesudah)
- di baris 88 ada wont't ga ke handle : I hate thinking that this easy mayhem modifier event on total mayhem won ’ t last forever (sebelum), hate thinking easy mayhem modifier event total mayhem last forever (sesudah)
- di baris 93,94,95 ada cant't ga ke handle : I really can’t wait for this shitty mod to die (sebelum), really wait shitty mod die (sesudah) -93, I really can ’ t wait for this shitty trend starting to... die(sebelum), really wait shitty trend starting die(sesudah) -94, I seriously can’t wait on this shitty trend to die(sebelum), seriously wait shitty trend die (sesudah)
- ada sentiment aneh di baris 142, miracle negatif
----- lanjut di baris 150

update = baris 15 	Live Rock - Hard music La la Varlope, RARE & the POWERFUL, Live HANDSOME i JACKPOT, Borderlands 3 ( Sega Xbox ) dlvr. From it / e RMTrgF (Sebelum), live rock hard music varlope rare powerful live handsome jackpot borderland sega xbox dlvr(sesudah)


