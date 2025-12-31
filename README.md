Questo repository contiene l'implementazione del progetto **DiffTexture-SR**, una pipeline basata su **Stable Diffusion** per la generazione controllata di texture non-stazionarie. 

Il sistema utilizza tecniche di **Self-Rectification** e **MasaCtrl** (Mutual Self-Attention Control) per permettere all'utente di controllare scala e rotazione della texture generata tramite un semplice collage di input ("lazy edit"), superando i limiti dell'inpainting tradizionale.

## Caratteristiche
* **Controllo Strutturale:** Generazione guidata da collage grezzi ruotati e scalati.
* **Architettura:** Integrazione di MasaCtrl nella U-Net di Stable Diffusion per l'iniezione di feature (Key/Value) dal riferimento.
* **Pipeline a due stadi:** Approccio *Coarse-to-Fine* per garantire coerenza globale e dettagli locali.
* **Data Augmentation:** Supporto automatico per rotazioni e mirroring dei riferimenti.

## Dataset e Immagini
Le immagini di texture (riferimenti) e i collage di target utilizzati per i test sono disponibili al seguente link:

**[Scarica il Dataset da Google Drive](https://drive.google.com/drive/folders/1MLGhUwQu4q1FHPfHCe_2CDacDt83-kUg?usp=sharing)**

### Come utilizzare le immagini
Il codice è configurato per funzionare su Google Colab montando Google Drive. Per riprodurre i risultati:

1.  **Scarica** la cartella dal link Drive sopra indicato.
2.  **Carica** la cartella nel tuo Google Drive personale (es. nella root o in una sottocartella).
3.  Nel notebook/script, individua la variabile `path_dir` (generalmente all'inizio del codice) e aggiornala con il percorso della cartella nel tuo Drive:
    ```python
    # Esempio
    path_dir = '/content/drive/MyDrive/images/' 
    ```
4.  Assicurati che la struttura delle cartelle interna (`refs`, ecc.) rimanga inalterata.

## Installazione e Utilizzo
Il progetto è ottimizzato per **Google Colab** (GPU T4 o superiore consigliata).

1.  Clona il repository o scarica il notebook `.ipynb`.
2.  Installa le dipendenze necessarie (già incluse nella prima cella del notebook):
    ```bash
    pip install diffusers transformers xformers accelerate torch opencv-python
    ```
3.  Esegui le celle sequenzialmente per avviare la pipeline di Self-Rectification.

## 👥 Autori
* **Matteo Battilori**
* **Marco Michellini**

## Riferimenti
Basato sul paper:
* *Generating Non-Stationary Textures using Self-Rectification* (Xiao et al., 2024)
