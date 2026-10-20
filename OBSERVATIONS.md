# Observations — Ruinion AI

## OBS-006 — Page « Nouvelle réunion »

**Source :** capture fournie par l'auditeur, 20 octobre 2026.  
**Contexte :** utilisateur connecté sur navigateur mobile Android.

### Faits visibles
- Page intitulée « Nouvelle réunion ».
- Le texte présente le parcours : capturer l'audio, obtenir une transcription, puis générer un résumé court et un compte rendu détaillé.
- Champ « Titre de la réunion » prérempli avec « Réunion commerciale ».
- Section facultative d'invitation de membres.
- L'interface indique qu'aucun autre membre actif n'est présent dans l'équipe et affiche 0 membre sélectionné, 100 maximum.

Ces éléments décrivent l'interface uniquement. Le comportement de création n'a pas encore été testé.

## OBS-007 — Options audio et pipeline annoncé

**Source :** captures fournies par l'auditeur, 20 octobre 2026.

### Faits visibles
- Un bouton « Enregistrer » avec un compteur à 00:00:00.
- Une zone d'importation audio indiquant les formats MP3, WAV, M4A et WEBM, avec une taille maximale affichée de 500 Mo.
- Une section « Pipeline de traitement » listant la transcription, le résumé court, le compte rendu détaillé, l'identification des actions et décisions, et le document Word.
- Un état « Aucun audio sélectionné ».
- Le bouton « Générer les résumés » apparaît désactivé lorsque aucun audio n'est sélectionné.

### Limites
Les formats et la limite de 500 Mo sont des indications d'interface, pas des validations techniques. Aucun test d'importation ou de génération n'a encore été exécuté.

## TEST-001 — Enregistrement audio depuis le microphone

**Date :** 20 octobre 2026  
**Environnement :** navigateur mobile Android, utilisateur connecté.  
**Statut :** PASS — enregistrement effectué et audio prêt à être vérifié.

### Action réalisée
L'auditeur a lancé un enregistrement depuis le microphone et l'interface affiche ensuite un état « Votre audio est prêt ».

### Résultat observé
- Durée affichée : 00:00:22.
- Contrôle de lecture audio disponible.
- Lien « Télécharger l'audio » visible.
- Actions « Reprendre » et « Supprimer » visibles.
- Message indiquant que le brouillon est sauvegardé sur cet appareil à la dernière pause.
- L'interface demande de vérifier l'audio avant de lancer la génération.

### Conclusion limitée
La capture confirme qu'un enregistrement de 22 secondes a été obtenu et qu'un aperçu audio est proposé. Elle ne prouve pas encore que le son est intelligible, que le brouillon survit à une reconnexion, ni que la transcription et la génération fonctionnent.

### Preuve
Capture fournie dans la conversation le 20 octobre 2026. Le fichier original est conservé dans la conversation ; aucune capture n'est publiée dans ce repository à ce stade.
