import React, { useState, useEffect } from 'react';

// --- Datová struktura pro celou aplikaci ---
// Kompletní obsah z PDF pro 12 lekcí
const appData = {
  lessons: [
    {
      id: 1,
      title: "1. lekce: Substantiva I. deklinace. Sloveso esse",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Substantiva I. deklinace</h3>
        <p class="mb-4">Podle I. deklinace se skloňují substantiva s kmenovou samohláskou <strong>-a</strong>. V nominativu sg. mají zakončení <strong>-a</strong>, v genitivu sg. <strong>-ae</strong>, většinou jsou <strong>feminina</strong>.</p>
        
        <h4 class="text-lg font-semibold mb-2">Vzor: vēna, ae, f. - žíla</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pád</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Singulár</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Plurál</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">vēn-a</td><td class="px-4 py-2">vēn-ae</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">vēn-ae</td><td class="px-4 py-2">vēn-ārum</td></tr>
            <tr><td class="px-4 py-2">3. Dat.</td><td class="px-4 py-2">vēn-ae</td><td class="px-4 py-2">vēn-īs</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">vēn-am</td><td class="px-4 py-2">vēn-ās</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">vēn-ā</td><td class="px-4 py-2">vēn-īs</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Řecká substantiva I. deklinace</h4>
        <ul class="list-disc list-inside mb-4">
          <li>Feminina na <strong>-a</strong>, gen. <strong>-ae</strong> (např. <i>pneumonia, ae, f.</i> - zápal plic)</li>
          <li>Feminina na <strong>-ē</strong>, gen. <strong>-ēs</strong> (např. <i>systolē, ēs, f.</i> - srdeční stah)</li>
          <li>Maskulina na <strong>-ēs</strong>, gen. <strong>-ae</strong> (např. <i>diabētēs, ae, m.</i> - cukrovka)</li>
        </ul>

        <h3 class="text-xl font-semibold mb-3 mt-6">Sloveso ESSE - být</h3>
        <h4 class="text-lg font-semibold mb-2">Indikativ prézenta</h4>
        <div class="flex space-x-8">
          <div>
            <h5 class="font-medium">Singulár</h5>
            <ul class="list-disc list-inside">
              <li>1. sum (jsem)</li>
              <li>2. es</li>
              <li>3. est</li>
            </ul>
          </div>
          <div>
            <h5 class="font-medium">Plurál</h5>
            <ul class="list-disc list-inside">
              <li>1. sumus</li>
              <li>2. estis</li>
              <li>3. sunt</li>
            </ul>
          </div>
        </div>
      `,
      vocabulary: [
        { latin: "ā, ab (předl. s abl.)", czech: "od" },
        { latin: "absum, abesse", czech: "být nepřítomen" },
        { latin: "ad (předl. s ak.)", czech: "k, do" },
        { latin: "adsum, adesse", czech: "být přítomen, pomáhat" },
        { latin: "akmē, ēs, f.", czech: "vrchol" },
        { latin: "-algia, ae, f.", czech: "bolest" },
        { latin: "anaemia, ae, f.", czech: "chudokrevnost, anémie" },
        { latin: "antagonista, ae, m.", czech: "činitel působící opačně" },
        { latin: "aorta, ae, f.", czech: "srdečnice, aorta" },
        { latin: "apud (předl. s ak.)", czech: "u, při" },
        { latin: "aqua, ae, f.", czech: "voda" },
        { latin: "āreola, ae, f.", czech: "dvorec" },
        { latin: "artēria, ae, f.", czech: "tepna" },
        { latin: "ascītēs, ae, m.", czech: "vodnatelnost" },
        { latin: "axilla, ae, f.", czech: "podpaží" },
        { latin: "bucca, ae, f.", czech: "tvář" },
        { latin: "cachexia, ae, f.", czech: "sešlost, vyhublost" },
        { latin: "calva, ae, f.", czech: "lebeční klenba" },
        { latin: "capsula, ae, f.", czech: "pouzdro, tobolka" },
        { latin: "cataracta, ae, f.", czech: "šedý oční zákal" },
        { latin: "cellula, ae, f.", czech: "buňka" },
        { latin: "cephalē, ēs, f.", czech: "hlava" },
        { latin: "circum (předl. s ak.)", czech: "kolem" },
        { latin: "clavicula, ae, f.", czech: "klíční kost" },
        { latin: "columna, ae, f.", czech: "sloup" },
        { latin: "columna vertebrārum", czech: "páteř" },
        { latin: "concha, ae, f.", czech: "skořepa" },
        { latin: "contrā (předl. s ak.)", czech: "proti" },
        { latin: "costa, ae, f.", czech: "žebro" },
        { latin: "coxa, ae, f.", czech: "kyčel, kyčelní kloub" },
        { latin: "cupula, ae, f.", czech: "kyčel" },
        { latin: "cum (předl. s abl.)", czech: "s, se" },
        { latin: "diabētēs, ae, m.", czech: "cukrovka" },
        { latin: "diastolē, ēs, f.", czech: "diastola" },
        { latin: "diphtheria, ae, f.", czech: "záškrt" },
        { latin: "dysenteria, ae, f.", czech: "úplavice" },
        { latin: "dyspnoē, ēs, f.", czech: "dušnost" },
        { latin: "ē, ex (předl. s abl.)", czech: "z, ze, zevnitř, podle" },
        { latin: "-ectomia, ae, f.", czech: "chirurgické vynětí" },
        { latin: "fascia, ae, f.", czech: "povázka" },
        { latin: "fibula, ae, f.", czech: "kost lýtková" },
        { latin: "fissura, ae, f.", czech: "rýha, štěrbina, rozštěp" },
        { latin: "flexūra, ae, f.", czech: "ohyb" },
        { latin: "fossa, ae, f.", czech: "jamka, vyhloubenina" },
        { latin: "frāctūra, ae, f.", czech: "zlomenina" },
        { latin: "gangraena, ae, f.", czech: "sněť, gangréna" },
        { latin: "gingīva, ae, f.", czech: "dáseň" },
        { latin: "glandula, ae, f.", czech: "žláza" },
        { latin: "gutta, ae, f.", czech: "kapka" },
        { latin: "haemorrhagia, ae, f.", czech: "krvácení" },
        { latin: "herba, ae, f.", czech: "bylina, nať" },
        { latin: "hōra, ae, f.", czech: "hodina" },
        { latin: "in (předl. s ak./abl.)", czech: "do, na, v" },
        { latin: "incīsūra, ae, f.", czech: "zářez, rýha" },
        { latin: "incontinentia, ae, f.", czech: "neschopnost udržet moč" },
        { latin: "īnfluenza, ae, f.", czech: "chřipka" },
        { latin: "īnsufficientia, ae, f.", czech: "nedostatečnost, selhání" },
        { latin: "inter (předl. s ak.)", czech: "mezi" },
        { latin: "intumescentia, ae, f.", czech: "ztluštění, zduření" },
        { latin: "lagoena, ae, f.", czech: "láhev" },
        { latin: "lingua, ae, f.", czech: "jazyk" },
        { latin: "lympha, ae, f.", czech: "míza" },
        { latin: "mandibula, ae, f.", czech: "dolní čelist" },
        { latin: "mamma, ae, f.", czech: "prs, prsní žláza" },
        { latin: "massa, ae, f.", czech: "hmota" },
        { latin: "maxilla, ae, f.", czech: "horní čelist" },
        { latin: "membrāna, ae, f.", czech: "membrána, blána" },
        { latin: "mixtūra, ae, f.", czech: "směs" },
        { latin: "mora, ae, f.", czech: "prodlení, zdržení" },
        { latin: "olla, ae, f.", czech: "kelímek" },
        { latin: "paraplēgia, ae, f.", czech: "ochrnutí dolních končetin" },
        { latin: "patella, ae, f.", czech: "čéška" },
        { latin: "-pathia, ae, f.", czech: "blíže neurčená choroba" },
        { latin: "peronē, ēs, f.", czech: "lýtko, kost lýtková" },
        { latin: "phlegmonē, ēs, f.", czech: "neohraničený hnisavý zánět" },
        { latin: "pilula, ae, f.", czech: "pilulka" },
        { latin: "pleura, ae, f.", czech: "pohrudnice" },
        { latin: "plica, ae, f.", czech: "řasa" },
        { latin: "pneumonia, ae, f.", czech: "zápal plic" },
        { latin: "possum, posse", czech: "moci" },
        { latin: "post (předl. s ak.)", czech: "po, za" },
        { latin: "porta, ae, f.", czech: "brána, průchod" },
        { latin: "propter (předl. s ak.)", czech: "kvůli" },
        { latin: "prōsum, prōdesse", czech: "prospívat" },
        { latin: "pulpa, ae, f.", czech: "dřeň" },
        { latin: "rhaphē, ēs, f.", czech: "šev" },
        { latin: "rubeola, ae, f.", czech: "zarděnky" },
        { latin: "ruptūra, ae, f.", czech: "prasklina, trhlina" },
        { latin: "scapula, ae, f.", czech: "lopatka" },
        { latin: "scarlatina, ae, f.", czech: "spála" },
        { latin: "scatula, ae, f.", czech: "krabička" },
        { latin: "secundum (předl. s ak.)", czech: "podle" },
        { latin: "sine (předl. s abl.)", czech: "bez" },
        { latin: "spīna, ae, f.", czech: "trn, hřeben" },
        { latin: "sub (předl. s ak./abl.)", czech: "pod" },
        { latin: "sum, esse", czech: "být" },
        { latin: "suprā (předl. s ak.)", czech: "nad" },
        { latin: "sūra, ae, f.", czech: "lýtko" },
        { latin: "sūtūra, ae, f.", czech: "šev" },
        { latin: "systolē, ēs, f.", czech: "systola, stah srdce" },
        { latin: "tabuletta, ae, f.", czech: "tableta" },
        { latin: "tēla, ae, f.", czech: "tkáň" },
        { latin: "therapia, ae, f.", czech: "léčba" },
        { latin: "tībia, ae, f.", czech: "kost holenní" },
        { latin: "tīnctūra, ae, f.", czech: "tinktura" },
        { latin: "tōnsilla, ae, f.", czech: "mandle" },
        { latin: "trachea, ae, f.", czech: "průdušnice" },
        { latin: "tunica, ae, f.", czech: "vrstva, obal, stěna" },
        { latin: "ulna, ae, f.", czech: "kost loketní" },
        { latin: "urēthra, ae, f.", czech: "močová trubice" },
        { latin: "ūvula, ae, f.", czech: "čípek (v hrdle)" },
        { latin: "valvula (valva), ae, f.", czech: "chlopeň" },
        { latin: "varicella, ae, f.", czech: "plané neštovice" },
        { latin: "vēna, ae, f.", czech: "žíla" },
        { latin: "vēna portae", czech: "vrátnice" },
        { latin: "vertebra, ae, f.", czech: "obratel" },
        { latin: "vēsīca, ae, f.", czech: "měchýř" },
        { latin: "via, ae, f.", czech: "cesta" },
        { latin: "vīta, ae, f.", czech: "život" },
      ],
      practice: [],
    },
    {
      id: 2,
      title: "2. lekce: Substantiva II. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Substantiva II. deklinace</h3>
        <p class="mb-4">Substantiva II. deklinace mají kmen zakončený na <strong>-o</strong>. Většinou jsou to <strong>maskulina</strong> nebo <strong>neutra</strong>. V nominativu sg. mají maskulina zakončení <strong>-us</strong> nebo <strong>-er</strong>, neutra <strong>-um</strong>. V genitivu sg. mají všechna substantiva II. deklinace koncovku <strong>-ī</strong>.</p>
        
        <h4 class="text-lg font-semibold mb-2">Vzor: nervus, ī, m. - nerv</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pád</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Singulár</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Plurál</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">nerv-us</td><td class="px-4 py-2">nerv-ī</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">nerv-ī</td><td class="px-4 py-2">nerv-ōrum</td></tr>
            <tr><td class="px-4 py-2">3. Dat.</td><td class="px-4 py-2">nerv-ō</td><td class="px-4 py-2">nerv-īs</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">nerv-um</td><td class="px-4 py-2">nerv-ōs</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">nerv-ō</td><td class="px-4 py-2">nerv-īs</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Vzor: palātum, ī, n. - patro</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pád</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Singulár</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Plurál</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">palāt-um</td><td class="px-4 py-2">palāt-a</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">palāt-ī</td><td class="px-4 py-2">palāt-ōrum</td></tr>
            <tr><td class="px-4 py-2">3. Dat.</td><td class="px-4 py-2">palāt-ō</td><td class="px-4 py-2">palāt-īs</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">palāt-um</td><td class="px-4 py-2">palāt-a</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">palāt-ō</td><td class="px-4 py-2">palāt-īs</td></tr>
          </tbody>
        </table>
        
        <h4 class="text-lg font-semibold mb-2">Řecká substantiva</h4>
        <ul class="list-disc list-inside mb-4">
          <li>Maskulina na <strong>-os</strong>, gen. <strong>-ī</strong> (např. <i>spondylos, ī, m.</i> - obratel).</li>
          <li>Neutra na <strong>-on</strong>, gen. <strong>-ī</strong> (např. <i>neuron, ī, n.</i> - nerv).</li>
        </ul>
      `,
      vocabulary: [
        { latin: "acetabulum, ī, n.", czech: "jamka kyčelního kloubu" },
        { latin: "acidum, ī, n.", czech: "kyselina" },
        { latin: "acromion, iī, n.", czech: "nadpažek" },
        { latin: "adultus, ī, m.", czech: "dospělý" },
        { latin: "aegrotus, ī, m.", czech: "nemocný" },
        { latin: "alveolus, ī, m.", czech: "sklípek, zubní lůžko" },
        { latin: "angulus, ī, m.", czech: "úhel" },
        { latin: "ante (předl. s ak.)", czech: "před" },
        { latin: "antebrachium, iī, n.", czech: "předloktí" },
        { latin: "arthron, ī, n.", czech: "kloub, článek" },
        { latin: "articulus, ī, m.", czech: "kloub" },
        { latin: "ātrium, iī, n.", czech: "síň, předsíň" },
        { latin: "brachium, iī, n.", czech: "paže" },
        { latin: "cancer, crī, m.", czech: "rakovina" },
        { latin: "capitulum, ī, n.", czech: "hlavička" },
        { latin: "carpus, ī, m.", czech: "zápěstí" },
        { latin: "causa, ae, f.", czech: "příčina" },
        { latin: "cavum, ī, n.", czech: "dutina" },
        { latin: "cerebrum, ī, n.", czech: "mozek" },
        { latin: "cibus, ī, m.", czech: "jídlo" },
        { latin: "colon, ī, n.", czech: "tračník" },
        { latin: "collum, ī, n.", czech: "krk, krček, šíje" },
        { latin: "cranium, ī, n.", czech: "lebka" },
        { latin: "cubitus, ī, m.", czech: "loket" },
        { latin: "daktylos, ī, m.", czech: "prst" },
        { latin: "digitus, ī, m.", czech: "prst" },
        { latin: "dorsum, ī, n.", czech: "hřbet, záda" },
        { latin: "duodēnum, ī, n.", czech: "dvanáctník" },
        { latin: "emplastrum, ī, n.", czech: "náplast" },
        { latin: "encephalos, ī, m.", czech: "mozek" },
        { latin: "extractum, ī, n.", czech: "výtažek" },
        { latin: "fundus, ī, m.", czech: "dno" },
        { latin: "ganglion, ī, n.", czech: "nervová uzlina" },
        { latin: "gyrus, ī, m.", czech: "závit" },
        { latin: "hīlus, ī, m. (hīlum, ī, n.)", czech: "branka" },
        { latin: "humerus, ī, m.", czech: "kost pažní" },
        { latin: "icterus, ī, m.", czech: "žloutenka" },
        { latin: "ičiūnum, ī, n.", czech: "lačník" },
        { latin: "īleum, ī, n.", czech: "kyčelník" },
        { latin: "īleus, ī, m.", czech: "střevní neprůchodnost" },
        { latin: "intestīnum, ī, n.", czech: "střevo" },
        { latin: "isthmus, ī, m.", czech: "zúžené místo" },
        { latin: "labium, iī, n.", czech: "ret, pysk" },
        { latin: "līberī, ōrum, m. (pl.)", czech: "děti" },
        { latin: "ligāmentum, ī, n.", czech: "vaz" },
        { latin: "lobus, ī, m.", czech: "lalok" },
        { latin: "locus, ī, m.", czech: "místo" },
        { latin: "malleolus, ī, m.", czech: "kotník" },
        { latin: "medicamentum, ī, n.", czech: "lék" },
        { latin: "medulla, ae, f.", czech: "dřeň, mícha" },
        { latin: "membrum, ī, n.", czech: "končetina" },
        { latin: "mentum, ī, n.", czech: "brada" },
        { latin: "metatarsus, ī, m.", czech: "nárt" },
        { latin: "methodus, ī, f.", czech: "metoda" },
        { latin: "morbillī, ōrum, m. (pl.)", czech: "spalničky" },
        { latin: "morbus, ī, m.", czech: "nemoc" },
        { latin: "mūsculus, ī, m.", czech: "sval" },
        { latin: "nāsus, ī, m.", czech: "nos" },
        { latin: "neonātus, ī, m.", czech: "novorozenec" },
        { latin: "nephros, ī, m.", czech: "ledvina" },
        { latin: "nervus, ī, m.", czech: "nerv" },
        { latin: "neuron, ī, n.", czech: "nerv" },
        { latin: "nucleus, ī, m.", czech: "jádro" },
        { latin: "oculus, ī, m.", czech: "oko" },
        { latin: "oesophagus, ī, m.", czech: "jícen" },
        { latin: "ōlecranon, ī, n.", czech: "loketní výběžek" },
        { latin: "oleum, ī, n.", czech: "olej" },
        { latin: "ophthalmos, ī, m.", czech: "oko" },
        { latin: "orbita, ae, f.", czech: "očnice" },
        { latin: "orgănon / orgănum, ī, n.", czech: "orgán" },
        { latin: "osteon, ī, n.", czech: "kost" },
        { latin: "ōvārium, ī, n.", czech: "vaječník" },
        { latin: "per (předl. s ak.)", czech: "skrz, přes, během" },
        { latin: "perīculum, ī, n.", czech: "nebezpečí" },
        { latin: "periodus, ī, f.", czech: "období" },
        { latin: "pharmacon, ī, n.", czech: "lék" },
        { latin: "pylōrus, ī, m.", czech: "vrátník" },
        { latin: "radius, iī, m.", czech: "kost vřetenní" },
        { latin: "rāmus, ī, m.", czech: "větev, rameno" },
        { latin: "rēctum, ī, n.", czech: "konečník" },
        { latin: "remedium, ī, n.", czech: "lék" },
        { latin: "retināculum, ī, n.", czech: "šlachový vaz" },
        { latin: "sēptum, ī, n.", czech: "přepážka" },
        { latin: "signum, ī, n.", czech: "označení, příznak" },
        { latin: "spasmus, ī, m.", czech: "křeč" },
        { latin: "spondylos, ī, m.", czech: "obratel" },
        { latin: "sternum, ī, n.", czech: "kost hrudní" },
        { latin: "stomachus, ī, m.", czech: "žaludek" },
        { latin: "sulcus, ī, m.", czech: "rýha, žlábek" },
        { latin: "suppositorium, ī, n.", czech: "čípek" },
        { latin: "talus, ī, m.", czech: "kost hlezenní" },
        { latin: "tarsus, ī, m.", czech: "zánártí" },
        { latin: "truncus, ī, m.", czech: "trup, kmen" },
        { latin: "tūberculum, ī, n.", czech: "hrbolek" },
        { latin: "unguentum, ī, n.", czech: "mast" },
        { latin: "uterus, ī, m.", czech: "děloha" },
        { latin: "vaselīnum, ī, n.", czech: "vazelína" },
        { latin: "venēnum, ī, n.", czech: "jed" },
        { latin: "ventriculus, ī, m.", czech: "žaludek, komora" },
        { latin: "vestibulum, ī, n.", czech: "předsíň" },
        { latin: "vīrus, ī, n.", czech: "nákazová látka, jed" },
        { latin: "vitium, ī, n.", czech: "vada" },
        { latin: "vitrum, ī, n.", czech: "zkumavka, lahvička" },
      ],
      practice: [],
    },
    {
      id: 3,
      title: "3. lekce: Adjektiva I. a II. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Adjektiva I. a II. deklinace</h3>
        <p class="mb-4">Adjektiva I. a II. deklinace jsou trojvýchodná, mají v nominativu sg. pro každý rod zvláštní tvar. Skloňují se podle vzorů substantiv I. a II. deklinace.</p>
        <ul class="list-disc list-inside mb-4">
          <li>Maskulina: <strong>-us</strong> (např. <i>longus</i>) nebo <strong>-er</strong> (např. <i>dexter, niger, līber</i>)</li>
          <li>Feminina: <strong>-a</strong> (např. <i>longa</i>) nebo <strong>-ra</strong> (např. <i>dextra, nigra</i>), <strong>-era</strong> (např. <i>lībera</i>)</li>
          <li>Neutra: <strong>-um</strong> (např. <i>longum</i>) nebo <strong>-rum</strong> (např. <i>dextrum, nigrum</i>), <strong>-erum</strong> (např. <i>līberum</i>)</li>
        </ul>
        <p class="mb-4">Adjektivum se shoduje se substantivem v rodě, čísle a pádě. V latině stojí většinou za substantivem (např. <i>mūsculus longus</i>).</p>

        <h4 class="text-lg font-semibold mb-2">Příklad skloňování: vēna longa (dlouhá žíla)</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pád</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Singulár</th>
              <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Plurál</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">vēn-a long-a</td><td class="px-4 py-2">vēn-ae long-ae</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">vēn-ae long-ae</td><td class="px-4 py-2">vēn-ārum long-ārum</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">vēn-am long-am</td><td class="px-4 py-2">vēn-ās long-ās</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">vēn-ā long-ā</td><td class="px-4 py-2">vēn-īs long-īs</td></tr>
          </tbody>
        </table>

        <h3 class="text-xl font-semibold mb-3 mt-6">Participium perfekta pasiva</h3>
        <p class="mb-4">Skloňuje se jako adjektiva I. a II. deklinace. Vyjadřuje vlastnost nabytou dějem v minulosti. Končí na:</p>
        <ul class="list-disc list-inside mb-4">
          <li><strong>-tus, -ta, -tum</strong> (např. <i>perforātus</i> - prasklý)</li>
          <li><strong>-sus, -sa, -sum</strong> (např. <i>laesus</i> - poškozený)</li>
        </ul>

        <h3 class="text-xl font-semibold mb-3 mt-6">Adverbia (Příslovce)</h3>
        <p class="mb-4">Tvoří se od kmene adjektiva (z gen. sg.) příponou <strong>-ē</strong>.</p>
        <ul class="list-disc list-inside mb-4">
          <li><i>exāctus, a, um</i> (přesný) -> <i>exāct-ē</i> (přesně)</li>
          <li><i>bonus, a, um</i> (dobrý) -> <i>bene</i> (dobře)</li>
          <li><i>malus, a, um</i> (špatný) -> <i>male</i> (špatně)</li>
        </ul>
      `,
      vocabulary: [
        { latin: "acquīsītus, a, um", czech: "získaný" },
        { latin: "acutus, a, um", czech: "prudký" },
        { latin: "adnexa, ōrum, n. (pl.)", czech: "děložní přívěsky" },
        { latin: "albus, a, um", czech: "bílý" },
        { latin: "apertus, a, um", czech: "otevřený" },
        { latin: "aponeuroticus, a, um", czech: "týkající se ploché šlachy" },
        { latin: "azygos, on", czech: "nepárový" },
        { latin: "bene", czech: "dobře" },
        { latin: "benīgnus, a, um", czech: "nezhoubný" },
        { latin: "bīlifer, era, erum", czech: "žlučovodný" },
        { latin: "bonus, a, um", czech: "dobrý" },
        { latin: "caecum, ī, n.", czech: "slepe střevo" },
        { latin: "caecus, a, um", czech: "slepý" },
        { latin: "calidus, a, um", czech: "teplý" },
        { latin: "cavus, a, um", czech: "dutý" },
        { latin: "circumflexus, a, um", czech: "ohnutý" },
        { latin: "citō", czech: "rychle" },
        { latin: "complicātus, a, um", czech: "komplikovaný" },
        { latin: "congenitus, a, um", czech: "vrozený" },
        { latin: "contagiosus, a, um", czech: "nakažlivý" },
        { latin: "corōnārius, a, um", czech: "věnčitý" },
        { latin: "crassus, a, um", czech: "tlustý" },
        { latin: "criticus, a, um", czech: "rozhodný, kritický" },
        { latin: "cruciātus, a, um", czech: "zkřížený" },
        { latin: "dēstillātus, a, um", czech: "destilovaný" },
        { latin: "dexter, tra, trum", czech: "pravý" },
        { latin: "dūrus, a, um", czech: "tvrdý" },
        { latin: "externus, a, um", czech: "vnější" },
        { latin: "felleus, a, um", czech: "žlučový" },
        { latin: "frīgidus, a, um", czech: "chladný, studený" },
        { latin: "fuscus, a, um", czech: "tmavý, hnědý" },
        { latin: "grīseus, a, um", czech: "šedý" },
        { latin: "hepaticus, a, um", czech: "jaterní" },
        { latin: "chronicus, a, um", czech: "chronický, vleklý" },
        { latin: "idiopathicus, a, um", czech: "vzniklý z neznámé příčiny" },
        { latin: "internus, a, um", czech: "vnitřní" },
        { latin: "interosseus, a, um", czech: "mezikostní" },
        { latin: "intimus, a, um", czech: "nejvnitřnější" },
        { latin: "ischiadicus, a, um", czech: "sedací" },
        { latin: "lacer, era, erum", czech: "tržný" },
        { latin: "laesus, a, um", czech: "poškozený" },
        { latin: "lātus, a, um", czech: "široký" },
        { latin: "līber, era, erum", czech: "volný" },
        { latin: "longus, a, um", czech: "dlouhý" },
        { latin: "lymphaticus, a, um", czech: "lymfatický, mízní" },
        { latin: "magnus, a, um", czech: "velký" },
        { latin: "male", czech: "špatně" },
        { latin: "malignus, a, um", czech: "zhoubný" },
        { latin: "malus, a, um", czech: "špatný, zlý" },
        { latin: "medius, a, um", czech: "střední" },
        { latin: "medulla oblongāta", czech: "prodloužená mícha" },
        { latin: "mūcōsa, ae, f. (tunica)", czech: "sliznice" },
        { latin: "mūcōsus, a, um", czech: "slizký" },
        { latin: "multus, a, um", czech: "mnohý" },
        { latin: "niger, gra, grum", czech: "černý" },
        { latin: "nōdus, ī, m.", czech: "uzlina, uzlík" },
        { latin: "obliquus, a, um", czech: "šikmý" },
        { latin: "oblongātus, a, um", czech: "prodloužený" },
        { latin: "ōviger, era, erum", czech: "vejcovodný" },
        { latin: "palātīnus, a, um", czech: "patrový" },
        { latin: "parvus, a, um", czech: "malý" },
        { latin: "perforātus, a, um", czech: "prasklý" },
        { latin: "poplīteus, a, um", czech: "podkolenní" },
        { latin: "postoperatīvus, a, um", czech: "pooperační" },
        { latin: "profundus, a, um", czech: "hluboký" },
        { latin: "proprius, a, um", czech: "vlastní" },
        { latin: "rēctus, a, um", czech: "přímý, rovný" },
        { latin: "sānātus, a, um", czech: "vyléčený, zhojený" },
        { latin: "saphēnus, a, um", czech: "povrchový" },
        { latin: "sartorius, a, um", czech: "krejčovský" },
        { latin: "siccus, a, um", czech: "suchý" },
        { latin: "sinister, tra, trum", czech: "levý" },
        { latin: "squamosus, a, um", czech: "šupinový" },
        { latin: "thōrācicus, a, um", czech: "hrudní" },
        { latin: "thyroïdeus, a, um", czech: "štítný" },
        { latin: "transversus, a, um", czech: "příčný" },
        { latin: "tuba uterīna", czech: "vejcovod" },
        { latin: "tunica mūcōsa", czech: "sliznice" },
        { latin: "ūrīnārius, a, um", czech: "močový" },
        { latin: "uterīnus, a, um", czech: "děložní" },
        { latin: "valgus, a, um", czech: "vbočený" },
        { latin: "vārus, a, um", czech: "vybočený" },
        { latin: "vēnōsus, a, um", czech: "žilní" },
        { latin: "vērus, a, um", czech: "pravý" },
        { latin: "vēsīca fellea", czech: "žlučník" },
        { latin: "vēsīca ūrīnāria", czech: "močový měchýř" },
      ],
      practice: [],
    },
    {
      id: 4,
      title: "4. lekce: Slovesa I. - IV. konjugace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Slovesa I. - IV. konjugace</h3>
        <p class="mb-4">Latinská slovesa se dělí do 4 konjugací podle zakončení infinitivu prézenta:</p>
        <ul class="list-disc list-inside mb-4">
          <li><strong>I. konjugace:</strong> -āre (např. <i>sānāre</i> - léčit)</li>
          <li><strong>II. konjugace:</strong> -ēre (např. <i>vidēre</i> - vidět)</li>
          <li><strong>III. konjugace:</strong> -ere (např. <i>scrībere</i> - psát)</li>
          <li><strong>IV. konjugace:</strong> -īre (např. <i>audīre</i> - slyšet)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Indikativ prézenta aktiva (příklad I. konj.)</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2"></th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. os.</td><td class="px-4 py-2">sān-ō (léčím)</td><td class="px-4 py-2">sān-āmus</td></tr>
            <tr><td class="px-4 py-2">2. os.</td><td class="px-4 py-2">sān-ās</td><td class="px-4 py-2">sān-ātis</td></tr>
            <tr><td class="px-4 py-2">3. os.</td><td class="px-4 py-2">sān-at</td><td class="px-4 py-2">sān-ant</td></tr>
          </tbody>
        </table>
        
        <h4 class="text-lg font-semibold mb-2">Indikativ prézenta pasiva (příklad I. konj.)</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2"></th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. os.</td><td class="px-4 py-2">sān-or (jsem léčen)</td><td class="px-4 py-2">sān-āmur</td></tr>
            <tr><td class="px-4 py-2">2. os.</td><td class="px-4 py-2">sān-āris</td><td class="px-4 py-2">sān-āminī</td></tr>
            <tr><td class="px-4 py-2">3. os.</td><td class="px-4 py-2">sān-ātur</td><td class="px-4 py-2">sān-antur</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Imperativ (rozkaz)</h4>
        <ul class="list-disc list-inside mb-4">
          <li><i>sānā!</i> (léč!), <i>sānāte!</i> (léčte!)</li>
          <li>Zápor: <i>nōlī sānāre!</i> (neléč!), <i>nōlīte sānāre!</i> (neléčte!)</li>
        </ul>

        <h3 class="text-xl font-semibold mb-3 mt-6">Konjunktiv prézenta</h3>
        <p class="mb-4">Vyjadřuje přání nebo výzvu ("ať..."). Znakem je <strong>-e-</strong> u I. konj. a <strong>-a-</strong> u ostatních.</p>
        <ul class="list-disc list-inside mb-4">
          <li><i>sān-e-m</i> (ať léčím), <i>sān-e-t</i> (ať léčí)</li>
          <li><i>vide-a-m</i> (ať vidím), <i>vide-a-t</i> (ať vidí)</li>
          <li><i>fiat</i> (ať vznikne), <i>fiant</i> (ať vzniknou) - např. <i>Miscē, fiant suppositoria.</i> (Míchej, ať vzniknou čípky.)</li>
          <li><i>dētur!</i> (ať je dán!), <i>expediantur!</i> (ať jsou vydány!)</li>
        </ul>
      `,
      vocabulary: [
        { latin: "addō, ere", czech: "přidávat" },
        { latin: "adhibeō, ēre", czech: "užívat" },
        { latin: "agitō, āre", czech: "protřepat" },
        { latin: "aperiō, īre", czech: "otevírat" },
        { latin: "audiō, īre", czech: "slyšet" },
        { latin: "auscultō, āre", czech: "vyšetřovat poslechem" },
        { latin: "coquō, ere", czech: "vařit" },
        { latin: "cūrō, āre", czech: "ošetřovat, léčit" },
        { latin: "dēstillō, āre", czech: "destilovat" },
        { latin: "dignōscō, ere", czech: "rozpoznávat" },
        { latin: "dīvidō, ere", czech: "rozdělovat" },
        { latin: "dō, dare", czech: "dávat" },
        { latin: "examinō, āre", czech: "zkoušet, vyšetřovat" },
        { latin: "expediō, īre", czech: "vydávat" },
        { latin: "extrahō, ere", czech: "vytahovat" },
        { latin: "faciō, ere", czech: "dělat, působit" },
        { latin: "fluidus, a, um", czech: "tekutý" },
        { latin: "īnfūsum, ī, n.", czech: "nálev" },
        { latin: "iterō, āre", czech: "opakovat" },
        { latin: "magister, trī, m.", czech: "lékárník" },
        { latin: "medicus, ī, m.", czech: "lékař" },
        { latin: "misceō, ēre", czech: "míchat" },
        { latin: "nōminō, āre", czech: "jmenovat, nazývat" },
        { latin: "nutriō, īre", czech: "živit" },
        { latin: "observō, āre", czech: "zkoumat, pozorovat" },
        { latin: "ophthalmicus, a, um", czech: "oční" },
        { latin: "palpō, āre", czech: "vyšetřovat pohmatem" },
        { latin: "parō, āre", czech: "připravovat" },
        { latin: "praeparātum ī, n.", czech: "přípravek" },
        { latin: "praescrībō, ere", czech: "předepisovat" },
        { latin: "quantum satis (q. s.)", czech: "podle potřeby" },
        { latin: "recipiō, ere (Rp.)", czech: "brát, vezmi" },
        { latin: "repetō, ere", czech: "opakovat" },
        { latin: "sānō, āre", czech: "léčit" },
        { latin: "sēparō, āre", czech: "oddělovat" },
        { latin: "servō, āre", czech: "uchovávat" },
        { latin: "signō, āre", czech: "označovat" },
        { latin: "solūtiō, iōnis, f.", czech: "roztok" },
        { latin: "spīrō, āre", czech: "dýchat" },
        { latin: "stō, āre", czech: "stát" },
        { latin: "stomachicus, a, um", czech: "žaludeční" },
        { latin: "sūmō, ere", czech: "brát, užívat" },
        { latin: "videō, ēre", czech: "vidět" },
      ],
      practice: [],
    },
    {
      id: 5,
      title: "5. lekce: Substantiva IV. a V. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Substantiva IV. deklinace</h3>
        <p class="mb-4">Mají kmenovou samohlásku <strong>-u</strong>. Genitiv singuláru končí na <strong>-ūs</strong>.</p>
        <ul class="list-disc list-inside mb-4">
          <li>Maskulina: Nom. sg. <strong>-us</strong> (např. <i>processus, ūs, m.</i> - výběžek)</li>
          <li>Neutra: Nom. sg. <strong>-ū</strong> (např. <i>genū, ūs, n.</i> - koleno)</li>
          <li>Výjimky (feminina): <i>manus, ūs, f.</i> (ruka), <i>acus, ūs, f.</i> (jehla)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Vzor: processus, ūs, m.</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">process-us</td><td class="px-4 py-2">process-ūs</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">process-ūs</td><td class="px-4 py-2">process-uum</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">process-um</td><td class="px-4 py-2">process-ūs</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">process-ū</td><td class="px-4 py-2">process-ibus</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Vzor: genū, ūs, n.</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">gen-ū</td><td class="px-4 py-2">gen-ua</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">gen-ūs</td><td class="px-4 py-2">gen-uum</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">gen-ū</td><td class="px-4 py-2">gen-ua</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">gen-ū</td><td class="px-4 py-2">gen-ibus</td></tr>
          </tbody>
        </table>

        <h3 class="text-xl font-semibold mb-3 mt-6">Substantiva V. deklinace</h3>
        <p class="mb-4">Jsou to feminina s kmenovou samohláskou <strong>-e</strong>.</p>
        <ul class="list-disc list-inside mb-4">
          <li>Nom. sg. <strong>-ēs</strong>, Gen. sg. <strong>-ēī</strong> (nebo <strong>-eī</strong>).</li>
          <li>Např. <i>diēs, ēī, m.</i> (den - výjimka, maskulinum), <i>rēs, reī, f.</i> (věc), <i>faciēs, ēī, f.</i> (plocha, tvář), <i>speciēs, ēī, f.</i> (druh, čajová směs).</li>
        </ul>
        
        <h4 class="text-lg font-semibold mb-2">Vzor: diēs, ēī, m.</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">di-ēs</td><td class="px-4 py-2">di-ēs</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">di-ēī</td><td class="px-4 py-2">di-ērum</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">di-em</td><td class="px-4 py-2">di-ēs</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">di-ē</td><td class="px-4 py-2">di-ēbus</td></tr>
          </tbody>
        </table>
      `,
      vocabulary: [
        { latin: "abortus, ūs, m.", czech: "potrat" },
        { latin: "abscesus, ūs, m.", czech: "absces, hlíza" },
        { latin: "acus, ūs, f.", czech: "jehla" },
        { latin: "acūsticus, a, um", czech: "zvukový" },
        { latin: "apparātus, ūs, m.", czech: "ústrojí, soustava" },
        { latin: "arcus, ūs, m.", czech: "oblouk" },
        { latin: "audītus, ūs, m.", czech: "sluch" },
        { latin: "cariēs, ēī, f.", czech: "kaz, zánět kosti" },
        { latin: "cāsus, ūs, m.", czech: "případ, pád" },
        { latin: "choledochus, ī, m.", czech: "žlučovod" },
        { latin: "circulātōrius, a, um", czech: "oběhový" },
        { latin: "collāpsus, ūs, m.", czech: "zhroucení, kolaps" },
        { latin: "cornu, ūs, n.", czech: "roh, cíp" },
        { latin: "dēcubitus, ūs, m.", czech: "proleženina" },
        { latin: "dēcursus, ūs, m.", czech: "průběh" },
        { latin: "defectus, ūs, m.", czech: "defekt, vada" },
        { latin: "diēs, ēī, m. (f.)", czech: "den" },
        { latin: "dīgestōrius, a, um", czech: "trávicí" },
        { latin: "dīlūtus, a, um", czech: "ředěný" },
        { latin: "ductus, ūs, m.", czech: "vývod, kanál" },
        { latin: "exitus, ūs, m.", czech: "smrt" },
        { latin: "faciēs, ēī, f.", czech: "plocha, tvář" },
        { latin: "fētus, ūs, m.", czech: "plod" },
        { latin: "genū, ūs, n.", czech: "koleno" },
        { latin: "gustus, ūs, m.", czech: "chuť (smysl)" },
        { latin: "habitus, ūs, m.", czech: "vzhled" },
        { latin: "hiātus, ūs, m.", czech: "průchod, průzor" },
        { latin: "ictus, ūs, m.", czech: "záchvat, mrtvice" },
        { latin: "īnfarctus, ūs, m.", czech: "infarkt" },
        { latin: "manus, ūs, f.", czech: "ruka" },
        { latin: "meātus, ūs, m.", czech: "chodba, průchod" },
        { latin: "olfactus, ūs, m.", czech: "čich" },
        { latin: "partus, ūs, m.", czech: "porod" },
        { latin: "plexus, ūs, m.", czech: "pleteň" },
        { latin: "processus, ūs, m.", czech: "výběžek" },
        { latin: "prōlāpsus, ūs, m.", czech: "výhřez" },
        { latin: "prūrītus, ūs, m.", czech: "svědění" },
        { latin: "pulsus, ūs, m.", czech: "tep, puls" },
        { latin: "rabiēs, ēī, f.", czech: "vzteklina" },
        { latin: "recessus, ūs, m.", czech: "záhyb" },
        { latin: "rēctificātus, a, um", czech: "čištěný" },
        { latin: "respīrātōrius, a, um", czech: "dýchací" },
        { latin: "scabiēs, ēī, f.", czech: "svrab" },
        { latin: "sēnsus, ūs, m.", czech: "cit, smysl" },
        { latin: "sinus, ūs, m.", czech: "záhyb, dutina" },
        { latin: "situs, ūs, m.", czech: "poloha" },
        { latin: "speciēs, ēī, f.", czech: "druh" },
        { latin: "speciēs, ērum, f. (pl.)", czech: "čaj, čajová směs" },
        { latin: "spīritus, ūs, m.", czech: "dech, duch, líh" },
        { latin: "status, ūs, m.", czech: "stav" },
        { latin: "superficiēs, ēī, f.", czech: "povrch" },
        { latin: "tāctus, ūs, m.", czech: "hmat" },
        { latin: "tractus, ūs, m.", czech: "dráha, soustava" },
        { latin: "ūsus, ūs, m.", czech: "užití, užívání" },
        { latin: "vīsus, ūs, m.", czech: "zrak" },
        { latin: "vomitus, ūs, m.", czech: "zvracení" },
      ],
      practice: [],
    },
    {
      id: 6,
      title: "6. lekce: Substantiva III. deklinace - maskulina, feminina",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Substantiva III. deklinace</h3>
        <p class="mb-4">Největší skupina substantiv. Genitiv singuláru končí vždy na <strong>-is</strong>. Dělí se na kmeny souhláskové a samohláskové (i-kmeny).</p>
        <p class="mb-4">Dělí se také na <strong>různoslabičná</strong> (v gen. sg. o slabiku víc, např. <i>pulmō, pulmōnis, m.</i>) a <strong>stejnoslabičná</strong> (v gen. sg. stejný počet slabik, např. <i>pelvis, pelvis, f.</i>).</p>
        
        <h4 class="text-lg font-semibold mb-2">Typická zakončení (Maskulina a Feminina)</h4>
        <ul class="list-disc list-inside mb-4">
          <li><strong>Feminina:</strong> často na <i>-dō, -gō, -iō</i> (gen. <i>-dinis, -ginis, -iōnis</i>), např. <i>laesiō, iōnis, f.</i> (poškození).</li>
          <li><strong>Feminina:</strong> často na <i>-s, -x</i>, např. <i>pars, partis, f.</i> (část), <i>cervix, īcis, f.</i> (krk).</li>
          <li><strong>Maskulina:</strong> často na <i>-or</i> (gen. <i>-ōris</i>), např. <i>tumor, ōris, m.</i> (nádor), <i>dolor, ōris, m.</i> (bolest).</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Vzor: tumor, ōris, m. - nádor</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">tumor</td><td class="px-4 py-2">tumōr-ēs</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">tumōr-is</td><td class="px-4 py-2">tumōr-um</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">tumōr-em</td><td class="px-4 py-2">tumōr-ēs</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">tumōr-e</td><td class="px-4 py-2">tumōr-ibus</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Genitiv plurálu na -ium (i-kmeny)</h4>
        <p class="mb-4">Mají: 1) substantiva se skupinou souhlásek před <i>-is</i> v gen. sg. (např. <i>pars, partis, f.</i> -> <i>partium</i>; <i>dēns, dentis, m.</i> -> <i>dentium</i>) a 2) stejnoslabičná substantiva (např. <i>auris, auris, f.</i> -> <i>aurium</i>).</p>
      `,
      vocabulary: [
        { latin: "abductor, ōris, m.", czech: "odtahovač" },
        { latin: "ablātiō, iōnis, f.", czech: "odnětí, snesení" },
        { latin: "adductor, ōris, m.", czech: "přitahovač" },
        { latin: "apex, icis, m.", czech: "hrot, vrchol" },
        { latin: "articulātiō, iōnis, f.", czech: "kloub" },
        { latin: "auris, is, f.", czech: "ucho" },
        { latin: "calor, ōris, m.", czech: "teplo, teplota" },
        { latin: "calx, cis, f.", czech: "pata, kost patní" },
        { latin: "canālis, is, m.", czech: "kanál, průchod" },
        { latin: "cartilāgō, inis, f.", czech: "chrupavka" },
        { latin: "cavitās, ātis, f.", czech: "dutina" },
        { latin: "cervix, īcis, f.", czech: "krk, šíje" },
        { latin: "cicātrīx, īcis, f.", czech: "jizva" },
        { latin: "combustiō, iōnis, f.", czech: "popálenina" },
        { latin: "commōtiō, iōnis, f.", czech: "otřes" },
        { latin: "compressiō, iōnis, f.", czech: "stlačení" },
        { latin: "congelātiō, iōnis, f.", czech: "omrzlina" },
        { latin: "constrictor, ōris, m.", czech: "svěrač" },
        { latin: "contūsiō, iōnis, f.", czech: "zhmoždění" },
        { latin: "cortex, icis, m.", czech: "kůra" },
        { latin: "dēns, ntis, m.", czech: "zub" },
        { latin: "dīlātātor, ōris, m.", czech: "rozšiřovač" },
        { latin: "dolor, ōris, m.", czech: "bolest" },
        { latin: "excīsiō, iōnis, f.", czech: "vyříznutí" },
        { latin: "extensor, ōris, m.", czech: "natahovač, napínač" },
        { latin: "extractiō, iōnis, f.", czech: "vytržení" },
        { latin: "extrēmitās, ātis, f.", czech: "pól, konec, končetina" },
        { latin: "faucēs, ium, f. (pl.)", czech: "hltanová úžina" },
        { latin: "febris, is, f.", czech: "horečka" },
        { latin: "flexor, ōris, m.", czech: "ohybač" },
        { latin: "fornix, icis, m.", czech: "klenba, strop" },
        { latin: "frōns, ntis, f.", czech: "čelo" },
        { latin: "fūnctiō, iōnis, f.", czech: "funkce" },
        { latin: "graviditās, itātis, f.", czech: "těhotenství" },
        { latin: "hallūx, ūcis, m.", czech: "palec (u nohy)" },
        { latin: "impressiō, iōnis, f.", czech: "otisk" },
        { latin: "index, icis, m.", czech: "ukazovák" },
        { latin: "īnfectiō, iōnis, f.", czech: "infekce" },
        { latin: "īnflammātiō, iōnis, f.", czech: "zánět" },
        { latin: "iniectiō, iōnis, f.", czech: "injekce" },
        { latin: "īnsertiō, iōnis, f.", czech: "úpon" },
        { latin: "lacerātiō, iōnis, f.", czech: "roztržení" },
        { latin: "laesiō, iōnis, f.", czech: "poškození" },
        { latin: "larynx, ngis, m.", czech: "hrtan" },
        { latin: "levātor, ōris, m.", czech: "zdvihač" },
        { latin: "lēx, lēgis, f.", czech: "zákon, pravidlo" },
        { latin: "liēn, liēnis, m.", czech: "slezina" },
        { latin: "lūxātiō, iōnis, f.", czech: "vymknutí, vykloubení" },
        { latin: "margō, inis, m.", czech: "okraj, kraj" },
        { latin: "māter, tris, f.", czech: "matka, plena mozková" },
        { latin: "mēninx, ngis, f.", czech: "obal" },
        { latin: "mors, mortis, f.", czech: "smrt" },
        { latin: "operātiō, iōnis, f.", czech: "operace" },
        { latin: "orīgō, inis, f.", czech: "začátek; původ" },
        { latin: "pallor, ōris, m.", czech: "bledost" },
        { latin: "palpātiō, iōnis, f.", czech: "vyšetření pohmatem" },
        { latin: "pariēs, etis, m.", czech: "stěna, plocha" },
        { latin: "pars, rtis, f.", czech: "část" },
        { latin: "pelvis, is, f.", czech: "pánev" },
        { latin: "percussiō, iōnis, f.", czech: "vyšetření poklepem" },
        { latin: "pēs, pedis, m.", czech: "noha" },
        { latin: "phalanx, ngis, f.", czech: "článek prstu" },
        { latin: "pharynx, ngis, m.", czech: "hltan" },
        { latin: "pollex, icis, m.", czech: "palec ruky" },
        { latin: "pōns, ntis, m.", czech: "most" },
        { latin: "pulmō, ōnis, m.", czech: "plíce" },
        { latin: "pulvis, eris, m.", czech: "prášek" },
        { latin: "pūnctiō, iōnis, f.", czech: "nabodnutí, punkce" },
        { latin: "rādīx, īcis, f.", czech: "kořen" },
        { latin: "regiō, iōnis, f.", czech: "oblast, krajina" },
        { latin: "rēn, rēnis, m.", czech: "ledvina" },
        { latin: "rubor, ōris, m.", czech: "zarudnutí, zčervenání" },
        { latin: "sanguis, inis, m.", czech: "krev" },
        { latin: "sectiō, iōnis, f.", czech: "pitva; řez" },
        { latin: "sitis, is, f.", czech: "žízeň" },
        { latin: "solūtiō, iōnis, f.", czech: "roztok" },
        { latin: "suffūsiō, iōnis, f.", czech: "podlitina" },
        { latin: "suspīciō, iōnis, f.", czech: "podezření" },
        { latin: "tendō, inis, m.", czech: "šlacha" },
        { latin: "thōrāx, ācis, m.", czech: "hrudník" },
        { latin: "trānsfūsiō, iōnis, f.", czech: "transfúze" },
        { latin: "tūberōsitās, ātis, f.", czech: "drsnatina" },
        { latin: "tumor, ōris, m.", czech: "nádor, zduření" },
        { latin: "tussis, is, f.", czech: "kašel" },
        { latin: "varix, icis, f.", czech: "křečová žíla" },
        { latin: "venter, tris, m.", czech: "bříško, břicho" },
      ],
      practice: [],
    },
    {
      id: 7,
      title: "7. lekce: Neutra III. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Neutra III. deklinace</h3>
        <p class="mb-4">Dělí se na dvě hlavní skupiny:</p>
        <ol class="list-decimal list-inside mb-4">
          <li><strong>Různoslabičná (souhláskový kmen):</strong>
            <ul class="list-circle list-inside ml-6">
              <li>Nom. sg. na <strong>-men</strong>, gen. <strong>-minis</strong> (např. <i>forāmen, inis, n.</i> - otvor)</li>
              <li>Nom. sg. na <strong>-us</strong>, gen. <strong>-oris</strong> (např. <i>corpus, oris, n.</i> - tělo)</li>
              <li>Nom. sg. na <strong>-ur</strong>, gen. <strong>-ūris</strong> (např. <i>crūs, crūris, n.</i> - bérec)</li>
              <li>Další: <i>caput, itis, n.</i> (hlava), <i>cor, cordis, n.</i> (srdce), <i>ōs, ōris, n.</i> (ústa), <i>os, ossis, n.</i> (kost)</li>
            </ul>
          </li>
          <li><strong>Stejnoslabičná (i-kmen):</strong>
            <ul class="list-circle list-inside ml-6">
              <li>Nom. sg. na <strong>-e</strong> (např. <i>rēte, is, n.</i> - síť)</li>
              <li>Nom. sg. na <strong>-al</strong> (např. <i>animal, ālis, n.</i> - živočich)</li>
              <li>Nom. sg. na <strong>-ar</strong> (např. <i>calcar, āris, n.</i> - ostruha)</li>
            </ul>
          </li>
        </ol>

        <h4 class="text-lg font-semibold mb-2">Vzor: corpus, oris, n. - tělo</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">corpus</td><td class="px-4 py-2">corpor-a</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">corpor-is</td><td class="px-4 py-2">corpor-um</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">corpus</td><td class="px-4 py-2">corpor-a</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">corpor-e</td><td class="px-4 py-2">corpor-ibus</td></tr>
          </tbody>
        </table>
        
        <h4 class="text-lg font-semibold mb-2">Vzor: rēte, is, n. - síť</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pád</th><th class="px-4 py-2">Singulár</th><th class="px-4 py-2">Plurál</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">1. Nom.</td><td class="px-4 py-2">rēt-e</td><td class="px-4 py-2">rēt-ia</td></tr>
            <tr><td class="px-4 py-2">2. Gen.</td><td class="px-4 py-2">rēt-is</td><td class="px-4 py-2">rēt-ium</td></tr>
            <tr><td class="px-4 py-2">4. Akuz.</td><td class="px-4 py-2">rēt-e</td><td class="px-4 py-2">rēt-ia</td></tr>
            <tr><td class="px-4 py-2">6. Abl.</td><td class="px-4 py-2">rēt-ī</td><td class="px-4 py-2">rēt-ibus</td></tr>
          </tbody>
        </table>
        
        <p class="mb-4"><strong>Zvláštnosti:</strong> <i>os, ossis, n.</i> (kost) má gen. pl. <i>ossium</i> (i-kmen). <i>Vās, vāsis, n.</i> (céva) se v singuláru skloňuje podle III. dekl., ale v plurálu podle II. dekl. (<i>vāsa, vāsōrum</i>).</p>
      `,
      vocabulary: [
        { latin: "abdōmen, inis, n.", czech: "břicho" },
        { latin: "albūmen, inis, n.", czech: "bílkovina" },
        { latin: "aliēnus, a, um", czech: "cizí" },
        { latin: "animal, ālis, n.", czech: "živočich" },
        { latin: "bovīnus, a, um", czech: "„býčí“, chorobně zvětšený" },
        { latin: "calcar, āris, n.", czech: "ostruha" },
        { latin: "caput, itis, n.", czech: "hlava, hlavice" },
        { latin: "cardiacus, a, um", czech: "srdeční" },
        { latin: "carīnātus, a, um", czech: "ptačí" },
        { latin: "cochlear, āris, n.", czech: "lžíce" },
        { latin: "compactus, a, um", czech: "celistvý, kompaktní" },
        { latin: "contūsus, a, um", czech: "zhmožděný" },
        { latin: "cor, cordis, n.", czech: "srdce" },
        { latin: "corpus, oris, n.", czech: "tělo, těleso" },
        { latin: "crūs, crūris, n.", czech: "bérec, raménko" },
        { latin: "dēviātiō, iõnis, f.", czech: "vybočení, deviace" },
        { latin: "excavātus, a, um", czech: "vyhloubený, vpadlý" },
        { latin: "excoriātiō, ōnis, n.", czech: "odřenina" },
        { latin: "fel, fellis, n.", czech: "žluč" },
        { latin: "femur, oris, n.", czech: "stehno" },
        { latin: "fibrillātiō, iōnis, f.", czech: "míhání, rychlé stahy" },
        { latin: "forāmen, inis, n.", czech: "otvor" },
        { latin: "genus, eris, n.", czech: "rod, druh, původ" },
        { latin: "herpēs, ētis, m.", czech: "opar" },
        { latin: "intentiō, iōnis, f.", czech: "pokus, zásah" },
        { latin: "lacer, era, erum", czech: "tržný" },
        { latin: "latus, eris, n.", czech: "bok, strana" },
        { latin: "lūteus, a, um", czech: "žlutý" },
        { latin: "mare, is, n.", czech: "moře" },
        { latin: "mel, mellis, n.", czech: "med" },
        { latin: "membrānāceus, a, um", czech: "membránový" },
        { latin: "motorius, a, um", czech: "pohyblivý" },
        { latin: "murmur, uris, n.", czech: "šelest" },
        { latin: "nutrīcius, a, um", czech: "vyživující" },
        { latin: "ōs, ōris, n.", czech: "ústa" },
        { latin: "os, ossis, n.", czech: "kost" },
        { latin: "os coxae", czech: "kost pánevní" },
        { latin: "os īlium", czech: "kost kyčelní" },
        { latin: "os ischiī", czech: "kost sedací" },
        { latin: "os pūbis", czech: "kost stydká" },
        { latin: "os sacrum", czech: "kost křížová" },
        { latin: "os zygomaticum", czech: "kost lícní" },
        { latin: "palpitātiō, ōnis, f.", czech: "bušení" },
        { latin: "pectus, oris, n.", czech: "hrud" },
        { latin: "pūs, pūris, n.", czech: "hnis" },
        { latin: "rēte, is, n.", czech: "síť" },
        { latin: "rīma, ae, f.", czech: "štěrbina" },
        { latin: "sāl, salis, m. n.", czech: "sůl" },
        { latin: "scissus, a, um", czech: "řezný" },
        { latin: "sclopetārius, a, um", czech: "střelný" },
        { latin: "sectus, a, um", czech: "sečný" },
        { latin: "spongiosus, a, um", czech: "houbovitý" },
        { latin: "tegmen, inis, n.", czech: "strop, kryt" },
        { latin: "tempus, oris, n.", czech: "čas; spánek (anat.)" },
        { latin: "tūber, eris, n.", czech: "hrbol, výběžek" },
        { latin: "ulcus, eris, n.", czech: "vřed" },
        { latin: "vās, vāsis, n. (pl. vāsa, ōrum)", czech: "céva" },
        { latin: "vīscus, eris, n. (pl. vīscera)", czech: "útroby" },
        { latin: "vulnus, eris, n.", czech: "rána" },
      ],
      practice: [],
    },
    {
      id: 8,
      title: "8. lekce: Řecká substantiva III. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Řecká substantiva III. deklinace</h3>
        <p class="mb-4">Řada řeckých slov se skloňuje podle latinské III. deklinace.</p>
        
        <h4 class="text-lg font-semibold mb-2">Maskulina (vzor tumor)</h4>
        <ul class="list-disc list-inside mb-4">
          <li>Nom. <strong>-ēr</strong>, gen. <strong>-ēris</strong> (např. <i>urētēr, ēris, m.</i> - močovod; <i>sphincter, ēris, m.</i> - svěrač)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Feminina (vzor tumor)</h4>
        <ul class="list-disc list-inside mb-4">
          <li>Nom. <strong>-is</strong>, gen. <strong>-idis</strong> (např. <i>parōtis, idis, f.</i> - příušní žláza; <i>carōtis, idis, f.</i> - krkavice)</li>
          <li>Nom. <strong>-ītis</strong>, gen. <strong>-ītidis</strong> (označuje zánět, např. <i>arthrītis, ītidis, f.</i> - zánět kloubu; <i>hepatītis, ītidis, f.</i> - zánět jater)</li>
        </ul>
        
        <h4 class="text-lg font-semibold mb-2">Neutra (vzor corpus)</h4>
        <ul class="list-disc list-inside mb-4">
          <li>Nom. <strong>-ma</strong>, gen. <strong>-matis</strong> (např. <i>trauma, atis, n.</i> - rána; <i>diaphragma, atis, n.</i> - bránice)</li>
          <li>Nom. <strong>-ōma</strong>, gen. <strong>-ōmatis</strong> (označuje nádor, např. <i>osteōma, atis, n.</i> - kostní nádor)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Feminina (vzor rēte, ale s odchylkami)</h4>
        <p class="mb-4">Nom. <strong>-is</strong>, gen. <strong>-is</strong> (nebo <strong>-eōs</strong>). Akuz. sg. <strong>-im/-in</strong>, Abl. sg. <strong>-ī</strong>. Gen. pl. <strong>-ium</strong>.</p>
        <ul class="list-disc list-inside mb-4">
          <li>Např. <i>basis, is, f.</i> (spodina), <i>metastasis, is, f.</i> (metastáza), <i>dosis, is, f.</i> (dávka)</li>
          <li>Sufix <strong>-ōsis</strong>: nezánětlivé onemocnění (např. <i>arthrosis, is, f.</i>)</li>
          <li>Sufix <strong>-iāsis</strong>: přítomnost kamenů (např. <i>cholēlithiasis, is, f.</i> - žlučové kameny)</li>
        </ul>
      `,
      vocabulary: [
        { latin: "adēn, adenos", czech: "žláza" },
        { latin: "adynamia, ae, f.", czech: "slabost" },
        { latin: "aneurysma, atis, n.", czech: "výduť, rozšíření" },
        { latin: "aponeurosis, is, f.", czech: "plochá šlacha" },
        { latin: "arteriosclerosis, is, f.", czech: "kornatění tepen" },
        { latin: "arthrītis, ītidis, f.", czech: "zánět kloubu" },
        { latin: "arthrosis, is, f.", czech: "nezánětlivé onemocnění kloubu" },
        { latin: "āsthma, atis, n.", czech: "astma, záducha" },
        { latin: "basis, is, f.", czech: "spodina, základna" },
        { latin: "carcinoma, atis, n.", czech: "rakovina" },
        { latin: "carōtis, idis, f.", czech: "krkavice" },
        { latin: "cataplasma, atis, n.", czech: "náplast" },
        { latin: "cōma, atis, n.", czech: "bezvědomí, kóma" },
        { latin: "coxarthrosis, is, f.", czech: "degenerativní onemocnění kyč. kloubu" },
        { latin: "cystis, is, f.", czech: "cysta, váček" },
        { latin: "derma, atis, n.", czech: "kůže" },
        { latin: "diagnosis, is, f.", czech: "diagnóza, rozpoznání" },
        { latin: "diaphragma, atis, n.", czech: "bránice" },
        { latin: "diarrhoë, ës, f.", czech: "průjem" },
        { latin: "dosis, is, f.", czech: "dávka" },
        { latin: "dyspepsia, ae, f.", czech: "porucha trávení" },
        { latin: "emesis, is, f.", czech: "zvracení" },
        { latin: "encephalītis, ītidis, f.", czech: "zánět mozku" },
        { latin: "erythēma, atis, n.", czech: "zarudnutí, překrvení" },
        { latin: "exanthēma, atis, n.", czech: "vyrážka" },
        { latin: "gastër, tris, f.", czech: "žaludek" },
        { latin: "gastrītis, ītidis, f.", czech: "zánět žaludku" },
        { latin: "glaucoma, atis, n.", czech: "zelený oční zákal" },
        { latin: "glōttis, idis, f.", czech: "hlasivka" },
        { latin: "haematōma, atis, n.", czech: "podlitina" },
        { latin: "hēpar, hepatis, n.", czech: "játra" },
        { latin: "hepatītis, ītidis, f.", czech: "zánět jater" },
        { latin: "hypophysis, is, f.", czech: "podvěsek mozkový" },
        { latin: "lipōma, atis, n.", czech: "nádor z tukové tkáně" },
        { latin: "lipos", czech: "tuk" },
        { latin: "massētēr, ēris, m.", czech: "žvýkač" },
        { latin: "metastasis, is, f.", czech: "metastáza" },
        { latin: "myōma, atis, n.", czech: "svalový nádor" },
        { latin: "myosītis, ītidis, f.", czech: "zánět svalu" },
        { latin: "mys, myos", czech: "sval" },
        { latin: "narcosis, is, f.", czech: "narkóza" },
        { latin: "nausea, ae, f.", czech: "nevolnost" },
        { latin: "nephrītis, ītidis, f.", czech: "zánět ledvin" },
        { latin: "nephrosis, is, f.", czech: "nezánětlivé onemocnění ledvin" },
        { latin: "neurītis, ītidis, f.", czech: "zánět nervu" },
        { latin: "neurosis, is, f.", czech: "nezánětlivé onemocnění nervu" },
        { latin: "oedēma, atis, n.", czech: "otok" },
        { latin: "osteōma, atis, n.", czech: "nádor z kostní tkáně" },
        { latin: "osteomyelītis, ītidis, f.", czech: "zánět kostní dřeně" },
        { latin: "otītis, ītidis, f.", czech: "zánět ucha" },
        { latin: "pancreas, atis, n.", czech: "slinivka břišní" },
        { latin: "pancreatītis, ītidis, f.", czech: "zánět slinivky břišní" },
        { latin: "parōtis, idis, f.", czech: "příušní žláza" },
        { latin: "parōtītis, ītidis, f.", czech: "zánět příušní žlázy" },
        { latin: "phthisis, is, f.", czech: "tuberkulóza" },
        { latin: "platysma, atis, n.", czech: "široký krční sval" },
        { latin: "pleurītis, ītidis, f.", czech: "zánět pohrudnice" },
        { latin: "prognosis, is, f.", czech: "prognóza" },
        { latin: "psoriāsis, is, f.", czech: "lupénka" },
        { latin: "scoliosis, is, f.", czech: "vybočení páteře do strany" },
        { latin: "sēpsis, is, f.", czech: "otrava" },
        { latin: "sinusītis, ītidis, f.", czech: "zánět dutin" },
        { latin: "sōma, atis, n.", czech: "tělo" },
        { latin: "sphincter, ēris, m.", czech: "svěrač" },
        { latin: "stigma, atis, n.", czech: "známka, znamení" },
        { latin: "stoma, atis, n.", czech: "ústa" },
        { latin: "strōma, atis, n.", czech: "podpůrná vazivová tkáň" },
        { latin: "symptoma, atis, n.", czech: "příznak" },
        { latin: "syndrōma, atis, n.", czech: "soubor příznaků" },
        { latin: "systēma, atis, n.", czech: "systém" },
        { latin: "thrombosis, is, f.", czech: "trombóza" },
        { latin: "trauma, atis, n.", czech: "rána" },
        { latin: "trochanter, ēris, m.", czech: "chocholík" },
        { latin: "urētēr, ēris, m.", czech: "močovod" },
        { latin: "vertīgō, inis, f.", czech: "závrať" },
      ],
      practice: [],
    },
    {
      id: 9,
      title: "9. lekce: Adjektiva III. deklinace",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Adjektiva III. deklinace</h3>
        <p class="mb-4">Skloňují se jako i-kmeny substantiv III. deklinace (tj. Abl. sg. <strong>-ī</strong>, Gen. pl. <strong>-ium</strong>, Nom./Akuz. pl. neutra <strong>-ia</strong>).</p>
        
        <h4 class="text-lg font-semibold mb-2">Dělení podle zakončení v Nom. sg.:</h4>
        <ul class="list-disc list-inside mb-4">
          <li><strong>Trojvýchodná:</strong> m. <strong>-er</strong>, f. <strong>-is</strong>, n. <strong>-e</strong> (např. <i>ācer, ācris, ācre</i> - ostrý)</li>
          <li><strong>Dvojvýchodná:</strong> m./f. <strong>-is</strong>, n. <strong>-e</strong> (např. <i>brevis, breve</i> - krátký). Velmi častá, často odvozená sufixy <strong>-ālis, -e</strong> (např. <i>vertebrālis, e</i> - obratlový) nebo <strong>-āris, -e</strong>.</li>
          <li><strong>Jednovýchodná:</strong> m./f./n. mají jeden tvar (např. <strong>-x, -s, -ns, -r</strong>), genitiv se uvádí (např. <i>simplex, icis</i> - jednoduchý; <i>recēns, entis</i> - čerstvý).</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Vzor: brevis, e - krátký</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2">Pád</th>
              <th class="px-4 py-2">Maskulinum / Femininum</th>
              <th class="px-4 py-2">Neutrum</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">Nom. sg.</td><td class="px-4 py-2">brev-is</td><td class="px-4 py-2">brev-e</td></tr>
            <tr><td class="px-4 py-2">Gen. sg.</td><td class="px-4 py-2">brev-is</td><td class="px-4 py-2">brev-is</td></tr>
            <tr><td class="px-4 py-2">Abl. sg.</td><td class="px-4 py-2">brev-ī</td><td class="px-4 py-2">brev-ī</td></tr>
            <tr><td class="px-4 py-2">Nom. pl.</td><td class="px-4 py-2">brev-ēs</td><td class="px-4 py-2">brev-ia</td></tr>
            <tr><td class="px-4 py-2">Gen. pl.</td><td class="px-4 py-2">brev-ium</td><td class="px-4 py-2">brev-ium</td></tr>
          </tbody>
        </table>

        <h4 class="text-lg font-semibold mb-2">Vzor: recēns, entis - čerstvý</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2">Pád</th>
              <th class="px-4 py-2">Maskulinum / Femininum</th>
              <th class="px-4 py-2">Neutrum</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">Nom. sg.</td><td class="px-4 py-2">recēns</td><td class="px-4 py-2">recēns</td></tr>
            <tr><td class="px-4 py-2">Gen. sg.</td><td class="px-4 py-2">recent-is</td><td class="px-4 py-2">recent-is</td></tr>
            <tr><td class="px-4 py-2">Abl. sg.</td><td class="px-4 py-2">recent-ī</td><td class="px-4 py-2">recent-ī</td></tr>
            <tr><td class="px-4 py-2">Nom. pl.</td><td class="px-4 py-2">recent-ēs</td><td class="px-4 py-2">recent-ia</td></tr>
            <tr><td class="px-4 py-2">Gen. pl.</td><td class="px-4 py-2">recent-ium</td><td class="px-4 py-2">recent-ium</td></tr>
          </tbody>
        </table>
      `,
      vocabulary: [
        { latin: "abdominālis, e", czech: "břišní" },
        { latin: "ācer, ācris, ācre", czech: "prudký, ostrý" },
        { latin: "aequālis, e", czech: "stejný" },
        { latin: "anulāris, e", czech: "prstencový, kruhový" },
        { latin: "articulāris, e", czech: "kloubní" },
        { latin: "biceps, bicipitis", czech: "dvojhlavý" },
        { latin: "biventer, tris, tre", czech: "dvojbříškový" },
        { latin: "brevis, e", czech: "krátký" },
        { latin: "bronchiālis, e", czech: "průduškový" },
        { latin: "capillāris, e", czech: "vlásečnicový" },
        { latin: "capitālis, e", czech: "hlavový" },
        { latin: "causālis, e", czech: "příčinný" },
        { latin: "celer, is, e", czech: "rychlý" },
        { latin: "cervīcālis, e", czech: "krční" },
        { latin: "commūnis, e", czech: "společný" },
        { latin: "costālis, e", czech: "žeberní" },
        { latin: "crāniālis, e", czech: "lebeční" },
        { latin: "dentālis, e", czech: "zubní" },
        { latin: "dēns molāris", czech: "stolička" },
        { latin: "difficilis, e", czech: "obtížný, nesnadný" },
        { latin: "distālis, e", czech: "koncový, okrajový" },
        { latin: "dorsālis, e", czech: "hřbetní, zádový, zadní" },
        { latin: "duplex, duplicis", czech: "dvojitý" },
        { latin: "faciālis, e", czech: "licní" },
        { latin: "femorālis, e", czech: "stehenní" },
        { latin: "fibulāris, e", czech: "lýtkový" },
        { latin: "frequens, entis", czech: "častý" },
        { latin: "frontālis, e", czech: "čelní" },
        { latin: "gravis, e", czech: "těžký" },
        { latin: "impār, imparis", czech: "nestejný" },
        { latin: "intervertebrālis, e", czech: "meziobratlový" },
        { latin: "intrāmūsculāris, e", czech: "nitrosvalový" },
        { latin: "iugulāris, e", czech: "hrdelní" },
        { latin: "laterālis, e", czech: "boční, postranní" },
        { latin: "lumbālis, e", czech: "bederní" },
        { latin: "medicīnālis, e", czech: "lékařský, léčivý" },
        { latin: "medulla spīnālis", czech: "mícha" },
        { latin: "mitrālis, e", czech: "mitrální, dvojcípý" },
        { latin: "mollis, e", czech: "měkký" },
        { latin: "nasālis, e", czech: "nosní" },
        { latin: "nosocomiālis, e", czech: "nemocniční" },
        { latin: "occipitālis, e", czech: "týlní" },
        { latin: "omnis, e", czech: "každý, všechen" },
        { latin: "palmāris, e", czech: "dlaňový" },
        { latin: "parietālis, e", czech: "temenní; nástěnný" },
        { latin: "pectorālis, e", czech: "hrudní, prsní" },
        { latin: "plantāris, e", czech: "chodidlový" },
        { latin: "prīncipālis, e", czech: "hlavní" },
        { latin: "proximālis, e", czech: "horní, bližší" },
        { latin: "pulmonālis, e", czech: "plicní" },
        { latin: "quadriceps, quadricipitis", czech: "čtyřhlavý" },
        { latin: "recēns, entis", czech: "čerstvý" },
        { latin: "rēnālis, e", czech: "ledvinový" },
        { latin: "sacrālis, e", czech: "křížový" },
        { latin: "sapō, ōnis, m.", czech: "mýdlo" },
        { latin: "senīlis, e", czech: "stařecký" },
        { latin: "similis, e", czech: "podobný" },
        { latin: "simplex, simplicis", czech: "jednoduchý" },
        { latin: "spīnālis, e", czech: "míšní; trnový" },
        { latin: "superficiālis, e", czech: "povrchový" },
        { latin: "temporālis, e", czech: "spánkový" },
        { latin: "tenuis, e", czech: "tenký" },
        { latin: "terēs, ētis", czech: "hladký, oblý" },
        { latin: "tībiālis, e", czech: "holenní" },
        { latin: "triceps, tricipitis", czech: "trojhlavý" },
        { latin: "ulnāris, e", czech: "loketní" },
        { latin: "ūniversālis, e", czech: "celkový, povšechný" },
        { latin: "vertebrālis, e", czech: "obratlový" },
      ],
      practice: [],
    },
    {
      id: 10,
      title: "10. lekce: Participium prézenta aktiva",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Participium prézenta aktiva</h3>
        <p class="mb-4">Vyjadřuje děj probíhající v současnosti, neukončený a činný. Překládá se jako přídavné jméno slovesné činné (např. "léčící", "vidoucí") nebo vedlejší větou ("ten, který léčí").</p>
        
        <h4 class="text-lg font-semibold mb-2">Tvoření</h4>
        <ul class="list-disc list-inside mb-4">
          <li><strong>I. a II. konj.:</strong> Kmen + <strong>-ns</strong> (např. <i>sānā-ns</i>, <i>vidē-ns</i>)</li>
          <li><strong>III. a IV. konj.:</strong> Kmen + <strong>-ēns</strong> (např. <i>scrīb-ēns</i>, <i>audi-ēns</i>)</li>
        </ul>
        <p class="mb-4">V nominativu sg. končí na <strong>-āns</strong> nebo <strong>-ēns</strong>, v genitivu sg. na <strong>-antis</strong> nebo <strong>-entis</strong>. Skloňuje se jako jednovýchodné adjektivum III. deklinace (vzor <i>recēns</i>).</p>

        <h4 class="text-lg font-semibold mb-2">Příklad skloňování: latēns, entis - skrytý</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr>
              <th class="px-4 py-2">Pád</th>
              <th class="px-4 py-2">Maskulinum / Femininum</th>
              <th class="px-4 py-2">Neutrum</th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">Nom. sg.</td><td class="px-4 py-2">latēns</td><td class="px-4 py-2">latēns</td></tr>
            <tr><td class="px-4 py-2">Gen. sg.</td><td class="px-4 py-2">latent-is</td><td class="px-4 py-2">latent-is</td></tr>
            <tr><td class="px-4 py-2">Abl. sg.</td><td class="px-4 py-2">latent-ī</td><td class="px-4 py-2">latent-ī</td></tr>
            <tr><td class="px-4 py-2">Nom. pl.</td><td class="px-4 py-2">latent-ēs</td><td class="px-4 py-2">latent-ia</td></tr>
            <tr><td class="px-4 py-2">Gen. pl.</td><td class="px-4 py-2">latent-ium</td><td class="px-4 py-2">latent-ium</td></tr>
          </tbody>
        </table>
        
        <p class="mb-4">Často se používá pro označení léků podle účinku, např. <i>remedium exsiccāns</i> (lék vysušující) nebo v plurálu <i>expectorantia</i> (léky usnadňující odkašlávání).</p>
      `,
      vocabulary: [
        { latin: "abducēns, entis", czech: "odvodný" },
        { latin: "aberrāns, antis", czech: "odchylující se, odbočující" },
        { latin: "adiuvāns, antis", czech: "podpůrný" },
        { latin: "adolēscēns, entis", czech: "dospívající" },
        { latin: "adstringēns, entis", czech: "stahující" },
        { latin: "afferēns, entis", czech: "přivádějící, přívodný" },
        { latin: "agēns, entis", czech: "tvůrčí, účinný" },
        { latin: "ascendēns, entis", czech: "vzestupný" },
        { latin: "calcificāns, antis", czech: "zvápeňující" },
        { latin: "comitāns, antis", czech: "provázející" },
        { latin: "commūnicāns, antis", czech: "spojující" },
        { latin: "confluens, entis", czech: "splývající" },
        { latin: "dēformāns, antis", czech: "deformující" },
        { latin: "dēscendēns, entis", czech: "sestupný" },
        { latin: "differentiālis, e", czech: "rozlišující" },
        { latin: "donātor, ōris, m.", czech: "dárce" },
        { latin: "efferēns, entis", czech: "odvodný" },
        { latin: "effervescens, entis", czech: "šumivý" },
        { latin: "ēmolliēns, entis", czech: "změkčující" },
        { latin: "exacerbāns, antis", czech: "zhoršující se" },
        { latin: "excitāns, antis", czech: "povzbuzující" },
        { latin: "expectorāns, antis", czech: "usnadňující odkašlávání" },
        { latin: "exsiccāns, entis", czech: "vysušující" },
        { latin: "exulcerāns, antis", czech: "vředovatějící" },
        { latin: "fluctuāns, antis", czech: "volný" },
        { latin: "fulmināns, antis", czech: "bleskový" },
        { latin: "imminēns, entis", czech: "hrozící" },
        { latin: "incipiēns, entis", czech: "začínající" },
        { latin: "īnfāns, ntis, m.", czech: "dítě" },
        { latin: "intermittens, entis", czech: "střídavý" },
        { latin: "latēns, entis", czech: "skrytý" },
        { latin: "laxāns, antis", czech: "projímavý" },
        { latin: "meningītis, ītidis, f.", czech: "zánět mozkových blan" },
        { latin: "migrāns, antis", czech: "stěhovavý, bludný" },
        { latin: "multiplex, icis", czech: "mnohočetný" },
        { latin: "obtūrāns, antis", czech: "zneprůchodňující" },
        { latin: "opponēns, entis", czech: "stojící proti" },
        { latin: "penetrāns, antis", czech: "pronikající" },
        { latin: "perforāns, antis", czech: "proděravějící" },
        { latin: "permanēns, entis", czech: "stálý, trvalý" },
        { latin: "persistēns, entis", czech: "přetrvávající" },
        { latin: "praesēns, entis", czech: "přítomný, současný" },
        { latin: "prōgrediēns, entis", czech: "postupující, šířící se" },
        { latin: "prōminēns, entis", czech: "vyčnívající" },
        { latin: "recipiēns, entis", czech: "příjemce" },
        { latin: "reconvalescēns, entis", czech: "uzdravující se" },
        { latin: "recurrēns, entis", czech: "návratný, zpětný" },
        { latin: "remittens, entis", czech: "povolující, ustupující" },
        { latin: "stenōsāns, antis", czech: "zužující" },
        { latin: "sufficiens, entis", czech: "dostačující" },
      ],
      practice: [],
    },
    {
      id: 11,
      title: "11. lekce: Stupňování adjektiv",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Stupňování adjektiv</h3>
        <p class="mb-4">Adjektiva mají 3 stupně: 1. pozitiv (např. <i>longus</i>), 2. komparativ (<i>longior</i>), 3. superlativ (<i>longissimus</i>).</p>

        <h4 class="text-lg font-semibold mb-2">Komparativ (2. stupeň)</h4>
        <p class="mb-4">Tvoří se příponami <strong>-ior</strong> (m./f.) a <strong>-ius</strong> (n.) ke kmeni adjektiva. Genitiv sg. je <strong>-iōris</strong>. Skloňuje se podle III. deklinace (vzor <i>tumor/corpus</i>).</p>
        <ul class="list-disc list-inside mb-4">
          <li><i>longus</i> -> <i>longior, longius</i> (delší)</li>
          <li><i>brevis</i> -> <i>brevior, brevius</i> (kratší)</li>
          <li><i>recēns</i> -> <i>recentior, recentius</i> (čerstvější)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Superlativ (3. stupeň)</h4>
        <p class="mb-4">Tvoří se příponami <strong>-issimus, a, um</strong> (nejčastější), <strong>-rimus, a, um</strong> (pro adj. na -er), <strong>-limus, a, um</strong> (pro 6 adj. na -ilis). Skloňuje se podle I. a II. deklinace.</p>
        <ul class="list-disc list-inside mb-4">
          <li><i>longus</i> -> <i>longissimus</i> (nejdelší)</li>
          <li><i>ācer</i> -> <i>ācerrimus</i> (nejprudší)</li>
          <li><i>facilis</i> -> <i>facillimus</i> (nejsnadnější)</li>
        </ul>

        <h4 class="text-lg font-semibold mb-2">Nepravidelné stupňování</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pozitiv</th><th class="px-4 py-2">Komparativ</th><th class="px-4 py-2">Superlativ</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">magnus (velký)</td><td class="px-4 py-2">maior, maius</td><td class="px-4 py-2">māximus, a, um</td></tr>
            <tr><td class="px-4 py-2">parvus (malý)</td><td class="px-4 py-2">minor, minus</td><td class="px-4 py-2">minimus, a, um</td></tr>
            <tr><td class="px-4 py-2">bonus (dobrý)</td><td class="px-4 py-2">melior, melius</td><td class="px-4 py-2">optimus, a, um</td></tr>
            <tr><td class="px-4 py-2">malus (špatný)</td><td class="px-4 py-2">peior, peius</td><td class="px-4 py-2">pessimus, a, um</td></tr>
          </tbody>
        </table>
        
        <h4 class="text-lg font-semibold mb-2">Neúplné stupňování (bez pozitivu)</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Komparativ (překlad pozitivem)</th><th class="px-4 py-2">Superlativ</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">superior, superius (horní)</td><td class="px-4 py-2">suprēmus / summus (nejvyšší)</td></tr>
            <tr><td class="px-4 py-2">īnferior, īnferius (dolní)</td><td class="px-4 py-2">īnfimus / īmus (nejnižší)</td></tr>
            <tr><td class="px-4 py-2">anterior, anterius (přední)</td><td class="px-4 py-2">--</td></tr>
            <tr><td class="px-4 py-2">posterior, posterius (zadní)</td><td class="px-4 py-2">postrēmus (nejzadnější)</td></tr>
            <tr><td class="px-4 py-2">interior, interius (vnitřní)</td><td class="px-4 py-2">intimus (nejvnitřnější)</td></tr>
            <tr><td class="px-4 py-2">exterior, exterius (vnější)</td><td class="px-4 py-2">extrēmus (nejzazší)</td></tr>
          </tbody>
        </table>
        <p class="mb-4">V anatomii se <i>maior/minor, superior/īnferior</i> atd. často překládají pozitivem (např. <i>trochanter maior</i> - velký chocholík).</p>
      `,
      vocabulary: [
        { latin: "adventīcia, ae, f.", czech: "zevní vrstva cévní stěny" },
        { latin: "anterior, ius", czech: "přední" },
        { latin: "bonus, a, um", czech: "dobrý" },
        { latin: "calix, icis, m.", czech: "kalich" },
        { latin: "certus, a, um", czech: "jistý" },
        { latin: "cingulum, ī, n.", czech: "pásek, pletenec" },
        { latin: "cuspis, idis, f.", czech: "cíp, hrot" },
        { latin: "difficilis, e", czech: "nesnadný, obtížný" },
        { latin: "dissimilis, e", czech: "nepodobný" },
        { latin: "embolus, ī, m.", czech: "vmetek" },
        { latin: "exterior, ius", czech: "vnější" },
        { latin: "extrēmus, a, um", czech: "nejzazší" },
        { latin: "facilis, e", czech: "snadný" },
        { latin: "fortis, e", czech: "silný" },
        { latin: "fragilis, e", czech: "křehký" },
        { latin: "glūtaeus, ī, m.", czech: "hýžďový sval" },
        { latin: "gracilis, e", czech: "tenký, štíhlý" },
        { latin: "humilis, e", czech: "nízký" },
        { latin: "īmus, a, um", czech: "nejnižší" },
        { latin: "īnferior, ius", czech: "dolní" },
        { latin: "īnfimus, a, um", czech: "nejnižší" },
        { latin: "intercostālis, e", czech: "mezižeberní" },
        { latin: "interior, ius", czech: "vnitřní" },
        { latin: "intimus, a, um", czech: "nejvnitřnější" },
        { latin: "lātissimus, a, um", czech: "nejširší, široký (anat.)" },
        { latin: "levis, e", czech: "lehký" },
        { latin: "longissimus, a, um", czech: "nejdelší, dlouhý (anat.)" },
        { latin: "magnus, a, um", czech: "velký" },
        { latin: "maior, maius", czech: "větší; velký (anat.)" },
        { latin: "malus, a, um", czech: "špatný" },
        { latin: "māximus, a, um", czech: "největší" },
        { latin: "melior, melius", czech: "lepší" },
        { latin: "minor, minus", czech: "menší; malý (anat.)" },
        { latin: "minimus, a, um", czech: "nejmenší" },
        { latin: "multī, ae, a", czech: "mnozí" },
        { latin: "optimus, a, um", czech: "nejlepší" },
        { latin: "parvus, a, um", czech: "malý" },
        { latin: "peior, peius", czech: "horší" },
        { latin: "pessimus, a, um", czech: "nejhorší" },
        { latin: "plūrimī, ae, a", czech: "nejčetnější" },
        { latin: "plūrēs, plūra", czech: "četnější" },
        { latin: "posterior, ius", czech: "zadní" },
        { latin: "postrēmus, a, um", czech: "nejzadnější, poslední" },
        { latin: "resistentia, ae, f.", czech: "odpor, odolnost" },
        { latin: "sagittālis, e", czech: "šípový" },
        { latin: "salīvārius, a, um", czech: "slinný" },
        { latin: "sēnsōrius, a, um", czech: "senzorický, vnímatelný" },
        { latin: "similis, e", czech: "podobný" },
        { latin: "subtīlis, e", czech: "jemný" },
        { latin: "summus, a, um", czech: "nejvyšší" },
        { latin: "superior, ius", czech: "horní" },
        { latin: "suprēmus, a, um", czech: "nejvyšší" },
        { latin: "vehemens, ntis", czech: "silný, vydatný" },
        { latin: "ventrālis, e", czech: "břišní, směrem k břichu" },
      ],
      practice: [],
    },
    {
      id: 12,
      title: "12. lekce: Adverbia",
      theory: `
        <h3 class="text-xl font-semibold mb-3">Tvoření adverbií (Příslovcí)</h3>
        
        <h4 class="text-lg font-semibold mb-2">Od adjektiv I. a II. deklinace</h4>
        <p class="mb-4">Tvoří se příponou <strong>-ē</strong> ke kmeni. Např. <i>longus</i> -> <i>long-ē</i> (dlouze).</p>
        <p class="mb-4">Výjimky: <i>bonus</i> -> <i>bene</i> (dobře), <i>malus</i> -> <i>male</i> (špatně).</p>

        <h4 class="text-lg font-semibold mb-2">Od adjektiv III. deklinace</h4>
        <p class="mb-4">Tvoří se příponou <strong>-iter</strong> ke kmeni. Např. <i>brevis</i> -> <i>brev-iter</i> (krátce), <i>ācer</i> -> <i>ācr-iter</i> (prudce).</p>
        <p class="mb-4">Adjektiva na <strong>-ns</strong> tvoří příponou <strong>-er</strong>. Např. <i>recēns</i> -> <i>recent-er</i> (čerstvě), <i>frequens</i> -> <i>frequent-er</i> (často).</p>
        <p class="mb-4">Výjimka: <i>facilis</i> -> <i>facile</i> (snadno).</p>

        <h3 class="text-xl font-semibold mb-3 mt-6">Stupňování adverbií</h3>
        <p class="mb-4">Komparativ (2. stupeň) je shodný s neutrem komparativu adjektiva (končí na <strong>-ius</strong>). Superlativ (3. stupeň) se tvoří od superlativu adjektiva příponou <strong>-ē</strong>.</p>
        
        <h4 class="text-lg font-semibold mb-2">Pravidelné stupňování</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pozitiv</th><th class="px-4 py-2">Komparativ (-ius)</th><th class="px-4 py-2">Superlativ (-ē)</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">longē (dlouze)</td><td class="px-4 py-2">longius (déle)</td><td class="px-4 py-2">longissimē (nejdéle)</td></tr>
            <tr><td class="px-4 py-2">ācriter (prudce)</td><td class="px-4 py-2">ācrius (prudčeji)</td><td class="px-4 py-2">ācerrimē (nejprudčeji)</td></tr>
            <tr><td class="px-4 py-2">facile (snadno)</td><td class="px-4 py-2">facilius (snadněji)</td><td class="px-4 py-2">facillimē (nejsnadněji)</td></tr>
          </tbody>
        </table>
        
        <h4 class="text-lg font-semibold mb-2">Nepravidelné stupňování</h4>
        <table class="min-w-full divide-y divide-gray-200 border border-gray-300 mb-6">
          <thead class="bg-gray-100">
            <tr><th class="px-4 py-2">Pozitiv</th><th class="px-4 py-2">Komparativ</th><th class="px-4 py-2">Superlativ</th></tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr><td class="px-4 py-2">bene (dobře)</td><td class="px-4 py-2">melius (lépe)</td><td class="px-4 py-2">optimē (nejlépe)</td></tr>
            <tr><td class="px-4 py-2">male (špatně)</td><td class="px-4 py-2">peius (hůře)</td><td class="px-4 py-2">pessimē (nejhůře)</td></tr>
            <tr><td class="px-4 py-2">multum (mnoho)</td><td class="px-4 py-2">plūs (více)</td><td class="px-4 py-2">plūrimum (nejvíce)</td></tr>
            <tr><td class="px-4 py-2">paulum (málo)</td><td class="px-4 py-2">minus (méně)</td><td class="px-4 py-2">minimē (nejméně)</td></tr>
          </tbody>
        </table>
      `,
      vocabulary: [
        { latin: "altus, a, um", czech: "vysoký" },
        { latin: "bene", czech: "dobře" },
        { latin: "breviter", czech: "krátce" },
        { latin: "citius", czech: "rychleji" },
        { latin: "constāns, antis", czech: "stálý, trvalý" },
        { latin: "constanter", czech: "trvale" },
        { latin: "diū", czech: "dlouho" },
        { latin: "exāctē", czech: "přesně" },
        { latin: "facile", czech: "snadno" },
        { latin: "facilius", czech: "snadněji" },
        { latin: "fortiter", czech: "silně" },
        { latin: "frequenter", czech: "často" },
        { latin: "graviter", czech: "těžce" },
        { latin: "lege artis (l. a.)", czech: "odborně" },
        { latin: "magistrāliter", czech: "odborně (lékárensky)" },
        { latin: "magnopere", czech: "velmi" },
        { latin: "magis", czech: "více, spíše" },
        { latin: "male", czech: "špatně" },
        { latin: "maximē", czech: "nejvíce" },
        { latin: "melius", czech: "lépe" },
        { latin: "minus", czech: "méně" },
        { latin: "multum", czech: "mnoho" },
        { latin: "noctū", czech: "v noci" },
        { latin: "nūper", czech: "nedávno" },
        { latin: "ōlim", czech: "dávno" },
        { latin: "optimē", czech: "nejlépe" },
        { latin: "paulum", czech: "málo" },
        { latin: "peius", czech: "hůře" },
        { latin: "pessimē", czech: "nejhůře" },
        { latin: "plūs", czech: "více" },
        { latin: "plūrimum", czech: "nejvíce" },
        { latin: "praecipuē", czech: "zvláště, především" },
        { latin: "quantum", czech: "kolik" },
        { latin: "recenter", czech: "čerstvě" },
        { latin: "saepe", czech: "často" },
        { latin: "satis", czech: "dost" },
        { latin: "semper", czech: "stále" },
        { latin: "simpliciter", czech: "jednoduše" },
        { latin: "statim", czech: "ihned" },
        { latin: "suāvis, e", czech: "libý, příjemný" },
        { latin: "vērisimiliter", czech: "pravděpodobně" },
      ],
      practice: [],
    },
  ],
  test: [
    {
      question: "K jaké deklinaci patří 'vēna, ae, f.'?",
      options: ["I. deklinace", "II. deklinace", "III. deklinace"],
      correctAnswer: "I. deklinace",
    },
    {
      question: "Co znamená 'cerebrum, ī, n.'?",
      options: ["Žíla", "Mozek", "Sval", "Kost"],
      correctAnswer: "Mozek",
    },
    {
      question: "Jaký je genitiv singuláru od 'nervus, ī, m.'?",
      options: ["nervus", "nervōrum", "nervī", "nervum"],
      correctAnswer: "nervī",
    },
    {
      question: "Jaký je nominativ plurálu od 'palātum, ī, n.'?",
      options: ["palātī", "palātōrum", "palāta", "palātum"],
      correctAnswer: "palāta",
    },
    {
      question: "Přeložte 'zlomenina žebra':",
      options: ["Fractūra costae", "Vēna magna", "Morbus cerebrī", "Cancer linguae"],
      correctAnswer: "Fractūra costae",
    },
    {
      question: "Jaký pád je 'in aquā' (ve vodě)?",
      options: ["Nominativ", "Genitiv", "Akuzativ", "Ablativ"],
      correctAnswer: "Ablativ",
    },
    {
      question: "Co znamená 'glandula'?",
      options: ["Žláza", "Jazyk", "Dutina", "Hlava"],
      correctAnswer: "Žláza",
    },
    {
      question: "K jakému rodu patří 'digitus, ī, m.'?",
      options: ["Maskulinum", "Femininum", "Neutrum"],
      correctAnswer: "Maskulinum",
    },
    {
      question: "Vyberte slovo, které NEPATŘÍ do I. deklinace:",
      options: ["costa, ae, f.", "mūsculus, ī, m.", "vēna, ae, f.", "lingua, ae, f."],
      correctAnswer: "mūsculus, ī, m.",
    },
    {
      question: "Co znamená 'ante' (předl. s ak.)?",
      options: ["Před", "Po", "V, na", "S, se"],
      correctAnswer: "Před",
    },
  ],
};

// --- Pomocné komponenty (Ikony) ---

const IconBookOpen = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
  </svg>
);

const IconList = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M4 6h16M4 10h16M4 14h16M4 18h16" />
  </svg>
);

const IconPencil = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
  </svg>
);

const IconCheckSquare = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
  </svg>
);

const IconHome = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 01-1 1h-2a1 1 0 01-1-1v-4z" />
  </svg>
);

const IconChevronLeft = () => (
  <svg xmlns="http://www.w3.org/2000/svg" className="h-5 w-5 mr-2 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M15 19l-7-7 7-7" />
  </svg>
);

// --- Nová ikona pro načítání ---
const IconLoading = () => (
  <svg className="animate-spin h-5 w-5 mr-3" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 4.75V6.25" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M17.1266 6.87347L16.0659 7.93413" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M19.25 12L17.75 12" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M17.1266 17.1265L16.0659 16.0659" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M12 17.75V19.25" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M6.87344 17.1265L7.9341 16.0659" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M4.75 12L6.25 12" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
    <path d="M6.87344 6.87347L7.9341 7.93413" stroke="currentColor" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"></path>
  </svg>
);


// --- Komponenty stránek ---

const Header = ({ title }) => (
  <header className="bg-white shadow-md p-4 sticky top-0 z-10">
    <h1 className="text-2xl font-bold text-blue-800">{title}</h1>
  </header>
);

const Footer = () => (
  <footer className="bg-gray-200 text-gray-600 p-4 mt-8 text-center text-xs">
    <p>Vypracoval: František Vlček Jr. 2025.</p>
    <p>čerpáno z učebnice : ZÁKLADY LATINSKÉ LÉKAŘSKÉ TERMINOLOGIE pro bakalářské obory (VŠS) Jiřina Plašilová.</p>
  </footer>
);

const Sidebar = ({ onNavClick, lessons }) => (
  <nav className="w-full md:w-64 bg-gray-800 text-white p-4 flex-shrink-0">
    <h2 className="text-xl font-semibold mb-4">Navigace</h2>
    <ul>
      <li>
        <button onClick={() => onNavClick('home')} className="flex items-center w-full text-left py-2 px-3 rounded hover:bg-gray-700 transition-colors">
          <IconHome /> Domů
        </button>
      </li>
      <li>
        <button onClick={() => onNavClick('lesson_overview')} className="flex items-center w-full text-left py-2 px-3 rounded hover:bg-gray-700 transition-colors">
          <IconList /> Přehled lekcí
        </button>
      </li>
      <li>
        <button onClick={() => onNavClick('test')} className="flex items-center w-full text-left py-2 px-3 rounded hover:bg-gray-700 transition-colors mt-4">
          <IconCheckSquare /> Závěrečný test
        </button>
      </li>
      
      <li className="mt-6">
        <span className="text-xs font-semibold text-gray-400 uppercase tracking-wider">Jednotlivé lekce</span>
      </li>
      {lessons.map(lesson => (
        <li key={lesson.id}>
          <button onClick={() => onNavClick('lesson', lesson.id)} className="w-full text-left py-2 px-3 rounded hover:bg-gray-700 transition-colors text-sm">
            {lesson.title}
          </button>
        </li>
      ))}
    </ul>
  </nav>
);

const HomePage = () => (
  <div className="bg-white p-6 rounded-lg shadow-lg">
    <h2 className="text-3xl font-bold text-gray-800 mb-4">Vítejte ve výukové aplikaci!</h2>
    <p className="text-lg text-gray-700 mb-4">
      Tato aplikace je navržena pro studenty bakalářských oborů k procvičení základů
      latinské lékařské terminologie.
    </p>
    <p className="text-gray-600 mb-6">
      Vyberte si lekci z navigace vlevo pro zobrazení teorie, slovní zásoby, nebo si
      rovnou vyzkoušejte cvičení. Po prostudování všech materiálů si můžete
      ověřit své znalosti v závěrečném testu.
    </p>
    <div className="bg-blue-50 border-l-4 border-blue-500 text-blue-800 p-4 rounded-md">
      <p className="font-semibold">Hodně štěstí při studiu!</p>
    </div>
  </div>
);

const LessonOverviewPage = ({ lessons, onNavClick }) => (
  <div className="bg-white p-6 rounded-lg shadow-lg">
    <h2 className="text-3xl font-bold text-gray-800 mb-6">Přehled lekcí</h2>
    <div className="space-y-6">
      {lessons.map(lesson => (
        <div key={lesson.id} className="border border-gray-200 p-4 rounded-lg shadow-sm">
          <h3 className="text-xl font-semibold text-blue-700 mb-3">{lesson.title}</h3>
          <div className="flex flex-wrap gap-2">
            <button 
              onClick={() => onNavClick('lesson', lesson.id)}
              className="bg-blue-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-blue-700 transition-colors flex items-center"
            >
              <IconBookOpen /> Teorie
            </button>
            <button 
              onClick={() => onNavClick('vocabulary', lesson.id)}
              className="bg-green-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-green-700 transition-colors flex items-center"
            >
              <IconList /> Slovíčka
            </button>
            <button 
              onClick={() => onNavClick('practice', lesson.id)}
              className="bg-yellow-500 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-yellow-600 transition-colors flex items-center"
            >
              <IconPencil /> Procvičování
            </button>
          </div>
        </div>
      ))}
    </div>
  </div>
);

const LessonPage = ({ lesson, onNavClick }) => (
  <div className="bg-white p-6 rounded-lg shadow-lg">
    <button onClick={() => onNavClick('lesson_overview')} className="text-blue-600 hover:text-blue-800 mb-4 flex items-center text-sm">
      <IconChevronLeft /> Zpět na přehled lekcí
    </button>
    <h2 className="text-3xl font-bold text-gray-800 mb-6">{lesson.title} - Teorie</h2>
    {/* Použití dangerouslySetInnerHTML pro renderování HTML obsahu (tabulky, formátování) */}
    <div className="prose max-w-none" dangerouslySetInnerHTML={{ __html: lesson.theory }} />
    
    <div className="flex flex-wrap gap-2 mt-8 border-t pt-6">
      <button 
        onClick={() => onNavClick('vocabulary', lesson.id)}
        className="bg-green-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-green-700 transition-colors flex items-center"
      >
        <IconList /> Přejít na slovíčka
      </button>
      <button 
        onClick={() => onNavClick('practice', lesson.id)}
        className="bg-yellow-500 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-yellow-600 transition-colors flex items-center"
      >
        <IconPencil /> Přejít na procvičování
      </button>
    </div>
  </div>
);

const VocabularyPage = ({ lesson, onNavClick }) => (
  <div className="bg-white p-6 rounded-lg shadow-lg">
    <button onClick={() => onNavClick('lesson_overview')} className="text-blue-600 hover:text-blue-800 mb-4 flex items-center text-sm">
      <IconChevronLeft /> Zpět na přehled lekcí
    </button>
    <h2 className="text-3xl font-bold text-gray-800 mb-6">{lesson.title} - Slovní zásoba</h2>
    <div className="overflow-x-auto">
      <table className="min-w-full divide-y divide-gray-200 border border-gray-300">
        <thead className="bg-gray-100">
          <tr>
            <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Latinský termín</th>
            <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Český překlad</th>
          </tr>
        </thead>
        <tbody className="bg-white divide-y divide-gray-200">
          {lesson.vocabulary.map((item, index) => (
            <tr key={index} className={index % 2 === 0 ? 'bg-white' : 'bg-gray-50'}>
              <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{item.latin}</td>
              <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{item.czech}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
    <div className="flex flex-wrap gap-2 mt-8 border-t pt-6">
      <button 
        onClick={() => onNavClick('lesson', lesson.id)}
        className="bg-blue-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-blue-700 transition-colors flex items-center"
      >
        <IconBookOpen /> Přejít na teorii
      </button>
      <button 
        onClick={() => onNavClick('practice', lesson.id)}
        className="bg-yellow-500 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-yellow-600 transition-colors flex items-center"
      >
        <IconPencil /> Přejít na procvičování
      </button>
    </div>
  </div>
);

// --- Přepracovaná PracticePage s integrací Gemini ---

// Helper funkce pro API volání s exponenciálním zpožděním
async function fetchWithBackoff(url, options, retries = 3, delay = 1000) {
  try {
    const response = await fetch(url, options);
    if (!response.ok) {
      if (response.status >= 500 && retries > 0) {
        console.warn(`API call failed with status ${response.status}. Retrying in ${delay}ms...`);
        await new Promise(res => setTimeout(res, delay));
        return fetchWithBackoff(url, options, retries - 1, delay * 2);
      }
      throw new Error(`API call failed with status ${response.status}`);
    }
    return response.json();
  } catch (error) {
    if (retries > 0) {
      console.warn(`API call failed: ${error.message}. Retrying in ${delay}ms...`);
      await new Promise(res => setTimeout(res, delay));
      return fetchWithBackoff(url, options, retries - 1, delay * 2);
    }
    console.error("API call failed after multiple retries:", error);
    throw error;
  }
}

const PracticePage = ({ lesson, onNavClick }) => {
  const [questions, setQuestions] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  const [answers, setAnswers] = useState({});
  const [showResults, setShowResults] = useState(false);

  // Schema pro JSON odpověď od Gemini
  const responseSchema = {
    type: "ARRAY",
    items: {
      type: "OBJECT",
      properties: {
        "question": { "type": "STRING" },
        "options": {
          type: "ARRAY",
          items: { "type": "STRING" },
          minItems: 4,
          maxItems: 4
        },
        "correctAnswer": { "type": "STRING" }
      },
      required: ["question", "options", "correctAnswer"]
    }
  };

  // Funkce pro generování otázek
  const generatePracticeQuestions = async (lessonTitle) => {
    setLoading(true);
    setError(null);
    setAnswers({});
    setShowResults(false);
    setQuestions([]);

    const apiKey = ""; // API klíč bude doplněn prostředím
    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;

    const systemPrompt = "Jsi asistent pro tvorbu kvízů specializovaný na latinskou lékařskou terminologii. Vytvářej otázky v češtině. Ujisti se, že jedna z 'options' přesně odpovídá 'correctAnswer'.";
    const userQuery = `Vytvoř 5 kvízových otázek (multiple choice, 4 možnosti) na téma: '${lessonTitle}'. Otázky musí být v češtině.`;

    const payload = {
      systemInstruction: {
        parts: [{ text: systemPrompt }]
      },
      contents: [{
        parts: [{ text: userQuery }]
      }],
      generationConfig: {
        responseMimeType: "application/json",
        responseSchema: responseSchema,
        temperature: 0.8 // Mírná kreativita pro různé otázky
      }
    };

    try {
      const result = await fetchWithBackoff(apiUrl, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payload)
      });

      if (result.candidates && result.candidates[0].content && result.candidates[0].content.parts[0].text) {
        const generatedQuestions = JSON.parse(result.candidates[0].content.parts[0].text);
        
        // Ověření, zda correctAnswer je jednou z options
        const validatedQuestions = generatedQuestions.filter(
          q => q.options && q.options.includes(q.correctAnswer)
        );
        
        setQuestions(validatedQuestions);
        if (validatedQuestions.length === 0) {
            setError("Nepodařilo se vygenerovat platné otázky. Zkuste to prosím znovu.");
        }
      } else {
        throw new Error("Neplatná struktura odpovědi od API.");
      }
    } catch (err) {
      console.error("Chyba při generování otázek:", err);
      setError("Při generování otázek nastala chyba. Zkuste to prosím znovu.");
    } finally {
      setLoading(false);
    }
  };

  // Spustit generování při změně lekce
  useEffect(() => {
    if (lesson) {
      generatePracticeQuestions(lesson.title);
    }
  }, [lesson]);

  const handleAnswerChange = (questionText, answer) => {
    setAnswers({
      ...answers,
      [questionText]: answer,
    });
  };

  const checkAnswers = () => {
    setShowResults(true);
  };

  const resetPractice = () => {
    // Znovu vygeneruje otázky
    generatePracticeQuestions(lesson.title);
  };

  const getButtonClass = (question, option) => {
    if (!showResults) {
      return answers[question.question] === option 
        ? 'bg-blue-100 border-blue-500' 
        : 'bg-white border-gray-300';
    }
    
    if (option === question.correctAnswer) {
      return 'bg-green-100 border-green-500 text-green-800 font-semibold';
    }
    
    if (answers[question.question] === option && option !== question.correctAnswer) {
      return 'bg-red-100 border-red-500 text-red-800';
    }

    return 'bg-white border-gray-300';
  };
  
  const score = showResults 
    ? questions.reduce((acc, q) => acc + (answers[q.question] === q.correctAnswer ? 1 : 0), 0)
    : 0;

  return (
    <div className="bg-white p-6 rounded-lg shadow-lg">
      <button onClick={() => onNavClick('lesson_overview')} className="text-blue-600 hover:text-blue-800 mb-4 flex items-center text-sm">
        <IconChevronLeft /> Zpět na přehled lekcí
      </button>
      <h2 className="text-3xl font-bold text-gray-800 mb-6">{lesson.title} - Procvičování (Generováno AI)</h2>
      
      {loading && (
        <div className="flex items-center justify-center h-64">
          <IconLoading />
          <span className="text-lg text-gray-600">Generuji nové otázky...</span>
        </div>
      )}

      {error && (
        <div className="bg-red-100 border-l-4 border-red-500 text-red-800 p-4 rounded-md">
          <p className="font-semibold">Chyba</p>
          <p>{error}</p>
          <button
            onClick={resetPractice}
            className="mt-2 bg-red-600 text-white px-4 py-2 rounded-lg text-sm font-semibold hover:bg-red-700 transition-colors"
          >
            Zkusit znovu
          </button>
        </div>
      )}

      {!loading && !error && questions.length > 0 && (
        <>
          <div className="space-y-6">
            {questions.map((q, index) => (
              <div key={index} className="border border-gray-200 p-4 rounded-lg">
                <p className="font-semibold text-gray-800 mb-3">{index + 1}. {q.question}</p>
                <div className="space-y-2">
                  {q.options.map((option, i) => (
                    <button
                      key={i}
                      onClick={() => !showResults && handleAnswerChange(q.question, option)}
                      disabled={showResults}
                      className={`block w-full text-left p-3 rounded-lg border ${getButtonClass(q, option)} transition-colors ${!showResults ? 'hover:bg-gray-50' : 'cursor-not-allowed'}`}
                    >
                      {option}
                    </button>
                  ))}
                </div>
              </div>
            ))}
          </div>

          <div className="mt-8 pt-6 border-t">
            {!showResults ? (
              <button
                onClick={checkAnswers}
                className="bg-blue-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors"
              >
                Zkontrolovat odpovědi
              </button>
            ) : (
              <div className="flex flex-col md:flex-row justify-between items-center gap-4">
                <div className="text-xl font-bold p-4 rounded-lg bg-gray-100">
                  Vaše skóre: <span className="text-blue-700">{score} / {questions.length}</span>
                </div>
                <button
                  onClick={resetPractice}
                  className="bg-gray-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-gray-700 transition-colors"
                >
                  Nové otázky
                </button>
              </div>
            )}
          </div>
        </>
      )}
    </div>
  );
};

const TestPage = ({ onNavClick }) => {
  const [currentQuestionIndex, setCurrentQuestionIndex] = useState(0);
  const [score, setScore] = useState(0);
  const [showScore, setShowScore] = useState(false);
  const [selectedAnswer, setSelectedAnswer] = useState(null);
  const [isAnswered, setIsAnswered] = useState(false);

  const questions = appData.test;
  const currentQuestion = questions[currentQuestionIndex];

  const handleAnswerClick = (answer) => {
    if (isAnswered) return; // Nedovolit změnu odpovědi
    
    setSelectedAnswer(answer);
    setIsAnswered(true);

    if (answer === currentQuestion.correctAnswer) {
      setScore(score + 1);
    }
    
    // Automaticky přejít na další otázku po krátké pauze
    setTimeout(() => {
      const nextQuestion = currentQuestionIndex + 1;
      if (nextQuestion < questions.length) {
        setCurrentQuestionIndex(nextQuestion);
        setSelectedAnswer(null); // Reset výběru
        setIsAnswered(false); // Povolit odpověď
      } else {
        setShowScore(true);
      }
    }, 1500); // 1.5 sekundy na zobrazení správné/špatné odpovědi
  };
  
  const getButtonClass = (option) => {
    if (!isAnswered) {
      return 'bg-white border-gray-300 hover:bg-gray-50';
    }
    
    if (option === currentQuestion.correctAnswer) {
      return 'bg-green-100 border-green-500 text-green-800 font-semibold';
    }
    
    if (selectedAnswer === option && option !== currentQuestion.correctAnswer) {
      return 'bg-red-100 border-red-500 text-red-800';
    }

    return 'bg-white border-gray-300';
  };

  const restartTest = () => {
    setCurrentQuestionIndex(0);
    setScore(0);
    setShowScore(false);
    setSelectedAnswer(null);
    setIsAnswered(false);
  };

  return (
    <div className="bg-white p-6 rounded-lg shadow-lg max-w-2xl mx-auto">
      <h2 className="text-3xl font-bold text-gray-800 mb-6">Závěrečný test</h2>
      
      {showScore ? (
        <div className="text-center">
          <h3 className="text-2xl font-semibold mb-4">Test dokončen!</h3>
          <p className="text-4xl font-bold text-blue-700 p-6 bg-gray-100 rounded-lg">
            Vaše skóre: {score} / {questions.length}
          </p>
          <button
            onClick={restartTest}
            className="mt-8 bg-blue-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors"
          >
            Opakovat test
          </button>
        </div>
      ) : (
        <div>
          <div className="mb-4">
            <p className="text-sm text-gray-500">Otázka {currentQuestionIndex + 1} z {questions.length}</p>
            <h3 className="text-xl font-semibold text-gray-800 mt-1">{currentQuestion.question}</h3>
          </div>
          <div className="space-y-3">
            {currentQuestion.options.map((option, i) => (
              <button
                key={i}
                onClick={() => handleAnswerClick(option)}
                disabled={isAnswered}
                className={`block w-full text-left p-4 rounded-lg border ${getButtonClass(option)} transition-colors ${isAnswered ? 'cursor-not-allowed' : ''}`}
              >
                {option}
              </button>
            ))}
          </div>
        </div>
      )}
    </div>
  );
};


// --- Hlavní komponenta aplikace ---

function App() {
  const [currentPage, setCurrentPage] = useState('home');
  const [currentLessonId, setCurrentLessonId] = useState(null);

  const handleNavClick = (page, lessonId = null) => {
    setCurrentPage(page);
    setCurrentLessonId(lessonId);
  };

  const renderPage = () => {
    const lesson = currentLessonId ? appData.lessons.find(l => l.id === currentLessonId) : null;
    
    switch (currentPage) {
      case 'home':
        return <HomePage />;
      case 'lesson_overview':
        return <LessonOverviewPage lessons={appData.lessons} onNavClick={handleNavClick} />;
      case 'lesson':
        return lesson ? <LessonPage lesson={lesson} onNavClick={handleNavClick} /> : <LessonOverviewPage lessons={appData.lessons} onNavClick={handleNavClick} />;
      case 'vocabulary':
        return lesson ? <VocabularyPage lesson={lesson} onNavClick={handleNavClick} /> : <LessonOverviewPage lessons={appData.lessons} onNavClick={handleNavClick} />;
      case 'practice':
        return lesson ? <PracticePage lesson={lesson} onNavClick={handleNavClick} /> : <LessonOverviewPage lessons={appData.lessons} onNavClick={handleNavClick} />;
      case 'test':
        return <TestPage onNavClick={handleNavClick} />;
      default:
        return <HomePage />;
    }
  };

  return (
    <div className="flex flex-col min-h-screen bg-gray-100 font-inter">
      <Header title="Základy latinské lékařské terminologie" />
      <div className="flex flex-1 flex-col md:flex-row">
        <Sidebar onNavClick={handleNavClick} lessons={appData.lessons} />
        <main className="flex-1 p-4 md:p-8 overflow-auto">
          {renderPage()}
        </main>
      </div>
      <Footer />
    </div>
  );
}

export default App;
