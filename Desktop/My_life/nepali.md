# Reading a kundali in Nepali

A Nepali kundali is the standard Parashari chart written in Devanagari, dated in Bikram Sambat (BS), timed by ishtakal, drawn in the North Indian diamond. Convert those three things and every rule in the other references applies.

## The cheena (चिना)
"That which identifies" a person. Prepared by a jyotishi or family purohit from birth date, time and place; tradition says within six days of birth, though many families have it written around age five. Families exchange cheenas for marriage matching (चिना मिलाउने). A typical cheena contains:
- BS date with month, paksha, tithi, vara (often also the Shaka year)
- Sunrise (सूर्योदय) and ishtakal (इष्टकाल) = birth moment in ghadi-pala after sunrise
- Birth nakshatra and pada (चरण/पाउ), yoga, karana
- Janma rashi (Moon sign) and janma lagna
- Graha spashta (ग्रह स्पष्ट): planet sign and degree table
- Lagna kundali, often Chandra kundali and Navamsa, in the North Indian diamond
- Vimshottari dasha balance (भोग्य दशा) and dasha dates in BS; sometimes Yogini dasha
- The nwaran name syllable from the nakshatra pada

When the user shares a cheena photo or PDF: read these values, rebuild the chart with `jyotish.py chart --bs ... --ishtakal ...` (or `--time`), and compare lagna, Moon nakshatra and planet degrees. Differences of a few minutes of arc are normal (different ayanamsa or sunrise rules); a different lagna means the time, sunrise or time zone is off — ask before trusting either.

