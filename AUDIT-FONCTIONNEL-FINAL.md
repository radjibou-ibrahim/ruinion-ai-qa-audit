# Ruinion AI — Rapport final d'audit QA fonctionnel

**Auditeur :** Radjibou IBRAHIM  
**Application auditée :** https://ai.jonathanzadi.com  
**Date des tests documentés :** 20 octobre 2026  
**Environnement principal :** navigateur mobile Android  
**Version :** 1.0 — rapport consolidé des tests réellement exécutés

## 1. Résumé exécutif

Cet audit fonctionnel ciblé a examiné des parcours représentatifs de Ruinion AI : enregistrement et importation audio, transcription et génération de comptes rendus, téléchargement Word, historique, recherche, gestion d'équipe, invitations et authentification.

Le principal écart fonctionnel confirmé concerne la transcription d'un audio enregistré depuis le microphone : la phrase « mardi prochain » a été transcrite « lundi prochain ». Cette divergence est ensuite propagée au résumé et au compte rendu détaillé. Elle est comptée comme une anomalie principale, et non comme trois bugs indépendants.

D'autres points nécessitent une investigation : apparition intermittente d'une page blanche lors d'une actualisation ou pendant l'utilisation, et réinitialisation du titre de réunion à une ancienne valeur après actualisation. Ces comportements ont été rapportés ou observés, mais leur cause et leur règle fonctionnelle attendue ne sont pas déterminées.

Les principaux parcours de création et d'acceptation d'une invitation ont fonctionné dans les essais réalisés. La révocation de l'invitation n'a pas été testée. Les tests d'authentification réalisés en fin de session ont donné les résultats attendus pour la connexion valide, le mot de passe incorrect, les champs vides, la déconnexion et le bouton Retour.

**Conclusion générale :** plusieurs parcours représentatifs fonctionnent, mais la fiabilité de la transcription microphone et les comportements intermittents d'affichage/session méritent une investigation prioritaire. Ce rapport est un audit fonctionnel ciblé, et non une certification exhaustive de la qualité, de la sécurité ou des performances du produit.

## 2. Périmètre et méthode

Les tests ont été conduits dans l'ordre réel de la session :
1. Enregistrement audio depuis le microphone, puis examen de la transcription, du résumé et du compte rendu.
2. Téléchargement et ouverture du document Word.
3. Importation d'un fichier audio local et consultation des résultats.
4. Historique, recherche de réunion, titre de réunion et comportements d'actualisation.
5. Consultation des paramètres et de la rubrique Équipe.
6. Création d'une invitation, copie du lien, ouverture du lien, acceptation depuis le compte invité et observation des permissions du rôle Membre.
7. Authentification : déconnexion, connexion valide, tentative avec mot de passe incorrect, soumission avec champs vides et navigation arrière.

Les résultats reposent sur les actions rapportées par l'auditeur, les captures transmises et les résultats visibles. Un comportement non testé n'est pas considéré comme conforme. Les causes techniques ne sont pas déduites sans preuve.

### Légende des statuts
- **PASS** : résultat attendu observé pour le scénario testé.
- **FAIL** : écart constaté par rapport au résultat attendu.
- **PASS partiel / examen partiel** : une partie du parcours a fonctionné, mais la validation n'est pas exhaustive.
- **À confirmer / inconclusif** : observation réelle, mais règle attendue, cause ou reproduction insuffisamment établies.
- **NOT TESTED** : aucun résultat ne peut être conclu.

## 3. Synthèse des résultats

