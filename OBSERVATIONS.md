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

**Source :** deux captures fournies par l'auditeur, 20 octobre 2026.

### Faits visibles
- Un bouton « Enregistrer » avec un compteur à 00:00:00.
- Une zone d'importation audio indiquant les formats MP3, WAV, M4A et WEBM, avec une taille maximale affichée de 500 Mo.
- Une section « Pipeline de traitement » listant la transcription, le résumé court, le compte rendu détaillé, l'identification des actions et décisions, et le document Word.
- Un état « Aucun audio sélectionné ».
- Le bouton « Générer les résumés » apparaît désactivé lorsque aucun audio n'est sélectionné.

### Valeur pour l'utilisateur
L'interface annonce un parcours complet allant de l'audio au compte rendu et au document Word. L'audit devra vérifier si ce parcours fonctionne avec un fichier de référence et si le contenu généré est fidèle à l'audio.

### Limites
- Les formats et la limite de 500 Mo sont des indications affichées par l'interface, pas des validations techniques effectuées.
- Le bouton de génération désactivé en l'absence d'audio paraît cohérent avec le message affiché ; aucune anomalie n'est déclarée.
- Aucun test d'enregistrement, d'importation ou de génération n'a encore été exécuté.
