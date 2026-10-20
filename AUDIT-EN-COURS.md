# Ruinion AI — Rapport d'audit QA fonctionnel

**Auditeur :** Radjibou IBRAHIM  
**Application :** https://ai.jonathanzadi.com  
**Date de démarrage :** 20 octobre 2026  
**Statut :** En cours — aucune conclusion finale à ce stade

## 1. Résumé

Cet audit vise à apporter au développeur un regard centré sur l'utilisateur et sur la valeur du produit : vérifier le parcours principal, relever les écarts observés, expliquer leurs conséquences et recommander des améliorations concrètes.

Le rapport est mis à jour au fil des tests et des éléments fournis. Une divergence de transcription a été confirmée ; d'autres comportements restent à reproduire ou à clarifier.

## 2. Périmètre prévu

- Création d'espace et connexion.
- Création et consultation d'une réunion.
- Enregistrement ou importation d'un audio.
- Transcription et génération du compte rendu.
- Extraction des décisions et actions.
- Téléchargement et vérification du document Word.
- Historique et persistance des résultats, si accessibles.

Le périmètre final dépendra des fonctions disponibles, des règles métier clarifiées et du temps accordé. Les tests approfondis de sécurité, de confidentialité et de performance sont hors périmètre à moins d'un accord et de vérifications dédiées.

## 3. Premières observations — interfaces d'accès

Les captures transmises montrent deux interfaces. Elles constituent des observations d'interface, pas des résultats de tests fonctionnels.

### Création d'espace

Éléments visibles :
- Prénom et nom.
- Organisation.
- Adresse e-mail.
- Mot de passe avec indication « Minimum 8 caractères ».
- Confirmation du mot de passe.
- Option « Rester connecté ».

Le texte de la page indique qu'un compte administrateur et une organisation sont créés ensemble. Ce comportement reste à vérifier lors d'un test d'inscription autorisé.

### Connexion

Éléments visibles :
- Adresse e-mail et mot de passe.
- Contrôle d'affichage du mot de passe.
- Option « Se souvenir de moi », cochée sur la capture.
- Bouton « Se connecter ».
- Lien « Créer un espace ».
- Lien vers la politique de confidentialité.

### État des vérifications

Aucun test fonctionnel n'est déclaré exécuté sur la base de ces seules captures. L'accès effectif au compte et le comportement après connexion restent à confirmer.

## 4. Résultats des tests

À compléter après chaque exécution.

| ID | Parcours | Résultat | Preuve | Commentaire |
|---|---|---|---|---|
| TEST-001 | Enregistrement audio depuis le microphone | PASS partiel | Écoute confirmée | Enregistrement de 22 s audible ; lecture et téléchargement proposés. |
| TEST-002 | Transcription de l'audio microphone | FAIL | Audio de référence et transcription affichée | « mardi prochain » retranscrit « lundi prochain » ; divergence factuelle confirmée. |
| TEST-003 | Résumé court | Examen partiel | Résumé affiché | Informations principales reprises, mais divergence de date propagée. |
| TEST-004 | Compte rendu détaillé | Examiné — fidélité partielle | Compte rendu affiché | Sections structurées ; divergence de date propagée depuis la transcription. |
| TEST-005 | Extraction des actions et décisions | Examen partiel | Compte rendu affiché | Actions et décisions visibles ; validation métier exhaustive non réalisée. |
| TEST-006 | Téléchargement et ouverture du document Word | PASS partiel | Document ouvert sur mobile | Téléchargement et ouverture réussis ; contrôle complet du contenu et de la mise en page restant à faire. |
| TEST-007 | Importation d'un fichier audio local | PASS partiel | Écran « Audio prêt », puis réunion terminée | Fichier M4A de 19 s importé et traité ; transcription de « mardi prochain » correcte dans cet essai. |
| TEST-008 | Historique et persistance des réunions | PASS partiel | Historique visible | Deux réunions affichées ; persistance après déconnexion/reconnexion non testée. |
| TEST-009/010 | Titre prérempli après reconnexion/actualisation | Observation à clarifier | Capture et manipulation rapportées | « Réunion commerciale » revient dans le champ après actualisation ; règle attendue non confirmée. |
| TEST-011 | Page blanche après inactivité ou actualisation | INCONCLUSIVE — anomalie rapportée | Captures et récit de l'auditeur | Peut survenir après inactivité ou actualisation même en activité ; cause et perte éventuelle de données non déterminées. |
| TEST-012 | Copie de la transcription, du résumé et du compte rendu | PASS selon l'auditeur | Confirmation de l'auditeur | Les trois boutons de copie fonctionnent. |
| TEST-013 | Consultation de l'historique | PASS partiel | Capture de l'historique | Deux réunions terminées visibles ; conservation à long terme non testée. |
| TEST-014 | Rubrique Équipe | Observation de l'interface | Captures de la page Équipe | Membre, rôle et formulaire d'invitation visibles ; actions d'invitation et permissions non testées. |