| ID | Parcours | Résultat | Synthèse |
|---|---|---|---|
| TEST-001 | Enregistrement audio depuis le microphone | PASS partiel | Enregistrement de 22 secondes audible ; lecture et téléchargement proposés. |
| TEST-002 | Transcription de l'audio microphone | FAIL | « mardi prochain » apparaît comme « lundi prochain ». |
| TEST-003 | Résumé court | Examen partiel | Informations principales reprises ; la divergence de date est propagée. |
| TEST-004 | Compte rendu détaillé | Examen partiel | Sections structurées et actions visibles ; divergence de date propagée. |
| TEST-005 | Extraction des actions et décisions | Examen partiel | Actions et décisions visibles ; validation métier exhaustive non réalisée. |
| TEST-006 | Téléchargement et ouverture du document Word | PASS partiel | Téléchargement et ouverture sur mobile réussis ; mise en page complète non vérifiée sur ordinateur. |
| TEST-007 | Importation d'un fichier audio local | PASS partiel | Fichier M4A de 19 secondes importé et traité ; la phrase « mardi prochain » est correctement transcrite dans cet essai. |
| TEST-008 | Historique et persistance | PASS partiel | Réunion issue de l'importation visible dans l'historique ; persistance après reconnexion non entièrement vérifiée. |
| TEST-009/010 | Titre prérempli après reconnexion/actualisation | À confirmer | L'ancien titre « Réunion commerciale » réapparaît après actualisation ; règle attendue inconnue. |
| TEST-011 | Page blanche après actualisation ou pendant l'activité | À investiguer | Page blanche rapportée dans plusieurs circonstances ; cause et perte éventuelle de données non déterminées. |
| TEST-012 | Copie de la transcription, du résumé et du compte rendu | PASS selon l'auditeur | Les trois boutons de copie ont été confirmés fonctionnels. |
| TEST-013 | Consultation de l'historique | PASS partiel | Deux réunions terminées visibles ; conservation à long terme non testée. |
| TEST-014 | Rubrique Équipe | Observation partielle | Membres, rôles et formulaire d'invitation visibles ; actions non encore vérifiées à cette étape. |
| TEST-016 | Paramètres du compte et de l'équipe | Observation partielle | Options et durée de validité affichées ; sauvegarde et effets non testés. |
| TEST-017 | Recherche dans l'historique | PASS pour le scénario testé | Le terme « Test » filtre la liste et affiche une réunion correspondante. |
| TEST-019 | Déconnexion pendant une activité | À reproduire | Déconnexion rapportée pendant l'utilisation ; conditions et impact sur le travail non établis. |
| TEST-020 | Création et copie du lien d'invitation | PASS partiel | Invitation créée, affichée en attente, expiration annoncée à 7 jours ; copie confirmée par l'auditeur. |
| TEST-021 | Acceptation de l'invitation et accès du rôle Membre | PASS pour les points observés | Le compte invité a rejoint l'organisation ; l'accès à la gestion d'équipe est refusé au rôle Membre. |
| TEST-022 | Révocation d'une invitation | NOT TESTED | La révocation et l'invalidation effective du lien n'ont pas été testées. |
| TEST-023A | Déconnexion volontaire | PASS | Redirection vers la page de connexion observée. |
| TEST-023B | Connexion avec identifiants valides | PASS | La connexion fonctionne et l'accès est rétabli. |
| TEST-023C | Mot de passe incorrect | PASS | Connexion refusée avec le message « Invalid email or password ». |
| TEST-023D | Champs de connexion vides | PASS | Soumission bloquée avec un message indiquant les champs à renseigner. |
| TEST-023E | Bouton Retour après déconnexion | PASS — observation limitée | Aucune page privée ne réapparaît ; retour à la page d'accueil. Le contrôle des URL privées directes reste à faire. |

Les identifiants de test suivent le journal de travail ; les numéros absents ne sont pas interprétés comme des tests exécutés.

## 4. Anomalies et points d'attention

### 4.1 Divergence de date dans la transcription microphone

**Statut : FAIL confirmé**  
**Sévérité proposée : moyenne**  
**Priorité proposée : élevée à discuter avec le développeur, selon l'usage métier et la fréquence.**

- **Référence prononcée :** « Nous décidons de faire un point de suivi mardi prochain. »
- **Transcription affichée :** « Nous décidons de faire un point de suivi lundi prochain. »
- **Propagation :** la même date incorrecte est reprise dans le résumé court et le compte rendu détaillé.
- **Impact potentiel :** mauvaise date de suivi, confusion entre participants ou échéance manquée.

