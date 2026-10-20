# Observations — Ruinion AI

## Ce que l'interface annonce
Ruinion AI propose l'enregistrement depuis le microphone ou l'importation d'un fichier MP3, WAV, M4A ou WEBM (limite affichée : 500 Mo), puis la génération d'une transcription, d'un résumé, d'un compte rendu, des actions/décisions et d'un document Word. Les formats et la limite sont des indications de l'interface, pas des validations techniques.

## TEST-001 — Enregistrement audio depuis le microphone
**Date :** 20 octobre 2026  
**Environnement :** navigateur mobile Android, utilisateur connecté.  
**Statut :** PASS pour l'enregistrement et l'écoute, selon les observations transmises.

- Un enregistrement de 22 secondes a été obtenu.
- L'interface proposait la lecture et le téléchargement.
- L'auditeur a confirmé que la voix était audible et le texte compréhensible.

**Limite :** cela ne valide pas à lui seul la transcription ni la qualité des contenus générés.

## TEST-002 — Génération et affichage des résultats
**Date :** 20 octobre 2026  
**Statut :** PASS pour l'obtention et l'affichage d'une transcription ; contrôle qualité partiel en cours.

### Résultats visibles
- La réunion « Réunion commerciale » affiche le statut « Terminé ».
- Durée audio affichée : 0:22.
- Onglets visibles : « Transcription », « Résumé » et « Compte rendu ».
- La transcription comporte des segments horodatés :
  - 00:01 — « Bonjour, nous organisons une réunion commerciale le lundi 26 octobre. »
  - 00:08 — « Monsieur Ibrahim prépare une proposition tarifaire avant vendredi. »
  - 00:13 — « Jonathan valide le budget de 500 euros. »
  - 00:17 — « Nous décidons de faire un point de suivi lundi prochain. »
- Un bouton « Télécharger le Word » est visible.
- Le lecteur audio et la section Participants (1 participant : Bordeaux Lancer) sont affichés.

### Comparaison avec le texte de référence prononcé
Le texte de référence contenait :
1. Réunion commerciale le lundi 26 octobre.
2. Ibrahim prépare une proposition tarifaire avant vendredi.
3. Jonathan valide un budget de 500 euros.
4. Un point de suivi mardi prochain.

La transcription affichée reprend les quatre idées principales. Deux différences sont à noter :
- « Ibrahim » apparaît comme « Monsieur Ibrahim ».
- « mardi prochain » apparaît comme « lundi prochain ».

La première différence peut être une reformulation bénigne. La seconde est une divergence factuelle entre le texte de référence et la transcription affichée, mais il faut confirmer ce qui a réellement été prononcé et écouter le segment audio correspondant avant de qualifier une anomalie. À ce stade, elle est enregistrée comme **point à vérifier**, pas comme bug confirmé.

### Prochaine vérification
Écouter le segment autour de 00:17 et confirmer si l'audio dit « mardi prochain » ou « lundi prochain ». Puis ouvrir l'onglet « Résumé » et l'onglet « Compte rendu » pour examiner la fidélité des contenus.

### Preuves
Captures d'écran fournies par l'auditeur le 20 octobre 2026. Elles ne sont pas copiées dans le repository public ; les descriptions ci-dessus résument les éléments visibles.
