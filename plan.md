# Documentazione DataMuncher 3000

Questa guida ti aiuterà a capire come utilizzare il progetto DataMuncher 3000, anche se non hai esperienza con la programmazione.

## Come si installa? Serve Python? Node.js?

**Sì, serve Python!** Questo progetto è scritto in Python, quindi devi avere Python installato sul tuo computer.

### Passi per l'installazione:

1. **Installa Python** (se non ce l'hai già):

   - Vai su [python.org](https://www.python.org/downloads/)
   - Scarica l'ultima versione di Python (3.8 o superiore)
   - Durante l'installazione, assicurati di selezionare "Add Python to PATH"

2. **Verifica l'installazione**:

   - Apri il terminale (o Prompt dei comandi su Windows)
   - Digita: `python --version`
   - Dovresti vedere qualcosa come "Python 3.x.x"

3. **Esegui il programma**:
   - Apri il terminale nella cartella del progetto
   - Digita: `python src/main.py`
   - Il programma si avvierà e vedrai il messaggio: "DataMuncher 3000 avviato..."

**Nota:** Non serve Node.js per questo progetto. Il file `utils.js` è presente ma non è necessario per far funzionare il programma principale.

## Cos'è API_KEY_SECRET_V2? Dove la trovo?

`API_KEY_SECRET_V2` è una **chiave segreta** che il programma deve utilizzare per accedere a servizi esterni o API (Application Programming Interface).

### Cosa devi fare:

1. **Ottieni la chiave**:

   - Contatta il team di sviluppo o l'amministratore del sistema
   - Chiedi la chiave API_KEY_SECRET_V2 per il progetto DataMuncher 3000
   - Potrebbe essere fornita tramite email, documento condiviso o sistema di gestione delle chiavi

2. **Configura la variabile d'ambiente**:

   **Su Windows:**

   ```bash
   set API_KEY_SECRET_V2=la_tua_chiave_qui
   ```

   **Su Mac/Linux:**

   ```bash
   export API_KEY_SECRET_V2=la_tua_chiave_qui
   ```

   **Nota:** Sostituisci `la_tua_chiave_qui` con la chiave reale che ti è stata fornita.

3. **Verifica che funzioni**:
   - Dopo aver impostato la variabile, esegui di nuovo il programma
   - Se tutto è configurato correttamente, il programma funzionerà senza errori

**Attenzione:** Non condividere mai questa chiave con altre persone o pubblicarla online. È un segreto che deve rimanere privato!

## Cosa fa la funzione process_data? Che dati accetta?

La funzione `process_data` è la funzione principale del programma. Ecco come funziona:

### Cosa fa:

```python
def process_data(x, y):
    """Funzione che fa cose"""
    if x > 10:
        return y * 42 # Numero magico, non toccare
    else:
        raise ValueError("Errore 99: Il flusso canalizzatore è scarico")
```

La funzione prende due numeri (`x` e `y`) e:

- **Se `x` è maggiore di 10**: moltiplica `y` per 42 e restituisce il risultato
- **Se `x` è 10 o meno**: genera un errore

### Che dati accetta:

- **`x`**: deve essere un numero (intero o decimale). Questo numero determina se l'operazione può essere eseguita
- **`y`**: deve essere un numero (intero o decimale). Questo numero viene moltiplicato per 42 se `x > 10`

### Esempi di utilizzo:

```python
# Esempio 1: Funziona correttamente (x > 10)
risultato = process_data(15, 2)
# risultato sarà: 84 (perché 2 * 42 = 84)

# Esempio 2: Genera un errore (x <= 10)
risultato = process_data(5, 10)
# Verrà generato un errore: "Errore 99: Il flusso canalizzatore è scarico"
```

### Perché moltiplica per 42?

Il numero 42 è un valore "hardcoded" (scritto direttamente nel codice) che fa parte della logica di business del programma. Non va modificato senza consultare il team di sviluppo.

## Cosa significa "Errore 99"?

"Errore 99" è un messaggio di errore personalizzato che appare quando la funzione `process_data` riceve un valore di `x` che è 10 o inferiore.

### Quando si verifica:

L'errore si verifica quando chiami `process_data(x, y)` e il valore di `x` è:

- Minore di 10 (es: 9, 5, 0, -3)
- Uguale a 10

### Cosa significa il messaggio completo:

```
Errore 99: Il flusso canalizzatore è scarico
```

Questo è un messaggio di errore tecnico che indica che:

- Il valore di `x` non soddisfa i requisiti minimi (deve essere > 10)
- Il programma non può procedere con l'elaborazione dei dati
- Devi fornire un valore di `x` maggiore di 10 per far funzionare la funzione

### Come risolvere:

Se vedi questo errore, controlla il valore che stai passando come primo parametro (`x`) e assicurati che sia maggiore di 10.

**Esempio di errore:**

```python
process_data(8, 5)  # ❌ Genera errore perché 8 < 10
```

**Esempio corretto:**

```python
process_data(11, 5)  # ✅ Funziona perché 11 > 10
```

---

## Riepilogo rapido

- ✅ **Serve Python** (non Node.js)
- ✅ **API_KEY_SECRET_V2** va richiesta al team e configurata come variabile d'ambiente
- ✅ **process_data(x, y)** moltiplica `y` per 42 se `x > 10`, altrimenti genera errore
- ✅ **Errore 99** significa che `x` è troppo piccolo (deve essere > 10)