Statuts utilisés :
- **PASS** : résultat attendu observé.
- **FAIL** : écart constaté entre le résultat attendu et le résultat observé.
- **BLOCKED** : un blocage empêche l'exécution.
- **NOT RUN** : test non exécuté.
- **INCONCLUSIVE** : les éléments ne permettent pas de conclure.

## 5. Problèmes et points d'attention

### 5.1 Divergence de transcription — confirmée
Dans l'audio enregistré depuis le microphone, la phrase prononcée « Nous décidons de faire un point de suivi mardi prochain » apparaît comme « lundi prochain » dans la transcription. La même divergence est reprise dans le résumé et le compte rendu détaillé. Elle est comptée comme une anomalie principale, et non comme trois bugs indépendants. Sévérité proposée : moyenne ; priorité à discuter avec le développeur.

### 5.2 Page blanche — anomalie intermittente rapportée, cause inconnue
L'auditeur rapporte une page blanche après une période d'inactivité, mais également après actualisation et parfois alors qu'il utilise encore le site. Le bouton Retour peut restaurer une page précédente et une reconnexion est parfois demandée. La cause n'est pas déterminée et aucune perte de données n'est confirmée. Ce point reste à reproduire.

### 5.3 Titre de réunion réaffiché après actualisation — comportement à clarifier
Le champ « Titre de la réunion » revient à « Réunion commerciale » après actualisation, même après la saisie d'une valeur temporaire. Le comportement attendu n'est pas encore établi ; il est enregistré comme point d'attention et non comme défaut métier définitivement confirmé.

### 5.4 Affichage du tableau Word sur mobile — à vérifier
Dans la capture du document téléchargé, le tableau du plan d'actions dépasse la largeur visible de l'écran. Une vérification sur ordinateur est nécessaire avant de conclure à un défaut de mise en page du document généré.

Pour chaque problème confirmé, le rapport précisera :
- ce que l'utilisateur essaie de faire ;
- les étapes permettant de reproduire le problème ;
- le résultat attendu et le résultat observé ;
- l'impact concret pour l'utilisateur ou le produit ;
- la priorité recommandée et sa justification ;
- les preuves disponibles.

## 6. Risques et recommandations

Les tests de la rubrique Équipe restent limités à l'observation de l'interface : aucune invitation n'a été créée et aucun rôle ni droit d'accès n'a été modifié. Les boutons de copie de la transcription, du résumé et du compte rendu ont été confirmés fonctionnels par l'auditeur. La rubrique Équipe, l'utilisation et l'expiration des invitations, la persistance après reconnexion et l'affichage du document Word sur ordinateur restent à tester. Les risques non vérifiés sont présentés comme des points à examiner, et non comme des défauts avérés.

## 7. Limites

- L'audit est ciblé et ne constitue pas une certification complète de l'application.
- Les fonctions non accessibles ou non testées seront identifiées comme telles.
- La qualité du contenu généré sera évaluée par comparaison avec un audio de référence connu, si un jeu de données adapté est disponible.
- Les tests de sécurité, de confidentialité et de performance ne seront pas réputés couverts sans tests dédiés et autorisés.

## 8. Conclusion et prochaines étapes

La conclusion sera rédigée après l'exécution des tests retenus. Elle synthétisera les points importants, leur impact, les améliorations recommandées et les éventuelles pistes de collaboration QA.

---
*Document de travail : les résultats et conclusions seront ajoutés au fur et à mesure, sans inventer d'exécution ni de preuve.*