**Recommandations :**
1. Reproduire avec le même fichier audio et comparer le résultat de l'enregistrement microphone à celui de l'importation.
2. Ajouter des tests de référence portant sur les jours, dates, heures, montants, noms propres et responsables.
3. Vérifier si le problème dépend du chemin d'acquisition audio ou du traitement de transcription.
4. Éviter que les résumés et comptes rendus amplifient une donnée incertaine sans mécanisme de contrôle.

L'importation audio a correctement retranscrit « mardi prochain » lors d'un essai distinct. Ce contraste est utile pour l'investigation, mais ne prouve pas à lui seul la cause.

### 4.2 Page blanche lors d'une actualisation ou pendant l'utilisation

**Statut : anomalie rapportée ; cause inconnue.**

L'auditeur a signalé une page blanche après une période d'inactivité, mais aussi pendant une activité et après actualisation. Une actualisation peut elle-même aboutir à une page blanche ; un retour arrière ou une nouvelle connexion a parfois été nécessaire.

**Impact potentiel :** interruption du travail, difficulté à reprendre le parcours et éventuelle perte de travail non confirmée.

**Recommandations :**
1. Reproduire sur plusieurs pages et noter l'heure, la dernière action, l'URL et le délai depuis la dernière interaction.
2. Examiner les erreurs JavaScript, les réponses réseau et la gestion de session au moment de l'incident.
3. Vérifier que le contenu déjà saisi ou généré est conservé après récupération.
4. Ne pas attribuer le problème uniquement à l'inactivité : des cas ont aussi été rapportés pendant l'utilisation.

Aucune perte de données n'est confirmée dans les éléments collectés.

### 4.3 Ancien titre réaffiché après actualisation

**Statut : comportement observé ; règle attendue à confirmer.**

Après avoir saisi le titre temporaire TEST TITRE TEMPORAIRE puis actualisé la page, le champ « Titre de la réunion » est revenu à « Réunion commerciale ». Le titre est également réapparu après déconnexion/reconnexion.

**Impact potentiel :** l'utilisateur peut lancer une réunion sous un titre différent de celui qu'il vient de saisir ou devoir ressaisir ses données.

**Recommandations :**
- Clarifier si le champ doit être réinitialisé, restauré depuis un brouillon ou prérempli par défaut.
- Tester en quittant la page sans lancer de génération, puis en revenant, en actualisant et après reconnexion.
- Vérifier que le comportement est cohérent avec la règle métier et que les données d'une réunion ne sont pas confondues.

Ce point n'est pas déclaré bug confirmé tant que le comportement attendu n'est pas clarifié.

### 4.4 Déconnexion rapportée pendant une activité

**Statut : observation à reproduire.**

Une déconnexion alors que l'utilisateur était actif a été rapportée. La durée exacte, l'action en cours et l'impact sur le travail ne sont pas établis.

**Recommandations :** reproduire sous contrôle, consigner le délai, le message affiché, la fonctionnalité en cours et la récupération du travail. Vérifier si cela est lié à l'expiration de session ou à un autre problème avant de conclure.

### 4.5 Affichage du tableau Word sur mobile

**Statut : observation d'affichage, cause non confirmée.**

Le tableau du plan d'actions dépasse la largeur visible de l'écran mobile. Il reste à ouvrir le document sur ordinateur et à vérifier la mise en page réelle du fichier avant de qualifier cela de défaut du document généré.

## 5. Invitations et rôles

