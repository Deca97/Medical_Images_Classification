Il progetto consiste nello sviluppo di un sistema di Computer Vision basato su Deep Learning per la classificazione automatica di lesioni cutanee, con l'obiettivo di supportare la diagnosi precoce di neoplasie come il melanoma.


1. Il Dataset: DermaMNIST
Il progetto utilizza DermaMNIST, un dataset clinico standardizzato derivato dalla collezione HAM10000. Include migliaia di immagini dermatoscopiche suddivise in 7 categorie patologiche, tra cui:


2. Architettura e Strategia di Apprendimento
Il sistema sfrutta il Transfer Learning utilizzando una rete neurale ResNet18 pre-addestrata su ImageNet. La strategia di training è di tipo "progressivo":

Fase 1 (Feature Extraction): Il "corpo" della rete (backbone) viene congelato e si addestra solo lo strato finale (head). Questo permette di adattare il modello alle nuove classi senza corrompere le conoscenze geometriche già acquisite.

Fase 2 (Fine-Tuning Totale): Una volta raggiunto un plateau di performance (gestito tramite Early Stopping), la rete viene interamente sbloccata. Viene applicato un learning rate molto basso per rifinire i filtri convoluzionali e catturare i dettagli microscopici specifici delle texture tumorali.

3. Valutazione Medica
Oltre all'accuratezza globale, il progetto pone l'accento sulla Matrice di Confusione e sul Report di Classificazione (Precision, Recall, F1-Score). In ambito medico, questo è cruciale per monitorare i Falsi Negativi: confondere un melanoma per un nevo benigno è l'errore che il modello cerca di minimizzare attraverso l'ottimizzazione dei pesi.
