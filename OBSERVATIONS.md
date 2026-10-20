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
**Statut : PASS pour le téléchargement et l'ouverture ; examen du contenu partiel.**
- Le document Word a été téléchargé puis ouvert sur un appareil mobile.
- Le document contient un titre, une synthèse, les échanges et points clés, les décisions et un tableau de plan d'actions.
- **Observation d'affichage mobile :** le tableau de plan d'actions dépasse la largeur visible de l'écran et ses colonnes ne sont pas toutes visibles simultanément dans la capture. Il reste à vérifier sur ordinateur et à distinguer un problème de mise en page du document d'une limite d'affichage de l'application mobile.
- La vérification exhaustive du contenu et de la mise en page sur ordinateur n'a pas été effectuée.

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


## TEST-010 — Le titre saisi revient à une ancienne valeur après actualisation
**Statut : comportement reproductible observé ; règle attendue à confirmer.**
- **Action effectuée :** le titre du champ « Titre de la réunion » a été remplacé par `TEST TITRE TEMPORAIRE`, puis la page a été actualisée.
- **Résultat observé :** le champ est revenu à « Réunion commerciale ».
- **Interprétation prudente :** l'application ne conserve pas la nouvelle valeur saisie lors de cette actualisation et réaffiche l'ancien titre. Il reste à déterminer si cela provient d'une valeur par défaut, d'un brouillon conservé, d'un état mis en cache ou d'un comportement voulu.
- **Impact potentiel :** risque de créer une réunion avec un titre différent de celui que l'utilisateur vient de saisir, ou de devoir ressaisir les informations.
- **Sévérité/priorité :** à confirmer après vérification de la règle fonctionnelle et de la persistance attendue.

## TEST-011 — Page blanche lors de l'actualisation, y compris pendant une activité
**Statut : anomalie intermittente rapportée ; reproduction/diagnostic à poursuivre.**
- **Observation complémentaire :** l'auditeur indique que la page blanche peut apparaître même lorsqu'il est actif sur le site, et qu'une actualisation peut elle-même aboutir à une page blanche.
- **Impact potentiel :** l'utilisateur ne peut plus poursuivre le parcours normalement et peut devoir revenir en arrière ou se reconnecter.
- **Portée :** cette observation signifie que l'inactivité seule n'explique pas tous les cas rapportés. Il ne faut pas attribuer la cause à une expiration de session sans preuve.
- **Cause :** inconnue à ce stade ; aucune perte de données n'est confirmée.
- **Suite proposée :** relever la page exacte, l'heure, les actions juste avant l'erreur, et si le menu de navigation fonctionne encore ; vérifier si le problème survient après une actualisation depuis plusieurs pages différentes.


## TEST-012 — Copie de la transcription, du résumé et du compte rendu
**Statut : PASS selon confirmation de l'auditeur.**
- L'auditeur confirme que les boutons de copie de la transcription, du résumé et du compte rendu fonctionnent.
- Aucun défaut n'a été signalé sur ces boutons pendant le test.
- Les essais détaillés (texte exact copié, collage dans une autre application et comportement sur différents appareils) n'ont pas été documentés ; le résultat est limité au fonctionnement confirmé par l'auditeur.

## TEST-013 — Consultation de l'historique après importation audio
**Statut : PASS partiel.**
- L'historique affiche deux réunions terminées : « Test d'importation audio — Réunion de suivi » et « Réunion commerciale ».
- Les cartes présentent notamment le titre, la date, la durée de l'audio, un extrait de contenu et le nombre de participants.
- Cela confirme l'affichage des deux réunions dans l'historique à cet instant, mais pas la persistance après déconnexion/reconnexion ni l'exhaustivité de l'historique.

## TEST-014 — Consultation de la rubrique Équipe
**Statut : observation de l'interface ; actions fonctionnelles non testées.**
- La page « Équipe » affiche une organisation nommée « Micro Finance », un membre actif et le rôle « Propriétaire ».
- L'auditeur précise que « Micro Finance » est le nom d'organisation qu'il a renseigné lors de la création de son compte ; ce libellé est donc cohérent avec les données fournies lors de l'inscription.
- Un onglet « Invitations », une recherche de membres et un formulaire d'invitation sont visibles.
- Le formulaire demande une adresse e-mail et un rôle ; l'interface indique qu'un lien valable 7 jours sera créé et qu'aucun e-mail automatique ne sera envoyé.
- **Non testé :** création d'une invitation, utilisation ou expiration du lien, recherche effective, actualisation de la liste, modification/suppression d'un membre et contrôle des permissions.
- Aucune invitation n'a été envoyée et aucune modification n'a été réalisée pendant cette observation.


