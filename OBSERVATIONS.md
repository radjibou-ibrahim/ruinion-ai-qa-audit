# Résultats de l'audit — Ruinion AI

## Objectif
Vérifier des parcours représentatifs et relever uniquement les écarts appuyés par des observations réelles. Les captures sont conservées dans la conversation et ne sont pas publiées dans ce repository.

## TEST-001 — Enregistrement audio depuis le microphone
**Date :** 20 octobre 2026 · **Environnement :** navigateur mobile Android  
**Statut : PASS pour l'enregistrement et l'écoute**
- Un enregistrement de 22 secondes a été obtenu.
- L'auditeur confirme que la voix est audible et compréhensible.
- La lecture et le téléchargement de l'audio sont proposés.

## TEST-002 — Transcription de l'audio enregistré depuis le microphone
**Statut : FAIL — divergence factuelle confirmée par l'auditeur.**
- **Référence prononcée :** « Nous décidons de faire un point de suivi mardi prochain. »
- **Transcription affichée :** « Nous décidons de faire un point de suivi lundi prochain. »
- **Impact potentiel :** une échéance modifiée peut entraîner une confusion ou un suivi manqué.
- **Sévérité proposée :** Moyenne. **Priorité proposée :** P1, à confirmer avec le développeur selon la fréquence et les usages.
- **Preuve :** capture de la transcription et confirmation de l'auditeur. Le fichier audio n'est pas publié dans le repository.

## TEST-003 — Résumé court de l'enregistrement depuis le microphone
**Statut : examen partiel effectué.**
Le résumé reprend les informations principales : réunion commerciale prévue le lundi 26 octobre 2026, proposition tarifaire d'Ibrahim avant vendredi, budget de 500 euros validé par Jonathan, point de suivi prévu « lundi prochain » et responsable non précisé.

Le résumé reproduit la divergence de date observée dans la transcription. Il s'agit vraisemblablement de la propagation du même écart et non d'une anomalie indépendante. L'absence de responsable n'est pas qualifiée de bug sans règle métier confirmant qu'un responsable devait être déduit.

## TEST-004 — Compte rendu détaillé de l'enregistrement depuis le microphone
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

## TEST-005 — Extraction des actions et décisions à partir de l'enregistrement microphone
**Statut : vérification partielle.** Les actions et décisions sont visibles dans le compte rendu ; la divergence de date est propagée. Une validation métier exhaustive n'a pas été réalisée.

## TEST-006 — Téléchargement et vérification du document Word
**Statut : NOT RUN.** Le bouton « Télécharger le Word » est visible, mais le téléchargement et le contenu du fichier n'ont pas été vérifiés.

## TEST-007 — Importation d'un fichier audio local et génération des résultats
**Statut : PASS pour l'importation et la génération ; vérification fonctionnelle partielle.**
- Nom affiché : `Test d'audio.m4a`.
- Durée affichée par le lecteur : 00:00:19.
- L'interface a reconnu le fichier, affiché « Audio prêt » et activé le bouton « Générer les résumés ».
- Après le lancement du traitement, une page de réunion a été affichée avec le titre « Test d'importation audio — Réunion de suivi », le statut « Terminé » et une transcription.
- **Référence prononcée dans l'audio :** « Nous décidons de faire un point de suivi mardi prochain. »
- **Transcription affichée pour le fichier importé :** « Nous décidons de faire un point de suivi mardi prochain. »
- Pour cette occurrence, la phrase et le jour ont été retranscrits correctement. Cela contraste avec l'enregistrement microphone précédent, où « mardi » avait été transcrit « lundi ».
- Le résultat affiché ne permet pas, à lui seul, de conclure que toutes les fonctions de résumé et de compte rendu ont été validées pour ce fichier.

## ANOMALIE À CONFIRMER — Page blanche / retour à un état antérieur après inactivité
**Statut : anomalie intermittente rapportée ; cause non déterminée.**
- **Comportements rapportés par l'auditeur :** après quelques minutes d'inactivité, la page peut devenir blanche ; actualiser ne rétablit pas toujours l'affichage. Le bouton Retour du navigateur peut ramener à la page précédente, correspondant à un état antérieur à l'inactivité. À certaines occasions, l'application demande une nouvelle connexion.
- **Preuve disponible :** captures d'écran antérieures d'une page blanche et récit des étapes de récupération.
- **Impact potentiel :** interruption du parcours utilisateur, nécessité de revenir en arrière ou de se reconnecter ; risque de perte de travail non confirmé.
- **Sévérité/priorité :** à déterminer après reproduction et vérification de la durée d'inactivité, de la session, de la page concernée et de la persistance des données.
- **Limite d'interprétation :** les résultats récents confirment que le traitement du fichier importé a finalement abouti. Ils ne permettent pas de déterminer si la page blanche précédente était liée à l'inactivité, au traitement audio, à la session ou à une autre cause. Aucune perte de données n'est confirmée.

## TEST-008 — Historique et persistance des réunions
**Statut : PASS partiel pour la réunion issue de l'importation audio.**
- Après le traitement, la page de détail « Test d'importation audio — Réunion de suivi » est accessible et affiche la transcription.
- L'utilisateur confirme que la réunion apparaît dans l'historique.
- La persistance après une déconnexion puis une reconnexion n'a pas encore été vérifiée.

## Authentification
Les pages de connexion et de création d'espace ont été observées pendant la reconnaissance initiale. Les tests fonctionnels de connexion valide et invalide restent à exécuter. L'ordre réel des exécutions sera indiqué fidèlement.


## TEST-009 — Conservation du titre prérempli après déconnexion/reconnexion
**Statut : anomalie d'expérience utilisateur observée ; comportement attendu à confirmer.**
- **Observation :** après une déconnexion puis une reconnexion, le champ « Titre de la réunion » de l'écran « Nouvelle réunion » contient encore automatiquement « Réunion commerciale », titre utilisé lors du premier test.
- **Preuve :** capture d'écran du 20 octobre 2026 montrant le champ prérempli.
- **Impact potentiel :** l'utilisateur peut créer par inadvertance une nouvelle réunion avec un titre ancien, ou croire que le champ a été réinitialisé alors qu'il ne l'a pas été.
- **Limite :** on ne sait pas encore si ce comportement provient d'une valeur par défaut, d'un brouillon local, d'une préférence mémorisée ou d'une règle fonctionnelle. Il n'est pas établi que les données de réunion précédentes aient été restaurées ; seul le titre du champ est observé.
- **Vérification recommandée :** modifier le titre, quitter la page sans lancer de traitement, puis revenir à « Nouvelle réunion » ; comparer également après actualisation et après reconnexion. Noter si le titre revient toujours à « Réunion commerciale ».
