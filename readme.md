# Dotfiles Backup and Restore Scripts

Questo repository contiene una serie di script per gestire il backup, il ripristino e l'annullamento del ripristino dei tuoi dotfiles (file e directory che iniziano con un punto `.`) e altre configurazioni personali. Inoltre, include uno script per aggiungere alias al file `.zshrc` per semplificare l'esecuzione degli script.

---

## 📋 Contenuto del repository

1. **`backup-config.sh`**  
   Script per creare un backup dei tuoi dotfiles e configurazioni personali, escludendo file e directory specifici.

2. **`restore-config.sh`**  
   Script per ripristinare i dotfiles e le configurazioni personali dalla directory di backup.

3. **`undo-restore.sh`**  
   Script per annullare un ripristino, eliminando i file e le directory ripristinati.

4. **`add-alias.sh`**  
   Script per aggiungere alias al file `.zshrc`, semplificando l'esecuzione degli script tramite comandi brevi.

---

## 🛠️ Requisiti

- **Sistema operativo**: macOS o Linux.
- **Shell**: Zsh (necessario per il file `.zshrc`).
- **Strumenti richiesti**:
  - `rsync` per il backup e il ripristino.
  - `tac` per invertire l'ordine delle righe (disponibile su Linux; su macOS può essere installato con Homebrew: `brew install coreutils`).

---

## 🚀 Come utilizzare gli script

### 1. **Backup dei dotfiles**

Lo script `backup-config.sh` crea un backup dei tuoi dotfiles nella directory `~/Desktop/backup-configs`.

#### Esecuzione:
```bash
bash backup-config.sh
```

#### Cosa fa:
- Copia tutti i file e le directory che iniziano con un punto (`.*`) dalla tua home directory (`$HOME`) nella directory di destinazione.
- Esclude file e directory specifici definiti nella variabile `EXCLUDE`.

#### Output:
- I file di backup saranno salvati in `~/Desktop/backup-configs`.

---

### 2. **Ripristino dei dotfiles**

Lo script `restore-config.sh` ripristina i dotfiles dalla directory di backup alla tua home directory.

#### Esecuzione:
```bash
bash restore-config.sh
```

#### Cosa fa:
- Copia i file dalla directory `~/Desktop/backup-configs` alla tua home directory (`$HOME`).
- Registra i file ripristinati in un file di log: `~/restore-log.txt`.

#### Output:
- I file ripristinati saranno visibili nella tua home directory.
- Un file di log (`restore-log.txt`) sarà creato per tenere traccia dei file ripristinati.

---

### 3. **Annullamento del ripristino**

Lo script `undo-restore.sh` elimina i file e le directory ripristinati, utilizzando il file di log generato durante il ripristino.

#### Esecuzione:
```bash
bash undo-restore.sh
```

#### Cosa fa:
- Legge il file di log `~/restore-log.txt`.
- Elimina i file e le directory elencati nel log, in ordine inverso (prima i file, poi le directory vuote).

#### Output:
- I file e le directory ripristinati saranno eliminati.
- Il file di log sarà rimosso.

---

### 4. **Aggiunta di alias**

Lo script `add-alias.sh` aggiunge alias al file `.zshrc` per semplificare l'esecuzione degli script.

#### Esecuzione:
```bash
bash add-alias.sh
```

#### Cosa fa:
- Aggiunge i seguenti alias al file `.zshrc`:
  - `backup-config`: esegue `backup-config.sh`.
  - `restore-config`: esegue `restore-config.sh`.
  - `undo-restore`: esegue `undo-restore.sh`.
- Ricarica il file `.zshrc` per rendere immediatamente disponibili gli alias.

#### Alias disponibili:
- `backup-config`: Avvia il backup dei dotfiles.
- `restore-config`: Avvia il ripristino dei dotfiles.
- `undo-restore`: Annulla il ripristino dei dotfiles.

---

## 📂 Struttura dei file

- **`backup-config.sh`**: Script per il backup.
- **`restore-config.sh`**: Script per il ripristino.
- **`undo-restore.sh`**: Script per annullare il ripristino.
- **`add-alias.sh`**: Script per aggiungere alias.
- **`restore-log.txt`**: File di log generato durante il ripristino (creato automaticamente).

---

## ⚠️ Note importanti

1. **Esclusioni nel backup**:
   - Lo script `backup-config.sh` esclude alcune directory e file specifici (es. `.cache`, `.local`, `Downloads`, ecc.). Puoi personalizzare la lista modificando la variabile `EXCLUDE` nello script.

2. **Conferme richieste**:
   - Gli script `restore-config.sh` e `undo-restore.sh` richiedono una conferma prima di procedere.

3. **Compatibilità**:
   - Gli script sono progettati per funzionare su macOS e Linux. Su macOS, potrebbe essere necessario installare `tac` tramite Homebrew.

4. **Backup sicuro**:
   - Assicurati di verificare i file di backup prima di eseguire il ripristino o l'annullamento.

---

## 🧹 Personalizzazione

- **Modifica dei percorsi degli script**:
  - Puoi modificare i percorsi degli script (`BACKUP_SCRIPT_PATH`, `RESTORE_SCRIPT_PATH`, `UNDO_SCRIPT_PATH`) nello script `add-alias.sh` per adattarli alla tua configurazione.

- **Esclusioni personalizzate**:
  - Modifica la variabile `EXCLUDE` in `backup-config.sh` per aggiungere o rimuovere file/directory da escludere.

---

## ✅ Esempio di utilizzo

1. Esegui il backup:
   ```bash
   backup-config
   ```

2. Ripristina i file:
   ```bash
   restore-config
   ```

3. Annulla il ripristino:
   ```bash
   undo-restore
   ```

---