## TEST-016 — Consultation des paramètres du compte et de l'équipe
**Statut : affichage observé ; sauvegarde et effets des options non testés.**
- La page Paramètres présente une section « Votre accès » avec le nom du compte et le rôle « Propriétaire ».
- Dans « Règles d'invitation », la durée de validité du lien est réglée sur « 7 jours ».
- L'option « Autoriser les administrateurs à inviter » apparaît activée.
- Dans « Notifications », l'option « Activité des invitations » apparaît activée.
- Les rubriques « Documents juridiques » donnent accès à la politique de confidentialité et aux conditions d'utilisation.
- Le bouton « Enregistrer les modifications » est visible.
- **Non testé :** ouverture des documents juridiques, changement des options, enregistrement, persistance après actualisation et effet réel des notifications ou permissions.
- Aucune option n'a été modifiée et aucune sauvegarde n'a été effectuée durant cette observation.


## TEST-017 — Recherche d'une réunion dans l'historique
**Résultat : PASS pour le scénario observé.**
- Depuis l'historique des réunions, la saisie du terme « Test » filtre la liste.
- Une seule réunion est affichée : « Test d'importation audio — Réunion de suivi ».
- Le compteur indique « 1 réunion » et la carte correspondante est visible.
- Test effectué sur navigateur mobile.
- **Non testé :** recherche sans résultat, recherche par nom de participant ou mot-clé du contenu, casse/accents, effacement du champ et comportement avec un grand nombre de réunions.


## TEST-019 — Déconnexion pendant une activité
**Résultat : anomalie observée — à reproduire et caractériser.**
- L'utilisateur rapporte avoir été déconnecté alors qu'il était encore actif dans l'application.
- Ce comportement est à distinguer de la déconnexion observée après une période d'inactivité : dans ce cas, la déconnexion aurait eu lieu pendant l'utilisation.
- **À vérifier :** durée écoulée depuis la dernière action, fonctionnalité utilisée au moment de la déconnexion, présence d'un message d'expiration de session, conservation du travail en cours et possibilité de reprendre sans perte de données.
- **Statut :** observation rapportée par l'utilisateur ; reproduction contrôlée non encore effectuée.


## TEST-020 — Création d'une invitation et gestion du lien
**Résultat : PASS partiel — création confirmée ; copie et acceptation du lien non vérifiées.**
- Depuis **Paramètres > Équipe**, une invitation a été créée pour une adresse e-mail de test, avec le rôle **Membre**.
- Un message de confirmation vert indique : « Invitation créée. Copiez le lien ci-dessous pour le partager. »
- Le compteur affiche **1 invitation** pour l'organisation « Micro Finance ».
- Dans l'onglet **Invitations**, l'invitation apparaît avec le statut **En attente**.
- La date de création affichée est le **20 octobre 2026** et la date d'expiration le **27 octobre 2026**, ce qui correspond à la validité annoncée de 7 jours.
- Le panneau **Lien d'invitation** affiche un lien et un bouton **Copier le lien**. L'interface avertit que le lien doit être copié avant de quitter la page, car il ne pourra plus être affiché ensuite.
- Le menu d'actions permet d'ouvrir une boîte de dialogue **Révoquer l'invitation**, qui avertit que le lien deviendra inutilisable. La révocation n'a pas été confirmée.
- L'interface précise qu'aucun e-mail automatique n'est envoyé : le lien doit être partagé manuellement.
- **À tester ensuite :** bouton « Copier le lien » (confirmation visuelle et contenu réellement copié), ouverture du lien en session séparée, parcours d'acceptation, expiration et révocation effective.
- **Limite :** le lien n'a pas encore été ouvert avec le compte invité ; la création réussie ne confirme donc pas que le parcours d'acceptation fonctionne.
