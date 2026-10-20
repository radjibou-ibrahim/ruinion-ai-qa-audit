# Résultats de l'audit — Ruinion AI

## Objectif
Vérifier des parcours représentatifs et relever uniquement les écarts appuyés par des observations réelles. Les captures sont conservées dans la conversation et ne sont pas publiées dans ce repository.

## TEST-001 — Enregistrement audio depuis le microphone
**Date :** 20 octobre 2026 · **Environnement :** navigateur mobile Android  
**Statut : PASS pour l'enregistrement et l'écoute**
- Un enregistrement de 22 secondes a été obtenu.
- L'auditeur confirme que la voix est audible et compréhensible.
- La lecture et le téléchargement de l'audio sont proposés.

## TEST-002 — Transcription de l'audio
**Statut : FAIL — divergence factuelle confirmée par l'auditeur.**
- **Référence prononcée :** « Nous décidons de faire un point de suivi mardi prochain. »
- **Transcription affichée :** « Nous décidons de faire un point de suivi lundi prochain. »
- **Impact potentiel :** une échéance modifiée peut entraîner une confusion ou un suivi manqué.
- **Sévérité proposée :** Moyenne. **Priorité proposée :** P1, à confirmer avec le développeur selon la fréquence et les usages.
- **Preuve :** capture de la transcription et confirmation de l'auditeur. Le fichier audio n'est pas publié dans le repository.

## TEST-003 — Résumé court
**Statut : examen partiel effectué.**
Le résumé reprend les informations principales : réunion commerciale prévue le lundi 26 octobre 2026, proposition tarifaire d'Ibrahim avant vendredi, budget de 500 euros validé par Jonathan, point de suivi prévu « lundi prochain » et responsable non précisé.

Le résumé reproduit la divergence de date observée dans la transcription. Il s'agit vraisemblablement de la propagation du même écart et non d'une anomalie indépendante. L'absence de responsable n'est pas qualifiée de bug sans règle métier confirmant qu'un responsable devait être déduit.

## TEST-004 — Compte rendu détaillé
**Statut : EXAMINÉ — fidélité partielle ; divergence de date propagée.**
### Éléments observés
- Résumé long : réunion commerciale prévue le lundi 26 octobre 2026 ; proposition tarifaire à préparer par Monsieur Ibrahim avant vendredi ; budget de 500 euros validé par Jonathan ; point de suivi annoncé « lundi prochain ».
- Points importants : les informations principales sont reprises.
- Décisions : organiser la réunion commerciale, valider le budget de 500 euros sous la responsabilité de Jonathan, prévoir un point de suivi « lundi prochain ».
- Actions : préparer une proposition tarifaire (responsable : Monsieur Ibrahim ; échéance : avant vendredi) ; valider le budget de 500 euros (responsable : Jonathan ; échéance non précisée) ; faire un point de suivi (responsable et échéance précise non précisés, le texte indique « lundi prochain »).
- Questions ouvertes et risques/blocages : « Non précisé ».

### Analyse QA
Le compte rendu structure les informations en sections exploitables et associe correctement deux actions à des responsables. Cependant, il reprend « lundi prochain » alors que l'auditeur confirme avoir prononcé « mardi prochain ». Cette divergence peut modifier une échéance opérationnelle. Elle est liée à l'écart de transcription déjà enregistré et ne doit pas être comptée comme une anomalie indépendante sans investigation supplémentaire.

Le champ « Risques ou blocages : Non précisé » n'est pas en soi un défaut : le texte de référence ne mentionnait pas explicitement de risque ou blocage.

## TEST-005 — Extraction des actions et décisions
**Statut : vérification partielle.** Les actions et décisions sont visibles dans le compte rendu ; la divergence de date est propagée. Une validation métier exhaustive n'a pas été réalisée.

## TEST-006 — Téléchargement et vérification du document Word
**Statut : NOT RUN.** Le bouton « Télécharger le Word » est visible, mais le téléchargement et le contenu du fichier n'ont pas été vérifiés.

## TEST-007 — Importation d'un fichier audio
**Statut : PARTIELLEMENT PASS — fichier sélectionné et reconnu par l'interface ; génération interrompue/non vérifiée.**
- Nom affiché : `Test d'audio.m4a`.
- Durée affichée par le lecteur : 00:00:19.
- L'interface indiquait « Audio prêt » et le bouton « Générer les résumés » était actif.
- Après la tentative de lancement du traitement, une page blanche est apparue. Aucun résultat de génération n'a pu être observé.

## ANOMALIE À CONFIRMER — Page blanche / retour à un état antérieur après inactivité
**Statut : anomalie suspectée, reproduction à poursuivre.**
- **Comportements rapportés par l'auditeur :** après quelques minutes d'inactivité, la page peut devenir blanche ; actualiser ne rétablit pas toujours l'affichage. Le bouton Retour du navigateur peut ramener à la page précédente, correspondant à un état antérieur à l'inactivité. À certaines occasions, l'application demande une nouvelle connexion.
- **Preuve disponible :** capture d'écran d'une page blanche et récit des étapes de récupération.
- **Impact potentiel :** interruption du parcours utilisateur, nécessité de revenir en arrière ou de se reconnecter ; risque de perte de travail non confirmé.
- **Sévérité/priorité :** à déterminer après reproduction et vérification de la durée d'inactivité, de la session, de la page concernée et de la persistance des données.
- **Limite d'interprétation :** ces observations pourraient être liées à l'expiration de session, à la navigation ou à un problème d'affichage. La cause n'est pas établie et la perte de données n'a pas été constatée.

## TEST-008 — Historique et persistance
**Statut : NOT RUN.** La persistance après reconnexion doit être vérifiée séparément ; aucune perte de données n'est confirmée à ce stade.

## Authentification
Les pages de connexion et de création d'espace ont été observées pendant la reconnaissance initiale. Les tests fonctionnels de connexion valide et invalide restent à exécuter. L'ordre réel des exécutions sera indiqué fidèlement.
