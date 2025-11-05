 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..d0d0dcc90f50b99bc0a5ae5c251aab50f0d27b76
--- /dev/null
+++ b/README.md
@@ -0,0 +1,34 @@
+# Simulatore Budget Stagionale
+
+Questa applicazione web consente di stimare il budget stagionale di un team ciclistico partendo da un modello di costi fisso/variabile archiviato in JSON. L'interfaccia unica (`index.html`) carica i valori di default da `data/default_costs.json`, permette di modificarli, confronta lo scenario base con l'opzione "con Eviso" e genera grafici, riepiloghi e report esportabili.
+
+## Cosa è stato realizzato
+- **Modello dati JSON** con costi fissi, variabili e parametri di default facilmente aggiornabili.
+- **Motore di calcolo client-side** in JavaScript che aggrega i costi per gara, applica le percentuali di risparmio e aggiorna grafici a barre e a torta in tempo reale.
+- **Interfaccia responsive** per inserire scenari, modificare le voci di costo e confrontare i totali con/senza Eviso, comprensiva di pulsanti per esportare PDF e CSV.
+- **Note operative** su come mantenere l'elenco costi direttamente nella pagina e nel file JSON.
+
+## Esecuzione locale
+1. Installare un server statico a scelta (ad esempio Python è già disponibile).
+2. Avviare il server dalla cartella del progetto:
+   ```bash
+   python -m http.server 8000
+   ```
+3. Aprire un browser e visitare `http://localhost:8000/` per utilizzare il simulatore.
+
+## Distribuzione online
+- **GitHub Pages**: creare un repository pubblico, caricare questi file e attivare GitHub Pages dal branch `main`. La pagina sarà raggiungibile all'URL `https://<utente>.github.io/<repo>/`.
+- **Netlify / Vercel**: importare il repository e configurare un deploy statico, indicando la root del progetto come directory di pubblicazione.
+- **Qualsiasi hosting statico** (es. S3, Firebase Hosting): caricare `index.html`, la cartella `data/` e l'immagine `logo_uci_continental.png` mantenendo la stessa struttura di cartelle.
+
+## Verifica del funzionamento
+1. Aprire la pagina ospitata (locale o online) e assicurarsi che i grafici e i totali vengano popolati automaticamente con i dati di default.
+2. Modificare un parametro, ad esempio il numero di gare, e confermare che i riepiloghi stagionali e i grafici si aggiornino.
+3. Usare i pulsanti "Esporta CSV" e "Esporta PDF" per scaricare i report e aprirli per verificarne il contenuto.
+4. (Opzionale) Aggiornare `data/default_costs.json`, ricaricare la pagina e controllare che i nuovi valori vengano applicati.
+
+## Manutenzione
+- Per modificare i costi o aggiungere nuove voci, aggiornare `data/default_costs.json` mantenendo la struttura `fixed_costs`/`variable_costs`.
+- I testi delle sezioni informative e le note per gli utenti si trovano in coda al file `index.html`.
+- Eseguire `python -m json.tool data/default_costs.json` per validare il formato del file JSON dopo ogni modifica.
+
 
EOF
)