- La création d'une invitation pour un compte de test a abouti ; l'invitation apparaît « En attente » avec une validité annoncée de 7 jours.
- L'interface précise qu'aucun e-mail automatique n'est envoyé et que le lien doit être partagé manuellement.
- La copie du lien a été confirmée par l'auditeur.
- Le premier essai d'acceptation avec un compte différent de l'adresse invitée a affiché un message indiquant que l'invitation concernait une autre adresse e-mail.
- Après connexion avec le compte destinataire, l'acceptation a abouti et le compte est apparu dans l'organisation avec le rôle « Membre ».
- Depuis ce compte, la page de gestion de l'équipe a affiché « Accès réservé », ce qui correspond à la restriction annoncée pour ce rôle.

**Non testés :** révocation et invalidation du lien, expiration réelle, réutilisation du lien après acceptation, permissions détaillées sur les réunions et les comptes rendus, recherche avancée et modification/suppression de membres.

## 6. Authentification

Les tests d'authentification ont été exécutés vers la fin de la session, après les tests audio, l'importation, l'historique et les invitations.

- La déconnexion volontaire redirige vers la page de connexion.
- La connexion avec des identifiants valides fonctionne.
- Un mot de passe incorrect est refusé avec « Invalid email or password ».
- Une soumission avec les deux champs vides est bloquée avec un message explicite.
- Le bouton Retour après déconnexion n'a pas fait réapparaître une page privée lors de l'essai ; le navigateur est revenu à la page d'accueil.

**Limite importante :** l'accès direct à une URL privée après déconnexion, les tentatives avec une adresse inconnue et la protection des données côté serveur n'ont pas été testés. Les observations de cette session ne constituent pas un audit de sécurité.

## 7. Recommandations priorisées

1. **Priorité 1 — Investiguer la divergence de transcription microphone**, en particulier les dates et échéances, car une erreur de ce type peut modifier une décision opérationnelle.
2. **Priorité 2 — Reproduire et diagnostiquer la page blanche et la déconnexion pendant l'activité**, en vérifiant la conservation du travail.
3. **Priorité 3 — Clarifier et stabiliser le comportement du titre de réunion après actualisation et reconnexion.**
4. **Priorité 4 — Compléter la validation du document Word sur ordinateur et mobile.**
5. **Priorité 5 — Compléter les tests d'invitation non exécutés**, notamment révocation, expiration et réutilisation du lien.
6. **Priorité 6 — Compléter la couverture des accès**, notamment l'accès direct à une URL privée après déconnexion et les permissions détaillées des membres.

Ces priorités sont des recommandations QA initiales ; elles devront être ajustées avec le développeur selon l'impact métier, la fréquence de reproduction et le coût de correction.

## 8. Limites de l'audit

- Audit ciblé effectué principalement sur navigateur mobile Android.
- Plusieurs résultats sont partiels et certaines observations nécessitent une reproduction contrôlée.
- La mise en page Word sur ordinateur, la révocation d'invitation, l'expiration réelle du lien, l'accès direct aux routes privées et certaines permissions n'ont pas été testés.
- Aucun test approfondi de sécurité, de confidentialité, de charge ou de performance n'est revendiqué.
- Les causes techniques des anomalies ne sont pas établies.
- Les preuves disponibles sont les captures et observations de l'auditeur ; aucun journal serveur ni rapport de diagnostic technique n'a été fourni.

## 9. Conclusion

Les tests réalisés montrent que plusieurs parcours importants sont utilisables : l'enregistrement et l'importation audio, la génération des résultats, la consultation de l'historique, la création et l'acceptation d'une invitation, ainsi que les principaux scénarios de connexion.

L'écart le plus concret est la substitution de « mardi » par « lundi » dans la transcription issue du microphone, ensuite propagée aux résultats dérivés. La page blanche et le comportement du titre de réunion nécessitent également une investigation, sans conclure prématurément à leur cause.

L'audit ne permet pas d'affirmer que toutes les fonctionnalités sont exemptes de défauts. Il fournit une base de reproduction et des recommandations concrètes pour la suite. Les tests non exécutés restent explicitement hors des conclusions.

---
**Fin du rapport — version 1.0.**  
Le journal détaillé des observations et les limites test par test sont conservés dans OBSERVATIONS.md.