Checks learned from real cheenas
- Handwritten cheenas often give both ishtakal and the clock time ("प्रचलित समयानुसार बेला १२।३० बजे"). If the two disagree by about 10 minutes, the astrologer probably took sunrise in local mean time (Nepal's west is 10–20 min behind NST) while the clock time was standard time. Prefer the recorded clock time and mention the alternative.
- Tithi, nakshatra and yoga end times written in ghadi-pala come from traditional (often Surya Siddhanta-style) panchangs and can differ from modern calculation by 1–2 ghadi. Matching to within that is a pass; check yoga and nakshatra-pada first, they are the most legible.
- The navamsa lagna changes every ~10–15 minutes and the D10 lagna every ~8–12. A cheena's "नवांश" that differs from the computed one only means the time is uncertain by a few minutes. Run `jyotish.py rectify --bs ... --start HH:MM --end HH:MM --place ...` to see the time window for each D9/D10 lagna, then rectify with past events. Planets' own D9 signs do not depend on the birth minute.
- Read digits carefully: handwritten ३ and ६, १ and ९ are easy to confuse; cross-check a doubtful number against the computed value before treating it as a mismatch.

## Dates and time
- Bikram Sambat is solar sidereal: a month starts when the Sun enters a sidereal sign (sankranti); months run 29–32 days. BS ≈ AD + 56 years 8 months. BS 2083 began on 14 April 2026 (Baisakh 1).
- The BS birth month gives the Sun sign (except near a sankranti):

| BS month | Sun in | BS month | Sun in |
|---|---|---|---|
| Baisakh (बैशाख) | Mesha | Kartik (कार्तिक) | Tula |
| Jestha (जेठ) | Vrisha | Mangsir (मंसिर) | Vrishchika |
| Asar (असार) | Mithuna | Poush (पुष) | Dhanu |
| Shrawan (साउन) | Karkata | Magh (माघ) | Makara |
| Bhadra (भदौ) | Simha | Falgun (फागुन) | Kumbha |
| Asoj (असोज) | Kanya | Chaitra (चैत) | Meena |

- Ishtakal → clock: 1 ghadi = 24 min, 1 pala = 24 s, 2½ ghadi = 1 hour. Clock time = sunrise + ishtakal. Example: 12 ghadi 30 pala after a 6:05 sunrise = 11:05. The cheena's own sunrise may differ from the computed one by a few minutes; if the cheena states sunrise, pass it with `--sunrise`.
- Time zone: Nepal used local mean time (+5:41:16) before 1920, UTC+5:30 from 1920, UTC+5:45 since 1986. The script's default zone Asia/Kathmandu applies these automatically.
- Festivals and tithis follow the lunar calendar fixed yearly by the Nepal Panchang Nirnayak Samiti (nine astrologers, two-year terms, under the culture ministry), which also approves printed patros.

## Reading the North Indian diamond
- Houses are fixed: top centre diamond = house 1 (lagna); houses run anticlockwise (2 top-left, 3 left-upper, 4 left centre, 5 left-lower, 6 bottom-left, 7 bottom centre, 8 bottom-right, 9 right-lower, 10 right centre, 11 right-upper, 12 top-right).
- The Devanagari number in a box is the sign in that house (१ = Mesha … १२ = Meena). The number in house 1 is the lagna sign.
- Planet abbreviations: सू Sun, चं Moon, मं Mars, बु Mercury, बृ/गु Jupiter, शु Venus, श Saturn, रा Rahu, के Ketu; (व) or "व" marks retrograde (वक्री).
- Devanagari digits: ० १ २ ३ ४ ५ ६ ७ ८ ९.

## Nepali terms
| Nepali | Roman | Meaning |
|---|---|---|
| जन्मकुण्डली, चिना | janmakundali, cheena | Birth chart |
| लग्न | lagna | Ascendant |
| राशि, जन्मराशि | rashi, janma rashi | Sign; Moon sign |
| ग्रह | graha | Planet |
| भाव, घर | bhava, ghar | House |
| नक्षत्र, चरण/पाउ | nakshatra, charan/pau | Lunar mansion, quarter |
| उच्च, नीच | uchcha, neech | Exalted, debilitated |
| स्वगृही | swagrihi | Own sign |
| मित्रक्षेत्री, शत्रुक्षेत्री | mitrakshetri, shatrukshetri | In friend's / enemy's sign |
| वक्री, अस्त | vakri, asta | Retrograde, combust |
| दृष्टि, युति | drishti, yuti | Aspect, conjunction |
| महादशा, अन्तर्दशा, प्रत्यन्तर | mahadasha, antardasha, pratyantar | Dasha levels |
| भोग्य दशा | bhogya dasha | Dasha balance at birth |
| गोचर | gochar | Transit |
| साढेसाती, ढैया | sadhesati, dhaiya | Saturn over the Moon |
| मङ्गलिक, मङ्गल दोष | manglik, mangal dosh | Mars dosha |
| कालसर्प योग | kalsarpa yog | Kaal Sarpa |
| गुण मिलान | gun milan | Matching score |
| ग्रहशान्ति, उपाय | grahashanti, upaya | Pacification, remedy |
| तिथि, वार, पक्ष | tithi, vaar, paksha | Lunar day, weekday, fortnight |
| शुक्ल / कृष्ण पक्ष | shukla / krishna paksha | Bright / dark fortnight |
| औंसी, पूर्णिमा | aunsi, purnima | New moon, full moon |
| शुभ, अशुभ | shubh, ashubh | Auspicious, inauspicious |
| योगकारक, मारक, बाधक | yogakarak, marak, badhak | Yogakaraka, maraka, badhaka |
| केन्द्र, त्रिकोण, त्रिक (दुःस्थान) | kendra, trikon, trik | Angles, trines, 6-8-12 |
| राजयोग, धनयोग | rajyog, dhanyog | Power, wealth combinations |

Weekdays: आइतबार, सोमबार, मङ्गलबार, बुधबार, बिहीबार, शुक्रबार, शनिबार. Planets: सूर्य, चन्द्र, मङ्गल, बुध, बृहस्पति (गुरु), शुक्र, शनि, राहु, केतु. Houses in Nepali speech: पहिलो घर … बाह्रौं घर; or तनु, धन, सहज, सुख, पुत्र, शत्रु, कलत्र, आयु, भाग्य, कर्म, लाभ, व्यय भाव.

## Rashi from a name's first syllable (Nepali rashifal)
| Rashi | Syllables |
|---|---|
| मेष | चु चे चो ला लि लु ले लो अ |
| वृष | इ उ ए ओ वा वि वु वे वो |
| मिथुन | का कि कु घ ङ छ के को ह |
| कर्कट | हि हु हे हो डा डि डु डे डो |
| सिंह | मा मि मु मे मो टा टि टु टे |
| कन्या | टो पा पि पु ष ण ठ पे पो |
| तुला | रा रि रु रे रो ता ति तु ते |
| वृश्चिक | तो ना नि नु ने नो या यि यु |
| धनु | ये यो भा भि भु धा फा ढा भे |
| मकर | भो जा जि खि खु खे खो गा गि |
| कुम्भ | गु गे गो सा सि सु से सो दा |
| मीन | दि दु थ झ ञ दे दो चा चि |
Valid only for a nwaran (nakshatra) name; otherwise use the Moon sign from the chart.

## Writing a reading in Nepali
Use plain Nepali with Sanskrit terms people know from patros; give English in brackets only when the user mixes languages. Useful sentence patterns:
- तपाईंको जन्म लग्न तुला हो र लग्नेश शुक्र दशौं घरमा छ। (Your lagna is Libra and its lord Venus is in the 10th.)
- चन्द्रमा वृष राशिमा उच्च/मूलत्रिकोणमा भएकाले मन स्थिर र भावुक रहन्छ।
- अहिले बृहस्पतिको महादशा र केतुको अन्तर्दशा चलिरहेको छ (मंसिर २०८३ सम्म)।
- यो अवधिमा करियरमा सकारात्मक परिवर्तनको सम्भावना बलियो देखिन्छ।
- शनिको गोचर चन्द्रमाबाट एघारौं घरमा भएकाले आम्दानी बढ्ने योग छ।
- उपायका रूपमा बिहीबार "ॐ ग्रां ग्रीं ग्रौं सः गुरवे नमः" १०८ पटक जप गर्न सकिन्छ।
- ज्योतिषीय संकेत मात्र हो; स्वास्थ्य वा आर्थिक निर्णयमा विशेषज्ञको सल्लाह लिनुहोस्।
Convert dasha and transit dates to BS when writing for Nepali readers (`jyotish.py convert --ad2bs YYYY-MM-DD`).

## Institutions
Nepal Sanskrit University (founded 1986, central office Dang) teaches Jyotish at Shastri (BA) and Acharya (MA) level in Siddhanta and Phalit streams, including at Valmiki Vidyapeeth, Kathmandu. Hamro Patro offers kundali generation and paid calls with Nepali astrologers.
