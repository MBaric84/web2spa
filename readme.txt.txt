Pokretanje aplikacije:
- Development mode: npm run dev
- Production mode: npm run build && npm run preview
https://web2spa-ujob.onrender.com


1. interpolacija/jednosmjerno povezivanje - Da, src/components/Subjects.vue, linije 21-23, prikaz course.name, course.professor i course.credits u tablici

2. dvosmjerno povezivanje - Da, src/components/DetailsModal.vue, linije 16, 42, varijabla courseCredits povezana s formom preko v-model

3. metode - Da, src/components/Subjects.vue, linije 71-77, implementirane metode:
   - onDetails: za otvaranje modalnog prozora s detaljima predmeta
   - deleteCourse: definirana ali trenutno nije u upotrebi

4. computed svojstva - Da, src/components/Subjects.vue, linije 63-65, sumOfCredits koji automatski zbraja bodove predmeta

5. scoped style - Da, src/components/Subjects.vue, linije 82-117, lokalno stiliziranje tablice i komponenti

6. lifecycle hook - Da, src/components/Subjects.vue, linija 57-61, created() koji se pokreće pri inicijalizaciji komponente

7. usmjeravanje (više stranica) - Da, src/router/index.js, implementirane rute za navigaciju između stranica

8. bookmarkable aplikacija - Da, moguć direktan pristup na /about i ostale rute
   - dinamičko usmjeravanje s 404 stranicom - Da, src/router/index.js, hvata sve nepostojeće rute

9. komponente:
   - bez stanja - Da, src/components/DetailsModal.vue, radi samo s props
   - sa stanjem - Da, src/components/Subjects.vue, upravlja s selectedCourse i showModal

10. emitiranje događaja - Da, src/components/DetailsModal.vue, emitira 'close' događaj kod zatvaranja modala

11. store (Pinia) - Da, src/stores/courses.js, implementiran za upravljanje predmetima

12. asinkroni dohvat podataka - Da, src/stores/courses.js, fetchCourses funkcija dohvaća podatke s Mocky API-ja

