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
**Statut : PARTIELLEMENT PASS — fichier sélectionné et reconnu par l'interface.**

- Nom affiché : `Test d'audio.m4a`.
- Durée affichée par le lecteur : 00:00:19.
- L'interface indique « Audio prêt ».
- Le bouton « Générer les résumés » est actif.

**Limite :** cette observation confirme la sélection et la préparation apparente du fichier, mais pas encore la génération des résultats. Le traitement doit être lancé puis ses résultats examinés.

## TEST-008 — Historique et persistance
**Statut : NOT RUN.**

## Authentification
Les pages de connexion et de création d'espace ont été observées pendant la reconnaissance initiale. Les tests fonctionnels de connexion valide et invalide restent à exécuter. L'ordre réel des exécutions sera indiqué fidèlement.
