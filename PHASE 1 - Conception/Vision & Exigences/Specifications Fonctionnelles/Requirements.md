## exigences TMS



## 1 Présentation et statut du document

### 1.1 


### 1.2 Autorité et validation

Les instructions explicites du responsable de projet prévalent sur les recommandations de l’audit. Les contraintes fixées par cette mission et les exclusions explicites du Scope encadrent le livrable. Une information présente dans une source n’est pas automatiquement une décision approuvée.

| Marque ou statut | Sens et effet |
|---|---|
| CAD | Cadrage explicite confirmé pour cette consolidation |
| REC | Rédaction ou règle recommandée ; à approuver avant engagement de réalisation |
| HYP | Hypothèse ou arbitrage ouvert ; aucune réponse inventée |
| Révision modifiée | Référence conservée avec formulation corrigée ou précisée |
| Révision divisée | Sous responsabilités identifiées sans augmenter le nombre de références principales |
| Validation À valider | Aucun accord détaillé supplémentaire fourni ; critères proposés, non exécutés |
| Validation du cadrage | Ne vaut pas approbation des cardinalités, seuils, permissions ou procédures détaillées |

Les fiches distinguent systématiquement statut de révision et statut de validation. Toutes les priorités et tous les critères d’acceptation sont proposés. Un critère dépendant d’une question ouverte devient exécutable selon la règle retenue après décision consignée ; il ne peut pas être déclaré satisfait sur une hypothèse non approuvée. « Non applicable » exige une justification liée au déploiement ou à une option explicitement non retenue, jamais une simple absence de développement.

### 1.3 Utilisation et identifiants

Les identifiants EF01 à EF24 et ENF01 à ENF14 sont conservés. EF04a et EF04b sont des sous références d’EF04 ; ENF05a et ENF05b sont des sous références d’ENF05. Les critères gardent la forme CA-EF01-1 ou CA-ENF01-1. Les refus particuliers sont repérés RF suivi de la référence principale. Les dépendances expriment des liens de cohérence, de données ou de garantie ; elles ne constituent pas toutes un ordre de développement strict. Les cycles entre références doivent être conçus ensemble.

Les sections 4 et 5 organisent les exigences par domaine et catégorie. La section 6 relie sources, objectifs, modifications et tests ; la section 7 rassemble les priorités ; la section 8 conserve les décisions ouvertes et contradictions non résolues. Les tests d’une application ne sont pas exécutés dans ce document de spécification.

## 2 Périmètre V1 et exclusions

### 2.1 Cadrage confirmé

- CAD01 : application Java Desktop V1. JavaFX, SGBD, organisation en couches, topologie de stockage et mécanismes de partage ne sont pas des choix techniques définitifs.
- CAD02 : deux parcours conservés : A vente avec livraison et B transport seul. Le parcours B ne nécessite aucune commande de vente.
- CAD03 : transport central, gestion commerciale simple complémentaire. Les lignes de vente, leurs champs et leurs règles restent à préciser ; aucun ERP n’est introduit.
- CAD04 : chauffeur comme ressource à planifier, sans compte chauffeur ; client sans compte V1. Un employé habilité saisit les informations reçues du terrain.
- CAD05 : aucune transformation du projet en architecture Web ou SaaS. La séparation des données entre entreprises reste une garantie à concevoir et à vérifier selon le déploiement retenu.

### 2.2 Capacités consolidées proposées

| Domaine V1 | Contenu et limites |
|---|---|
| Accès et référentiels | Comptes individuels, droits cumulables, clients, véhicules et chauffeurs |
| Entrée A | Vente minimale, lignes simples, demande et mission de livraison liées, sans ressaisie obligatoire |
| Entrée B | Demande de transport de biens du client, directement reliée au traitement de mission |
| Transport commun | Planning manuel, disponibilité connue, affectation, conflits et indisponibilités, y compris missions extérieures saisies |
| Exécution | États et événements manuels, retards, incidents, historique et corrections tracées |
| Déchargement | Conditions convenues et heures connues, attente et immobilisation ; aucun service payant ajouté |
| Finance | Montants convenus, règlements partiels et confirmations, soldes et dépenses opérationnelles |
| Consultation | Listes, filtres, synthèse simple ; génération de rapports et export soumis à arbitrage EF24 |
| Qualités | Permissions effectives, confidentialité, persistance, erreurs, intégrité, audit, sauvegarde et restauration, concurrence selon partage |

Les détails de cette V1 restent des REC à approuver, même si leurs domaines sont imposés par la mission. Les priorités proposées ne suppriment aucun domaine annoncé. Le minimum nécessaire aux deux parcours doit être conservé ; un report effectif exige une décision explicite de périmètre.

### 2.3 Exclusions et éléments non engagés

Hors V1 : GPS et suivi automatique en temps réel ; prévision météo ou calcul automatique d’arrivée ; optimisation avancée ou IA ; application mobile, compte chauffeur et portail client ; SMS, WhatsApp, email ou autre notification externe automatique ; paiement en ligne, connexion bancaire et comptabilité complète ; gestion complète des achats, fournisseurs, stocks et paie.

Le service payant de déchargement, les pénalités automatiques d’attente, l’abonnement, le provisionnement d’une plateforme SaaS et l’analyse centrale des données clients ne sont pas engagés. Une indisponibilité pour entretien ne constitue pas un module de maintenance. Une référence de justificatif ne constitue pas une gestion de pièces jointes. Fractionnement, groupage, plusieurs véhicules par mission, délégation automatisée, duplication avancée, taux d’utilisation avancés et exports multiples ne sont pas ajoutés ; leur report proposé et les limites associées restent traçables dans les fiches et décisions.

Le logiciel présente des informations déclarées et leur ancienneté. Il ne garantit pas une heure d’arrivée, une position physique, la sécurisation des espèces, une rentabilité comptable ni une disponibilité réelle non renseignée.

## 3 Glossaire acteurs et règles communes

### 3.1 Glossaire métier proposé

| Terme | Définition proposée — REC |
|---|---|
| Employé | Personne de l’entreprise ; ne possède pas nécessairement de compte |
| Utilisateur / compte | Identité authentifiée qui exécute des actions dans un périmètre autorisé |
| Rôle | Ensemble nommé de permissions ; plusieurs rôles peuvent être attribués à un compte |
| Permission | Autorisation d’une action sur une catégorie de données et un périmètre |
| Chauffeur | Ressource de transport ; aucun compte n’en découle automatiquement |
| Demande | Besoin reçu, avec souhaits ; ne constitue pas une réservation ni une promesse de date |
| Commande de vente | Accord commercial minimal sur des produits, quantités et montants |
| Mission | Unité opérationnelle de transport partagée par les deux parcours |
| Affectation | Engagement daté de ressources pour une mission |
| Annulation | Arrêt motivé d’un dossier, sans effacer les faits, frais et mouvements déjà enregistrés |
| Correction | Nouvel acte traçable qui rectifie une donnée et conserve sa valeur antérieure |
| Obligation financière | Montant dû identifié une seule fois, relié au dossier et à ses composantes |
| Paiement annoncé | Intention ou information reçue, sans confirmation d’encaissement |
| Paiement enregistré | Mouvement saisi ; son statut détermine s’il compte dans le solde |
| Encaissement confirmé | Réception de fonds confirmée par une personne habilitée ; ne signifie pas rapprochement bancaire automatique |
| Sauvegarde de secours | Copie de récupération, distincte de l’enregistrement d’un formulaire |

### 3.2 Acteurs et responsabilités proposées

| Acteur | Responsabilité proposée | Validation requise |
|---|---|---|
| Administrateur de l’entreprise | Comptes, rôles, désactivation et remplacement | Matrice, premier et dernier administrateur, récupération Q04 et Q18 |
| Coordinateur transport | Préparation, confirmation, affectation, suivi et replanification | Droits de confirmer, annuler et corriger Q04 |
| Personnel commercial | Clients, demandes, vente minimale, consultation utile | Visibilité des montants et limites commerciales Q02 et Q04 |
| Personnel financier habilité | Montants, règlements, confirmation d’encaissement, dépenses, corrections | Preuves, autorité de confirmation et régularisations Q04 et Q13 à Q15 |
| Responsable ou lecteur autorisé | Consultation des dossiers, synthèse et rapports selon droits | Étendue des lectures et audit Q04 et Q20 |
| Responsable de sauvegarde | Copies, contrôle et restauration selon procédure | Personne désignée et politique Q19 |
| Chauffeur | Ressource et source d’informations transmises à l’employé | Aucun compte ni acteur logiciel authentifié en V1 |
| Client | Partie métier de la demande et du règlement | Aucun compte logiciel en V1 |

Une personne peut cumuler plusieurs fonctions selon les permissions approuvées. La propriété d’un dossier ne doit pas être assimilée à son créateur. Le responsable métier de chaque domaine sera nommé par l’équipe à la validation ; aucun nom ni accord individuel n’est présumé.

### 3.3 Règles communes proposées

Les règles RC sont des recommandations transversales à approuver ; le cadrage CAD reste applicable. Elles complètent chaque fiche et ses critères, sans remplacer la validation des règles sources BR-01 à BR-10 [V §7] et R1 à R12 [S §6].

**RC-1 — Autorisation et entreprise.** Toute lecture, écriture, recherche, synthèse et restitution applique EF02, ENF02 et ENF03. Cette précondition s’applique à toutes les fiches sans être répétée. Un contrôle d’interface seul est insuffisant.

**RC-2 — Écriture et historique.** Une opération métier produit un résultat cohérent ou échoue explicitement ; aucun faux succès ni effet partiel contradictoire. ENF05/06/07/08/13 s’appliquent. Une correction conserve l’état antérieur, l’auteur, la date de saisie et un motif pour les corrections critiques.

**RC-3 — Dates et inconnus.** Les heures sont des dates-heures complètes dans le référentiel horaire retenu pour l’exploitation, à documenter. Une valeur inconnue reste absente et signalée ; elle n’est pas remplacée par zéro ou l’heure de saisie. Les saisies rétroactives sont possibles si cohérentes et tracées. L’heure système de saisie n’est pas modifiable par l’utilisateur dans l’application.

**RC-4 — Tests.** Les critères CA de chaque fiche s’ajoutent aux contrôles RC-1 à RC-3. Un accès indu, un résultat financier faux, un écrasement silencieux ou un effet partiel contradictoire constitue toujours un refus. Les critères de refus RF ne répètent donc que les risques particuliers. Les jeux d’essai sont synthétiques et anonymes.

**RC-5 — Données minimales par étape.** Le brouillon accepte des champs métier incomplets ; la validation/confirmation vérifie seulement les champs nécessaires à l’action. Une valeur absente n’est pas une valeur validée. Les identifiants internes doivent rester stables même après modification du libellé d’un client ou désactivation d’un utilisateur.

### 3.4 Liens métier et conditions de recette

Parcours A proposé : client et vente simple → demande de livraison liée → mission commune → affectation → événements et déchargement → suivi financier. Parcours B proposé : client et demande de transport sans vente → même traitement de mission et de suivi. Une mission ne doit pas créer une seconde dette déjà portée par la vente liée.

La limite d’une mission active par demande et d’un couple véhicule chauffeur par mission est une simplification recommandée, toujours À valider en Q03. Le diagramme de classes doit afficher cette cardinalité comme provisoire tant que la décision n’est pas prise. Les classes techniques, tables et mécanismes ne sont pas imposés par les termes métier.

Les critères couvrent les deux parcours, les inconnus, les corrections et les échecs. Les contrôles RC-1 à RC-3 s’appliquent à chaque critère métier. Les essais utilisent des données synthétiques. Une donnée manquante n’est jamais remplacée par une valeur inventée. Les seuils de temps, limites d’inactivité, règles financières et transitions non approuvés empêchent de prononcer une recette complète sur leur domaine.

## 4 Exigences fonctionnelles par domaine

### 4.1 Domaine A Utilisateurs et accès

#### EF01 — Connexion, déconnexion et expiration d’accès

- **Groupe :** A. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q18.

- **Description détaillée :** permettre à une personne disposant d’un compte actif d’ouvrir une session de travail dans l’application Java Desktop, puis de la fermer. Aucune route Web ni méthode de gestion de jeton n’est imposée.
- **Acteur :** utilisateur disposant d’un compte.
- **Conditions préalables :** compte créé ; service de données nécessaire accessible ; politique d’inactivité définie.
- **Comportement attendu :** contrôler les informations de connexion, ouvrir les fonctions autorisées, refuser sans distinguer publiquement identifiant inconnu et mot de passe faux. Après déconnexion ou expiration, toute nouvelle action protégée exige une authentification.
- **Règles métier :** compte désactivé refusé ; expiration après une durée T à valider. Les 30 minutes de [R] restent une valeur candidate, pas une règle confirmée. La saisie non enregistrée doit être signalée selon la politique de verrouillage retenue, sans maintenir des droits expirés.
- **Erreurs/exceptions :** source d’authentification inaccessible : expliquer l’indisponibilité sans accorder l’accès ; reprise d’une saisie sans enregistrement automatique implicite.
- **CA-EF01-1 :** un compte actif avec données valides accède aux seules opérations de ses permissions.
- **CA-EF01-2 :** mot de passe incorrect, compte absent et compte désactivé n’ouvrent aucune fonction métier ; le message ne révèle pas l’existence du compte.
- **CA-EF01-3 :** avec T défini dans le protocole de test, après T d’inactivité puis après déconnexion explicite, une nouvelle action protégée est refusée jusqu’à reconnexion.
- **RF-EF01 :** une saisie en cours est enregistrée silencieusement sous une session expirée ; une erreur technique est présentée comme un mot de passe valide.
- **Dépendances :** EF02, ENF01, ENF02, ENF05, ENF06.
- **Justification :** conserver la fonction essentielle et retirer l’hypothèse de navigation Web et le délai arbitraire non justifié.

#### EF02 — Administration des comptes et attribution des droits cumulables

- **Groupe :** A. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q18, Q20.

- **Description détaillée :** créer, consulter, modifier et désactiver des comptes dans l’entreprise autorisée ; attribuer un ou plusieurs rôles selon une matrice approuvée. Un employé, une ressource chauffeur et un compte sont distincts.
- **Acteur :** administrateur de l’entreprise habilité ; utilisateur concerné pour l’effet des droits.
- **Conditions préalables :** matrice action/rôle/périmètre validée ; procédure de création du premier administrateur définie.
- **Comportement attendu :** contrôler l’unicité de l’identifiant dans le domaine d’authentification retenu ; enregistrer les rôles ; appliquer leurs permissions cumulées dans l’entreprise. Révoquer les accès d’un compte désactivé aux prochaines actions, y compris dans une session déjà ouverte.
- **Règles métier :** aucun rôle chauffeur créé par défaut ; aucune permission interentreprise par cumul ; compte historique désactivé plutôt que supprimé. REC : empêcher la suppression du dernier administrateur actif sans remplacement autorisé. La configuration fine de nouveaux rôles n’est pas exigée si des rôles prédéfinis suffisent.
- **Erreurs/exceptions :** identifiant existant, rôle inconnu, tentative d’élévation non autorisée, désactivation de son propre dernier accès d’administration : refus expliqué et sans changement partiel.
- **CA-EF02-1 :** un compte avec rôles commercial et opérations dispose de l’union approuvée des permissions, sans accès financier non attribué.
- **CA-EF02-2 :** après désactivation, aucune nouvelle lecture ou modification n’est autorisée depuis sa session ouverte ; ses anciens événements restent attribués à son identité.
- **CA-EF02-3 :** un non-administrateur ne peut pas attribuer de rôle, même en déclenchant directement l’opération hors de son écran habituel.
- **RF-EF02 :** supprimer une identité encore référencée ; conférer un accès d’éditeur aux dossiers métier par simple administration technique.
- **Dépendances :** EF01, ENF02, ENF03, ENF08, ENF11.
- **Justification :** respecter les petites équipes et supprimer l’assimilation d’un rôle à une personne ou à un compte chauffeur validé.

### 4.2 Domaine B Données de référence

#### EF03 — Fiches clients et coordonnées opérationnelles

- **Groupe :** B. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q17, Q20.

- **Description détaillée :** créer, rechercher, consulter et corriger des fiches clients réutilisables. Distinguer l’identification du client et les lieux réels utilisés pour une mission.
- **Acteur :** employé habilité à gérer les clients ; lecteurs autorisés.
- **Conditions préalables :** champs minimaux selon type de client approuvés ; règle d’identification fiscale contextualisée.
- **Comportement attendu :** conserver au minimum un identifiant stable et un nom/libellé ; saisir contacts et adresses utiles ; rechercher avant création ; contrôler les doublons exacts et avertir sur les doublons probables.
- **Règles métier :** un identifiant fiscal n’est obligatoire que si la catégorie de client et le parcours validés le nécessitent. Un nom partagé ne prouve pas un doublon. Une adresse de siège n’est pas automatiquement un lieu de déchargement. Une fiche utilisée ne peut être supprimée en détruisant ses liens ; l’archivage est la recommandation V1. Une modification ne réécrit pas silencieusement les conditions d’une mission confirmée.
- **Erreurs/exceptions :** contact incomplet, fiscal non applicable, client archivé ou homonyme ; demander la donnée nécessaire au moment utile plutôt que bloquer toute création.
- **CA-EF03-1 :** deux homonymes peuvent avoir des fiches distinctes ; deux identifiants fiscaux normalisés identiques dans l’entreprise sont signalés selon la règle approuvée.
- **CA-EF03-2 :** après correction de l’adresse du client, une mission confirmée garde son lieu convenu ; sa correction passe par EF06 et EF15.
- **CA-EF03-3 :** un client référencé peut être archivé sans perdre ses demandes, montants ni historique ; une nouvelle demande signale cet état.
- **RF-EF03 :** exiger un identifiant fiscal fictif pour un client non concerné ; fusionner automatiquement des homonymes.
- **Dépendances :** EF05, EF06, EF23, ENF07, ENF08, ENF12.
- **Justification :** éviter la rigidité administrative et la corruption rétroactive des opérations.

#### EF04 — Véhicules et chauffeurs comme ressources distinctes

- **Groupe :** B. **Priorité proposée :** P0, inchangée. **Statut de révision :** divisée et clarifiée sous référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q09, Q17.

- **Description détaillée :** EF04a gère les caractéristiques opérationnelles des véhicules ; EF04b gère l’identification et les qualifications utiles des chauffeurs. Cette division de responsabilité ne crée ni compte chauffeur ni module de maintenance.
- **Acteur :** gestionnaire de ressources habilité ; coordinateur en consultation.
- **Conditions préalables :** unités retenues et règles de qualification définies ; distinction entre fiche incomplète et ressource affectable.
- **Comportement attendu :** enregistrer véhicule avec immatriculation, type et capacités utiles ; chauffeur avec identité, contact utile et permis/validité lorsque requis. Afficher actif, archivé ou informations à compléter.
- **Règles métier :** immatriculation normalisée unique dans l’entreprise ; capacités strictement positives lorsqu’elles sont renseignées ; ne pas exiger volume et tonnage sans besoin. EF09 vérifie les dimensions retenues et la qualification requise sur la période. Le fait d’être chauffeur n’implique pas systématiquement la même catégorie de permis.
- **Erreurs/exceptions :** capacité inconnue, immatriculation dupliquée, permis expiré ou validité couvrant seulement une partie de la mission ; conserver la fiche si utile, mais ne pas la présenter comme éligible à une confirmation qui exige ces informations.
- **CA-EF04-1 :** une capacité de 5 tonnes est comparable à une charge de 4 000 kg après conversion définie ; une capacité négative est refusée.
- **CA-EF04-2 :** deux véhicules de la même entreprise ne peuvent pas partager la même immatriculation normalisée ; leurs anciennes missions survivent à un archivage.
- **CA-EF04-3 :** un chauffeur dont la qualification requise n’est pas valable pour la période n’est pas confirmable ; le motif est indiqué sans créer de compte utilisateur.
- **RF-EF04 :** rendre une ressource archivée affectable par simple recherche ; modifier une capacité sans recontrôler les missions futures concernées.
- **Dépendances :** EF09, EF10, EF11, EF12, ENF07, ENF08.
- **Justification :** séparer les objets, conserver les unités et déplacer les contrôles d’éligibilité vers l’affectation.

**Sous références :** EF04a véhicule est vérifiée par CA-EF04-1 et CA-EF04-2 ; EF04b chauffeur est vérifiée par CA-EF04-3. Les règles communes, statuts et dépendances de la fiche parent s’appliquent aux deux.

### 4.3 Domaine C Demandes et gestion commerciale simple

#### EF05 — Création et cycle des demandes des deux parcours

- **Groupe :** C. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q02, Q03, Q06, Q15.

- **Description détaillée :** créer une demande identifiée comme transport seul ou vente avec livraison, puis la compléter, la valider ou l’annuler. Une demande exprime un besoin ; elle ne confirme pas automatiquement une date ni une ressource.
- **Acteur :** commercial ou coordinateur habilité ; responsable pour les validations réservées.
- **Conditions préalables :** client identifiable ; règles de validation approuvées.
- **Comportement attendu :** attribuer une référence unique, conserver type et statut ; transporter les mêmes données vers le traitement commun. Proposition de cycle minimal de demande : brouillon → validée → clôturée, ou annulée ; mission et commande ont leurs propres états.
- **Règles métier :** transport seul sans commande de vente ; vente avec livraison reliée à EF07. REC de cardinalité à valider : au plus une mission active par demande V1, pas de fractionnement/groupage. La conversion répétée restitue le lien existant. Après confirmation, changement de type ou suppression ne doit pas casser les liens ; préférer annulation/correction motivée selon la politique approuvée.
- **Erreurs/exceptions :** client/type absent à validation ; double demande suspectée ; dossier déjà converti ; annulation après frais ou paiements : conserver ces faits et déclencher examen financier, sans remboursement automatique.
- **CA-EF05-1 :** un transport seul validé peut être planifié sans créer de commande ; une vente-livraison utilise le lien EF07.
- **CA-EF05-2 :** deux demandes similaires peuvent être signalées sans être automatiquement fusionnées ; une même action répétée après incident ne crée pas une seconde demande par inadvertance.
- **CA-EF05-3 :** annuler une demande affectée conserve la mission et son historique avec état cohérent ; les réservations futures sont libérées selon EF10 et les mouvements financiers restent visibles.
- **RF-EF05 :** afficher une date souhaitée comme confirmée avant l’affectation validée ; supprimer une demande liée en effaçant ses traces.
- **Dépendances :** EF03, EF06, EF07, EF08, EF10, EF13, EF18, ENF05, ENF08, ENF13.
- **Justification :** compléter le cycle et éviter la confusion demande/engagement et les trajets dupliqués.

#### EF06 — Contenu opérationnel, unités et conditions de validation

- **Groupe :** C. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q09, Q12, Q13.

- **Description détaillée :** décrire les biens, quantités, unités, lieux et fenêtres souhaitées ; conserver les données nécessaires à l’évaluation de la charge et aux montants convenus. Distinguer informations souhaitées, planifiées et réelles.
- **Acteur :** commercial ou coordinateur habilité.
- **Conditions préalables :** demande créée ; catalogue de champs et unités minimaux approuvé.
- **Comportement attendu :** permettre un brouillon incomplet ; avant confirmation, exiger client, départ, arrivée, période cohérente, description et données de charge nécessaires au véhicule. Le montant peut rester à négocier au brouillon ; son statut doit être explicite.
- **Règles métier :** calculer poids total seulement avec quantité, unité et poids unitaire compatibles, ou enregistrer un total déclaré identifié comme tel ; ne pas convertir des cartons en tonnes sans donnée de conversion. Conserver lieux convenus et composantes vente/transport ; leur affectation financière relève d’EF18. Une modification de charge, lieu ou période après planification exige un nouveau contrôle des ressources.
- **Erreurs/exceptions :** poids/volume inconnu, créneau inversé, unité incompatible, adresse imprécise, modification compromettant la mission : indiquer ce qui reste non validé et ne pas confirmer implicitement.
- **CA-EF06-1 :** 100 unités de 20 kg donnent 2 000 kg ; 100 unités sans poids ne donnent aucun tonnage inventé.
- **CA-EF06-2 :** une date-heure de fin antérieure au début est refusée ; un trajet traversant minuit avec dates cohérentes est accepté.
- **CA-EF06-3 :** une augmentation de charge après affectation déclenche le recontrôle EF09/11 ; le changement ne maintient pas silencieusement une confirmation devenue invalide.
- **RF-EF06 :** remplacer une valeur inconnue par zéro ; recopier des articles de vente comme nouvelle dette de transport.
- **Dépendances :** EF04, EF05, EF07, EF09, EF11, EF16, EF18, ENF07, ENF12.
- **Justification :** rendre les calculs fondés et définir le minimum nécessaire à chaque étape.

#### EF07 — Vente minimale et liaison unique à sa livraison

- **Groupe :** C. **Priorité proposée :** P0 pour le parcours A maintenu par CAD02 ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q02, Q03, Q06, Q13, Q15.

- **Description détaillée :** enregistrer une commande simple avec client, lignes de produits, quantités et montants, puis créer ou relier sa demande/mission de livraison en réutilisant les informations utiles. Aucun stock, achat fournisseur ou calcul comptable complet n’est inclus.
- **Acteur :** commercial ; coordinateur pour le lien de livraison.
- **Conditions préalables :** parcours A maintenu par CAD02 ; règles de montant, de statut commercial et de cardinalité validées.
- **Comportement attendu :** établir un lien consultable dans les deux sens ; conserver lignes commerciales dans la commande et données de charge dans l’opération commune, sans deuxième saisie obligatoire. L’affectation d’un véhicule ne signifie ni vente payée ni livraison achevée.
- **Règles métier :** REC V1 : une commande et sa demande de livraison ne donnent qu’une mission active ; modification des lignes après confirmation traçable et recontrôlée si charge/montant changent. Ne pas maintenir deux valeurs autonomes d’un même montant dû. Les remises, taxes et ventes sans livraison ne sont pas ajoutées par défaut ; leur nécessité minimale est à décider.
- **Erreurs/exceptions :** livraison déjà liée, commande annulée, lignes incohérentes, lien vers un autre client/entreprise ; refuser le lien invalide et conserver l’état initial.
- **CA-EF07-1 :** une commande à deux lignes conserve produits, quantités et montants après création de sa livraison ; le client et les lieux utiles sont réutilisés puis vérifiables.
- **CA-EF07-2 :** relancer « créer la livraison » retrouve la mission existante au lieu d’en créer une seconde ; les deux dossiers renvoient l’un vers l’autre.
- **CA-EF07-3 :** une affectation planifiée ne fait pas passer la commande à « livrée » ou « payée » ; un montant déjà porté par la vente n’est pas facturé une seconde fois par sa mission.
- **RF-EF07 :** créer un module de stock pour satisfaire cette exigence ; convertir de façon destructive et perdre les lignes.
- **Dépendances :** EF03, EF05, EF06, EF10, EF13, EF18, EF20, ENF05, ENF07, ENF12, ENF13.
- **Justification :** indispensable à un parcours A réel ; préserver Basic Business Management sans construire un ERP.

### 4.4 Domaine D Planification et affectation

#### EF08 — Consultation du planning commun des missions

- **Groupe :** D. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q06, Q10, Q21.

- **Description détaillée :** consulter toutes les missions autorisées des deux parcours avec période prévue, affectations, état courant et conflits connus. La présentation reste à concevoir par l’équipe UI/UX.
- **Acteur :** coordinateur et lecteurs autorisés.
- **Conditions préalables :** missions enregistrées ; référentiel d’états EF13 approuvé.
- **Comportement attendu :** distinguer demandes/missions à planifier, ressources engagées et indisponibilités ; rendre consultables période, statut, source et ancienneté utile de l’information ; accéder au dossier détaillé.
- **Règles métier :** aucun cycle de statut parallèle ; une mission extérieure suit les mêmes contrôles ; une absence d’affectation n’est pas un véhicule libre confirmé. Les souhaits client ne sont pas assimilés à la réservation.
- **Erreurs/exceptions :** aucun résultat ou données non rafraîchies : le signaler ; mission sans date au brouillon : la rendre retrouvable sans période fictive.
- **CA-EF08-1 :** les missions A et B prévues dans la même période sont consultables ensemble avec leurs ressources et leur état unique EF13.
- **CA-EF08-2 :** une mission à planifier sans horaire confirmé reste retrouvable ; aucune ressource n’apparaît réservée avant engagement EF10.
- **CA-EF08-3 :** après modification validée puis actualisation, planning et fiche donnent mêmes période et état ; un échec d’actualisation est visible.
- **RF-EF08 :** terminer une mission depuis une règle locale distincte d’EF13 ; présenter le planning comme un suivi GPS.
- **Dépendances :** EF05, EF10, EF11, EF12, EF13, EF14, EF15, EF23, ENF03, ENF06.
- **Justification :** supprimer la duplication des transitions tout en conservant la vue de travail essentielle.

#### EF09 — Évaluation de la disponibilité et de la compatibilité

- **Groupe :** D. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q08, Q09.

- **Description détaillée :** évaluer un véhicule et un chauffeur sur toute la période d’occupation prévue, en tenant compte des missions enregistrées, indisponibilités, capacités et qualifications retenues.
- **Acteur :** coordinateur habilité.
- **Conditions préalables :** période définie ; données de charge utiles connues ; règles d’éligibilité approuvées.
- **Comportement attendu :** indiquer compatible, incompatible ou information insuffisante, avec raison ; utiliser EF11 pour les chevauchements et EF12 pour les indisponibilités. Le résultat est une aide sur les informations enregistrées, pas une preuve de disponibilité physique.
- **Règles métier :** occupation incluant chargement, trajet, déchargement et, si nécessaire, repositionnement/retour ; durées estimées manuellement, sans calcul automatique d’itinéraire. REC : surcharge connue bloquante et données indispensables inconnues empêchant la confirmation. Contrôler les dimensions de capacité effectivement applicables avec unités communes. Une consultation ne réserve pas.
- **Erreurs/exceptions :** fin inconnue d’une immobilisation, permis non vérifiable, transfert entre lieux non estimé : ne pas conclure « disponible » ; exiger une estimation opérationnelle ou résolution autorisée explicite.
- **CA-EF09-1 :** mission prévue jusqu’à 15 h avec déchargement jusqu’à 16 h : la ressource n’est pas proposée compatible à 15 h 30.
- **CA-EF09-2 :** charge de 6 tonnes et capacité de 5 tonnes : confirmation impossible selon la règle proposée, avec motif ; charge inconnue n’est pas considérée nulle.
- **CA-EF09-3 :** une indisponibilité ou une mission extérieure sur un sous-intervalle rend la période incompatible ; toute modification avant engagement entraîne un recontrôle EF10.
- **RF-EF09 :** valider sur la seule heure de départ ; traiter une recherche initiale comme une réservation durable.
- **Dépendances :** EF04, EF06, EF10, EF11, EF12, EF14, EF16, ENF07, ENF13.
- **Justification :** couvrir le temps réellement immobilisé et séparer conseil de disponibilité et engagement.

#### EF10 — Affectation, réservation et réaffectation cohérentes

- **Groupe :** D. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q03, Q04, Q05, Q06, Q08, Q10.

- **Description détaillée :** confirmer l’engagement d’un véhicule et d’un chauffeur pour une mission et sa période, puis permettre leur remplacement autorisé sans perdre l’historique.
- **Acteur :** coordinateur habilité à confirmer.
- **Conditions préalables :** demande et données obligatoires validées ; contrôles EF09/11 satisfaits au moment de l’enregistrement.
- **Comportement attendu :** confirmer ensemble les ressources nécessaires et la période ; rendre l’engagement visible aux autres utilisateurs. En réaffectation, contrôler le nouveau couple avant de remplacer l’engagement précédent ; si l’opération échoue, conserver l’affectation antérieure cohérente.
- **Règles métier :** une proposition partielle peut rester au brouillon ; une mission ne devient planifiée qu’avec les ressources requises. REC V1 : un véhicule et un chauffeur par mission. L’annulation avant départ libère la réservation future ; les heures déjà réalisées restent historiques. Un changement en cours doit préciser sa date d’effet et conserver le segment antérieur, ou être déclaré hors procédure standard jusqu’à décision de l’équipe. Aucun document imprimé n’est obligatoire pour cette exigence.
- **Erreurs/exceptions :** autre utilisateur ayant réservé entre consultation et validation, ressource devenue indisponible, mission annulée, réaffectation en cours non prise en charge : blocage explicite sans demi-réservation.
- **CA-EF10-1 :** après confirmation, véhicule et chauffeur apparaissent engagés sur la même période ; aucune réservation isolée n’est créée en cas d’échec.
- **CA-EF10-2 :** une réaffectation valide remplace les engagements futurs et conserve auteur, ressources précédentes et période d’effet ; une tentative invalide ne libère pas l’ancien engagement.
- **CA-EF10-3 :** deux confirmations concurrentes incompatibles ne peuvent pas toutes deux aboutir ; un utilisateur reçoit une explication du conflit.
- **RF-EF10 :** faire passer à planifiée une mission partiellement affectée ; exiger une feuille de route non définie pour valider la réservation.
- **Dépendances :** EF08, EF09, EF11, EF12, EF13, EF15, ENF05, ENF08, ENF13.
- **Justification :** faire d’EF10 le point unique d’engagement, sans imposer l’architecture ni un livrable d’impression.

#### EF11 — Règle commune de chevauchement et réévaluation des conflits

- **Groupe :** D. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q07, Q08.

- **Description détaillée :** détecter les incompatibilités temporelles d’une même ressource pour toute création ou modification d’occupation ; distinguer refus d’un nouvel engagement et conflit apparu sur des missions déjà engagées.
- **Acteur :** coordinateur ; contrôle système à l’action.
- **Conditions préalables :** périodes complètes ou statut d’incertitude explicite ; convention de limites validée.
- **Comportement attendu :** comparer missions et indisponibilités ; indiquer les références autorisées et périodes concernées ; recontrôler après changement d’horaire, de ressource, retard ou déchargement prolongé.
- **Règles métier :** REC : intervalles [début, fin[ ; chevauchement si début A < fin B et début B < fin A. Deux périodes adjacentes ne sont acceptables que si le repositionnement et les marges nécessaires sont déjà inclus. Aucune marge chiffrée arbitraire. Une occupation réelle dépasse la prévision jusqu’à information de libération : elle ne doit pas être considérée terminée au seul dépassement de l’heure prévue. Pas d’annulation ni de décalage automatique en cascade.
- **Erreurs/exceptions :** fin inconnue, conflit créé par panne ou retard, durée inversée ; conserver le fait réel, signaler le conflit, empêcher de nouvelles confirmations incompatibles et demander traitement humain. La politique de blocage en cas de fin inconnue doit être approuvée.
- **CA-EF11-1 :** [10 h, 12 h[ et [11 h, 13 h[ sur le même chauffeur sont incompatibles ; [12 h, 13 h[ est adjacent, sous réserve de transit déjà pris en compte.
- **CA-EF11-2 :** une fin estimée repoussée de 14 h à 16 h rend visible le conflit avec une mission de 15 h, sans déplacer cette dernière silencieusement.
- **CA-EF11-3 :** la même règle est utilisée depuis affectation, réaffectation et indisponibilité ; les contrôles restent valides lors de deux écritures concurrentes.
- **RF-EF11 :** autoriser un contournement non défini ; effacer une panne pour préserver artificiellement un planning sans conflit.
- **Dépendances :** EF09, EF10, EF12, EF14, EF16, ENF07, ENF13.
- **Justification :** éliminer les variantes de règle et rendre explicite l’impact des aléas réels.

#### EF12 — Périodes d’indisponibilité et missions impactées

- **Groupe :** D. **Priorité proposée :** P0 ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q08, Q09.

- **Description détaillée :** enregistrer les périodes où un véhicule ou chauffeur ne peut pas être engagé, et traiter les missions déjà prévues impactées. La saisie d’un entretien est un blocage de ressource, pas une gestion complète de maintenance.
- **Acteur :** coordinateur ou gestionnaire de ressources habilité.
- **Conditions préalables :** ressource existante ; début et nature opérationnelle du blocage connus.
- **Comportement attendu :** saisir début, fin estimée ou inconnue, motif suffisant ; rendre la ressource non compatible avec les engagements concernés ; afficher les missions affectées et permettre une réaffectation EF10.
- **Règles métier :** une panne réelle doit pouvoir être enregistrée même si elle contredit une mission confirmée ; le conflit devient une action à résoudre. Pas de détail médical nécessaire : une catégorie d’absence suffit. Modifier ou terminer une indisponibilité conserve l’historique. Une fin estimée n’est pas une réparation constatée.
- **Erreurs/exceptions :** période inversée, doublon chevauchant, indisponibilité sans fin, annulation d’un blocage déjà commencé : contrôle, avertissement et trace selon le cas.
- **CA-EF12-1 :** une indisponibilité de 9 h à 12 h empêche une affectation de 11 h à 13 h, mais ne masque pas la fiche pour les périodes non concernées.
- **CA-EF12-2 :** une panne déclarée pendant une mission est conservée et liste les missions suivantes impactées ; aucune mission n’est réaffectée automatiquement.
- **CA-EF12-3 :** la prolongation ou clôture d’une indisponibilité entraîne une nouvelle évaluation et reste traçable.
- **RF-EF12 :** refuser de saisir la panne au motif que le véhicule est réservé ; afficher comme libre une ressource à fin de blocage inconnue sans décision explicite.
- **Dépendances :** EF04, EF09, EF10, EF11, EF15, ENF08.
- **Justification :** une vérification P0 n’est fiable que si ses entrées d’indisponibilité sont disponibles en V1.

### 4.5 Domaine E Exécution et suivi manuel

#### EF13 — Cycle de vie des missions et changements d’état contrôlés

- **Groupe :** E. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q06, Q10, Q11, Q12.

- **Description détaillée :** mettre à jour manuellement l’état d’une mission à partir d’informations reçues, selon un seul cycle validé. Un statut opérationnel ne modifie pas automatiquement le règlement commercial.
- **Acteur :** employé autorisé aux opérations ; pas de compte terrain implicite.
- **Conditions préalables :** mission créée ; liste et transitions approuvées ; ressources confirmées avant départ.
- **Comportement attendu :** enregistrer état, auteur, heure de saisie et heure réelle si connue ; créer simultanément l’événement métier consultable. Un retard et un incident sont des attributs/événements, pas des états remplaçant le cycle.
- **Règles métier :** proposition ci-dessous ; motif d’annulation requis ; fin opérationnelle distincte de solde financier. Une correction après clôture conserve l’état antérieur ; une mission terminée ne se transforme pas en annulation ordinaire. Un arrêt après départ nécessite un motif et conserve événements, occupation réelle et frais ; procédure exacte à valider.
- **Erreurs/exceptions :** état non autorisé, transition sans prérequis, événement inconnu, correction antidatée incohérente ; ne pas obliger à inventer des étapes. Si un appel arrive tard, permettre une saisie cohérente des faits connus selon la procédure approuvée.
- **CA-EF13-1 :** à planifier → terminée sans justification ni étapes requises est refusé ; le départ est refusé sans ressources confirmées.
- **CA-EF13-2 :** une mission arrivée sans attente peut passer en déchargement ; l’état d’attente n’est jamais imposé fictivement.
- **CA-EF13-3 :** une clôture conserve les dates connues et l’historique, sans marquer automatiquement la dette comme payée ; une correction postérieure est ajoutée avec motif.
- **RF-EF13 :** état modifié sans événement correspondant ; annulation d’une mission terminée par effacement de sa réalisation.
- **Dépendances :** EF05, EF07, EF10, EF14, EF15, EF16, EF18, ENF05, ENF07, ENF08.
- **Justification :** remplacer deux listes incompatibles par une proposition unique et vérifiable.

**Transitions proposées — HYP à approuver :**

| Depuis | Vers | Condition |
|---|---|---|
| À planifier | Planifiée | Affectation et période confirmées selon EF10 |
| Planifiée | À planifier | Retrait de planification avant départ, motivé et ressources libérées |
| Planifiée | En cours | Départ signalé ; ressources et période cohérentes |
| En cours | Arrivée | Arrivée signalée, heure réelle renseignée si connue |
| Arrivée | En attente de déchargement | Attente effectivement déclarée |
| Arrivée / En attente de déchargement | En déchargement | Début signalé |
| En déchargement | Terminée | Fin déclarée et conditions de clôture remplies |
| Arrivée | Terminée | Déchargement non applicable et conditions de clôture remplies |
| À planifier / Planifiée | Annulée | Motif et conséquences sur réservations/dossier examinés |
| En cours / Arrivée / Attente / En déchargement | Arrêt exceptionnel à valider | Ne pas l’assimiler silencieusement à une annulation avant départ ; conserver les faits et traiter la libération réelle |
| Terminée / Annulée | Aucun retour ordinaire | Correction tracée selon procédure autorisée ; réouverture éventuelle à décider |

La ligne d’arrêt exceptionnel signale un **blocage de validation** : aucun nouvel état officiel n’est ajouté sans décision humaine. Pour une démonstration limitée au parcours normal, ce cas peut être déclaré non pris en charge avec procédure manuelle explicite, sans fausse promesse d’usage opérationnel complet.

#### EF14 — Retards, incidents et estimations déclarées

- **Groupe :** E. **Priorité proposée :** P0 pour le signalement simple et l’impact planning ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q08, Q21.

- **Description détaillée :** enregistrer un retard ou incident connu, sa raison lorsqu’elle est connue, les informations temporelles disponibles et son effet possible sur les occupations suivantes.
- **Acteur :** employé opérations habilité.
- **Conditions préalables :** mission connue ; données prévues conservées.
- **Comportement attendu :** ajouter l’information reçue ; permettre « cause inconnue » et « estimation indisponible » ; conserver les estimations successives, l’heure prévue initiale et les heures réelles. Afficher l’événement aux personnes autorisées et réévaluer EF11 si l’occupation est modifiée.
- **Règles métier :** ETA = estimation manuelle, sans garantie ; incident possible sans retard ; un retard peut exister sans nouvelle ETA. L’employé décide et effectue le contact client hors automatisation du logiciel. Aucune couleur unique ni message externe automatique imposé.
- **Erreurs/exceptions :** information tardive, estimation antérieure aux faits déjà connus, incident dupliqué ou clôturé ; refuser l’incohérence, autoriser correction et fin d’incident tracées.
- **CA-EF14-1 :** un retard sans cause ni ETA peut être enregistré avec inconnu explicite et horodatage, sans valeur inventée.
- **CA-EF14-2 :** deux ETA successives laissent consultables l’heure initiale et les deux estimations avec leur date de saisie.
- **CA-EF14-3 :** repousser la libération prévue d’une ressource déclenche le contrôle des missions suivantes ; aucune date client n’est automatiquement garantie.
- **RF-EF14 :** remplacer l’heure réelle d’arrivée par une ETA ; effacer l’ancienne prévision ; considérer un statut ancien comme une information actuelle certaine.
- **Dépendances :** EF08, EF11, EF13, EF15, EF17, EF22, ENF08.
- **Justification :** le traitement des retards répond à un problème central et conditionne la fiabilité du planning ; il ne nécessite ni GPS ni prédiction.

#### EF15 — Consultation de l’historique métier des missions

- **Groupe :** E, transversal à D/F/G. **Priorité proposée :** P0 pour le noyau d’événements ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q11, Q20.

- **Description détaillée :** rendre consultable une chronologie des créations, validations, affectations, réaffectations, changements d’état, incidents, corrections et annulations. Les données financières ne sont visibles que selon les permissions.
- **Acteur :** lecteur autorisé de la mission ; émetteur de correction habilité.
- **Conditions préalables :** capture ENF08 active ; liste d’événements et visibilité approuvées.
- **Comportement attendu :** afficher identifiant d’événement, type, auteur stable, date-heure de saisie, date-heure réelle connue et informations métier utiles. Relier correction et événement corrigé ; permettre de distinguer ordre de saisie et ordre des faits.
- **Règles métier :** pas de modification/suppression d’événement par les opérations ordinaires ; correction par ajout. Précision de stockage et ordre technique suffisants pour départager deux événements saisis la même minute ; aucune promesse d’inaltérabilité contre tout administrateur système.
- **Erreurs/exceptions :** utilisateur désactivé, heure réelle inconnue, saisie rétroactive, deux événements de même heure ; conserver identité historique et ordre de saisie.
- **CA-EF15-1 :** un départ réel à 9 h saisi à 9 h 20 affiche distinctement les deux heures et l’auteur.
- **CA-EF15-2 :** corriger une arrivée de 10 h à 10 h 15 conserve l’ancienne valeur, la correction et son motif, sans dupliquer l’événement comme nouvelle arrivée.
- **CA-EF15-3 :** deux événements enregistrés à la même minute restent distinguables et ordonnables ; un lecteur non financier ne voit pas les montants protégés dans les détails.
- **RF-EF15 :** permettre un bouton « supprimer historique » ; perdre l’auteur après désactivation du compte.
- **Dépendances :** EF02, EF10, EF13, EF14, EF16, EF18, ENF03, ENF08.
- **Justification :** rendre les exigences de suivi et de correction testables, avec une seule capture transversale.

### 4.6 Domaine F Déchargement et immobilisation

#### EF16 — Conditions, étapes et temps de déchargement

- **Groupe :** F. **Priorité proposée :** P0 pour le minimum d’arrivée, conditions et occupation ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q10, Q11, Q12.

- **Description détaillée :** conserver les responsabilités et conditions convenues, la fenêtre prévue et les dates-heures réelles connues d’arrivée, début et fin de déchargement ; distinguer attente, déchargement et données manquantes.
- **Acteur :** commercial/coordinateur pour les conditions ; employé opérations pour les faits reçus.
- **Conditions préalables :** mission concernée ; déchargement applicable ou non renseigné explicitement ; responsabilités à confirmer avant la mission lorsqu’elles sont nécessaires.
- **Comportement attendu :** saisir qui organise le déchargement, moyens attendus, créneau et informations connues ; enregistrer les faits manuellement ; déduire attente = début − arrivée et durée = fin − début seulement lorsque leurs bornes sont connues et cohérentes. Réévaluer la libération des ressources et les conflits suivants.
- **Règles métier :** arrivée ≤ début ≤ fin pour les faits connus ; traversée de minuit autorisée avec dates complètes. Une valeur inconnue reste « non renseignée » ; une attente nulle signifie début égal à arrivée. Le service payant et les pénalités ne sont pas retenus ; aucun supplément n’est généré par une attente.
- **Erreurs/exceptions :** responsabilité encore inconnue, client non prêt, fin non reçue, heure corrigée après clôture ; signaler et recalculer les durées affectées. Une fin connue sans début connu peut être conservée sans inventer la durée ; la clôture dépend de la politique approuvée.
- **CA-EF16-1 :** arrivée 9 h 15, début 9 h 30, fin 10 h 15 : attente 15 min, déchargement 45 min.
- **CA-EF16-2 :** arrivée 23 h 50 et début le lendemain à 0 h 10 donnent 20 min ; début inconnu donne attente/durée indisponibles, pas zéro.
- **CA-EF16-3 :** une attente prolongeant l’occupation révèle les conflits suivants ; les conditions convenues restent consultables et aucun montant dû n’est créé automatiquement.
- **RF-EF16 :** fin antérieure à une arrivée ou un début connus ; terminer automatiquement l’occupation à l’heure prévue malgré une attente déclarée.
- **Dépendances :** EF06, EF09, EF11, EF13, EF15, EF18, EF22, ENF07, ENF08.
- **Justification :** traiter l’un des problèmes centraux des sources et séparer responsabilité, événements et hypothèse commerciale.

### 4.7 Domaine G Suivi financier simplifié

#### EF18 — Montants convenus et cycle des règlements

- **Groupe :** G. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q13, Q14, Q15.

- **Description détaillée :** porter une seule fois les sommes dues pour un dossier, distinguer composantes vente et transport, puis enregistrer les règlements partiels ou complets avec un état de confirmation. L’application enregistre des faits financiers ; elle ne transfère pas de fonds.
- **Acteur :** personnel habilité aux montants et paiements ; commercial selon permissions approuvées.
- **Conditions préalables :** dossier valide ; devise, précision, droits de confirmation et politique de correction décidés.
- **Comportement attendu :** saisir un montant convenu et ses ajustements autorisés ; créer un règlement relié à une seule obligation ou selon une répartition explicitement validée. Proposition minimale de cycle : annoncé → enregistré en attente → encaissement confirmé ; rejet/annulation motivé pour un mouvement non confirmé ; correction par contre-mouvement pour un mouvement déjà confirmé.
- **Règles métier :** un règlement enregistré peut être confirmé dans la même action si les preuves et droits requis sont présents ; son statut ne devient pas confirmé du seul fait de sa saisie. Pas de double comptage en consultant la vente puis sa livraison. Une annulation de mission ne supprime ni dette ni recette sans décision sur le montant réellement dû. Toute modification après confirmation exige auteur et motif.
- **Erreurs/exceptions :** montant absent avant accord, règlement nul/négatif ordinaire, doublon probable, issue technique incertaine, montant supérieur au solde. REC V1 tant qu’aucune politique contraire n’est approuvée : bloquer le trop-perçu à la confirmation et demander une décision ; ne pas créer automatiquement un avoir. Un trop-perçu réel doit pouvoir être régularisé par une procédure approuvée avant usage opérationnel.
- **CA-EF18-1 :** vente 4 000 et transport 1 000 donnent une dette totale de 5 000 ; l’accès à la mission liée ne crée pas une deuxième dette de 1 000.
- **CA-EF18-2 :** un acompte confirmé de 2 000 et un paiement annoncé de 1 000 sont distincts ; seule la somme confirmée alimente EF20.
- **CA-EF18-3 :** corriger un encaissement confirmé conserve l’original et un mouvement de correction lié ; une reprise après incident ne crée pas deux recettes.
- **RF-EF18 :** supprimer un encaissement confirmé ; considérer un virement annoncé comme reçu ; imposer remboursement ou avoir automatique à l’annulation.
- **Dépendances :** EF05, EF07, EF19, EF20, EF21, ENF05, ENF07, ENF08, ENF13.
- **Justification :** lever les ambiguïtés ayant un effet direct sur les soldes et respecter la gestion commerciale simple.

#### EF19 — Mode, dates et références des règlements

- **Groupe :** G. **Priorité proposée :** P0 pour les métadonnées minimales ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q14, Q24.

- **Description détaillée :** conserver le mode, le montant, le dossier, la date du fait financier, la date de saisie, la référence utile et l’auteur/confirmation de chaque règlement selon son étape.
- **Acteur :** employé financier habilité.
- **Conditions préalables :** liste des modes retenus et données requises par mode approuvées ; paiement EF18 existant ou créé dans la même opération.
- **Comportement attendu :** proposer seulement les modes retenus ; demander les références nécessaires au moment approprié ; rechercher les doublons probables selon entreprise, mode, référence et montant, sans supposer une référence universellement unique.
- **Règles métier :** espèces, chèque et virement sont documentés comme besoins ; traite et mode « autre » restent à valider. Un numéro de chèque ne prouve pas son encaissement ; une annonce sans référence peut rester en attente, mais ne doit pas être confirmée si les éléments requis manquent. Les justificatifs physiques et la confirmation restent de la responsabilité humaine.
- **Erreurs/exceptions :** référence inconnue, deux mouvements légitimes de même montant, paiement antidaté, mode mal sélectionné ; correction tracée et contrôle adapté plutôt qu’un doublon bloqué sur le seul montant.
- **CA-EF19-1 :** un chèque avec numéro mais non confirmé reste en attente ; une confirmation sans donnée requise selon la règle approuvée est refusée.
- **CA-EF19-2 :** un règlement espèces peut être enregistré sans numéro de chèque ; mode, montant, date et auteur restent disponibles.
- **CA-EF19-3 :** une référence déjà utilisée signale le mouvement précédent et permet le traitement explicite d’un doublon ou d’un cas légitime, dans les limites de la politique validée.
- **RF-EF19 :** forcer une référence inventée ; perdre l’heure de saisie en modifiant la date réelle du paiement.
- **Dépendances :** EF18, EF20, ENF07, ENF08.
- **Justification :** les données de preuve minimales sont nécessaires au cycle P0 des paiements ; éviter la fausse équivalence référence/encaissement.

#### EF20 — Calcul des soldes et représentation des régularisations

- **Groupe :** G. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q13, Q14, Q15, Q16.

- **Description détaillée :** calculer les sommes restant dues à partir du montant courant validé et des mouvements confirmés, sans saisie manuelle d’un second solde. Distinguer dossier, composantes et total client sans duplication.
- **Acteur :** employé financier ; lecteurs autorisés.
- **Conditions préalables :** règles EF18/19 validées ; devise et précision communes ; modèle de correction/remboursement approuvé.
- **Comportement attendu :** recalculer après accord, correction, confirmation, annulation de mouvement ou remboursement autorisé ; rendre les mouvements expliquant le résultat consultables.
- **Règles métier :** proposition : **D = montant initial + ajustements de dette validés signés** ; **E = encaissements confirmés − annulations/contre-mouvements d’encaissement confirmés − remboursements confirmés** ; **S = D − E**. Chaque mouvement correctif n’intervient qu’une fois. Un remboursement ne diminue pas automatiquement D : une réduction de prix/annulation commerciale est un ajustement distinct. Les dépenses ne figurent ni dans D ni dans E. Statuts : restant dû si S > 0, soldé si S = 0 ; S < 0 = trop-perçu à traiter si ce cas est admis. « En souffrance » exige une échéance et une règle de retard non définies : ne pas l’utiliser par défaut.
- **Erreurs/exceptions :** correction créant un solde négatif, remboursement supérieur aux fonds nets, données financières non confirmées ou incohérentes ; bloquer l’opération non autorisée et conserver les mouvements existants.
- **CA-EF20-1 :** D = 5 000 ; reçu confirmé 2 000 ; annoncé 1 000 ; dépenses 300 : S = 3 000.
- **CA-EF20-2 :** une réduction validée de dette de 500 après encaissement de 2 000 donne S = 2 500 ; aucune recette n’est modifiée fictivement.
- **CA-EF20-3 :** D initial = 5 000, encaissement = 2 000, dette annulée par ajustement −5 000, remboursement confirmé = 2 000 : D = 0, E = 0, S = 0. L’original et les deux régularisations restent visibles.
- **CA-EF20-4 :** total client = somme des soldes de ses obligations uniques dans la devise retenue ; la même vente-livraison n’est comptée qu’une fois.
- **RF-EF20 :** erreur d’arrondi à la précision retenue ; déduire un règlement annoncé ; soustraire deux fois un remboursement et son contre-mouvement.
- **Dépendances :** EF07, EF18, EF19, EF21, EF22, EF24, ENF05, ENF07, ENF13.
- **Justification :** définir une règle reproductible couvrant corrections et remboursements sans construire une comptabilité générale.

#### EF21 — Dépenses opérationnelles rattachées aux missions

- **Groupe :** G. **Priorité proposée :** P1, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q13, Q15, Q24.

- **Description détaillée :** enregistrer les dépenses réellement engagées pour une mission, avec catégorie, date, montant, référence de justificatif si disponible et auteur ; produire un total des dépenses déclarées.
- **Acteur :** employé habilité au suivi des dépenses ; pas de saisie directe chauffeur supposée.
- **Conditions préalables :** mission existante, même annulée ; catégories minimales et devise définies.
- **Comportement attendu :** ajouter, consulter et corriger les dépenses avec trace ; signaler les doublons probables ; distinguer frais engagés et estimations si ces dernières sont retenues. Le minimum V1 porte sur les frais engagés.
- **Règles métier :** une mission annulée peut avoir des frais réels de carburant ou déplacement ; les autoriser avec motif. Une correction ne détruit pas la trace. Une dépense ne diminue pas la somme due par le client. Aucun calcul de marge nette ; un éventuel écart prix transport/frais doit être nommé et présenté comme partiel, après validation séparée.
- **Erreurs/exceptions :** mission inconnue, montant ordinaire négatif, justificatif non disponible, double saisie suspectée ; référence absente signalée sans prétendre certifier la dépense.
- **CA-EF21-1 :** frais de 350 et 800 donnent un total déclaré de 1 150 ; le solde client reste inchangé.
- **CA-EF21-2 :** une mission annulée accepte un frais antérieurement engagé avec motif et auteur, sans être réactivée.
- **CA-EF21-3 :** une correction conserve montant précédent et nouvelle valeur/contre-mouvement selon le modèle retenu ; aucun écran n’appelle ce total « marge nette ».
- **RF-EF21 :** affecter le frais à une mission d’une autre entreprise ; effacer une dépense réelle du fait d’une annulation.
- **Dépendances :** EF13, EF15, EF18, EF20, EF24, ENF07, ENF08.
- **Justification :** conserver l’utilité financière sans prétention comptable et corriger le refus injustifié des frais d’annulation.

### 4.8 Domaine H Consultation et pilotage

#### EF17 — Liste d’exploitation et dernière information connue

- **Groupe :** H. **Priorité proposée :** P1, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q21, Q22.

- **Description détaillée :** consulter une liste détaillée des missions et blocages utiles à l’exploitation, avec état, ressources, information connue et éléments nécessitant une action.
- **Acteur :** coordinateur et responsable autorisés.
- **Conditions préalables :** données EF08/13–16 disponibles ; permissions appliquées.
- **Comportement attendu :** accéder aux dossiers retardés, en attente ou en conflit ; afficher la dernière mise à jour métier et la date de rafraîchissement de la consultation. Réutiliser EF23 pour les filtres.
- **Règles métier :** « en cours déclaré » n’est pas une observation temps réel. Une information ancienne ou absente reste visible avec sa date ; un seuil d’ancienneté éventuel doit être approuvé. Les taux d’utilisation et le filtrage géographique avancé ne sont pas indispensables à cette liste et restent reportables.
- **Erreurs/exceptions :** résultat vide, connexion aux données interrompue, droits modifiés ; signaler l’état et ne pas présenter un ancien résultat comme actualisé.
- **CA-EF17-1 :** une mission dont la dernière information date de la veille affiche cette date ; le rafraîchissement de la liste ne rajeunit pas l’événement.
- **CA-EF17-2 :** après actualisation réussie, liste et détail exposent les mêmes faits ; un conflit ou retard signalé donne accès à sa cause connue.
- **RF-EF17 :** indiquer « temps réel » ou « véhicule actuellement sur place » à partir d’une ancienne déclaration ; exposer les montants aux lecteurs sans permission.
- **Dépendances :** EF08, EF11, EF13, EF14, EF15, EF16, EF23, ENF03, ENF06.
- **Justification :** distinguer consultation détaillée, synthèse et observation physique.

#### EF22 — Synthèse opérationnelle et financière autorisée

- **Groupe :** H. **Priorité proposée :** P1 ; ancienne P0. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q16, Q21, Q22.

- **Description détaillée :** donner une synthèse légère des missions à planifier, en cours, retards connus, attentes, ressources indisponibles et soldes autorisés, en réutilisant les données sources et les mêmes filtres.
- **Acteur :** responsable, coordinateur, employé financier selon permissions.
- **Conditions préalables :** définitions des indicateurs approuvées ; listes détaillées disponibles.
- **Comportement attendu :** calculer les indicateurs pour un périmètre et une date identifiés ; permettre de retrouver les éléments qui composent un nombre ou montant. Préciser dernière actualisation et limites des saisies manuelles.
- **Règles métier :** compteur de retards signalés distinct d’une estimation automatique de retard ; préciser si les catégories se recoupent pour ne pas additionner des états incompatibles. Les soldes viennent d’EF20 et ne sont pas recalculés par une seconde règle. Une ressource indisponible n’est comptée qu’une fois à l’instant/période choisis.
- **Erreurs/exceptions :** données absentes ou actualisation échouée : indisponible/ancien résultat identifié, pas zéro trompeur ; permissions restreintes : indicateur financier absent ou refusé.
- **CA-EF22-1 :** un indicateur « trois missions en retard signalé » correspond aux trois dossiers détaillés sous mêmes filtres et état de données.
- **CA-EF22-2 :** un utilisateur sans lecture financière ne reçoit aucun montant par compteur, détail, message d’erreur ou export associé.
- **CA-EF22-3 :** un échec d’actualisation est signalé ; une actualisation réussie distingue date de calcul et dernière information des missions.
- **RF-EF22 :** attribuer à un compteur un sens non défini ; refuser toute donnée ancienne sans permettre d’en connaître l’ancienneté.
- **Dépendances :** EF08, EF12, EF14, EF16, EF17, EF20, EF23, ENF02, ENF03, ENF06.
- **Justification :** utile mais non indispensable si les listes sources P0 rendent le parcours complet utilisable.

#### EF23 — Recherche et filtrage explicites

- **Groupe :** H, réutilisé par B–G. **Priorité proposée :** P1 pour les combinaisons avancées, inchangée ; recherche élémentaire nécessaire à EF03/08 conservée dans ces références. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q21, Q22.

- **Description détaillée :** retrouver les dossiers autorisés par référence, client, état, ressource et période, en précisant ce que chaque filtre sélectionne.
- **Acteur :** utilisateur autorisé aux dossiers concernés.
- **Conditions préalables :** champs filtrables et signification des dates définis.
- **Comportement attendu :** combiner les critères par ET ; rendre les filtres actifs visibles ; permettre leur remise à zéro ; distinguer aucun résultat, erreur technique et absence de droit sans révéler l’existence d’un dossier protégé.
- **Règles métier :** préciser date de création, début prévu ou arrivée réelle selon la recherche. Pour un planning, REC : périodes qui intersectent l’intervalle demandé ; pour dates civiles de rapport, début du premier jour inclus et début du jour suivant le dernier exclu, dans le référentiel horaire retenu. Les dossiers sans date ne correspondent pas à un filtre de date, et ce comportement doit être visible/documenté.
- **Erreurs/exceptions :** bornes inversées, caractères spéciaux, homonymes, référence absente, très grand résultat ; limiter/segmenter l’affichage sans supprimer silencieusement des correspondances.
- **CA-EF23-1 :** client + statut + période renvoie exactement l’intersection des trois critères dans le jeu d’essai.
- **CA-EF23-2 :** réinitialiser retire tous les critères utilisateur mais conserve les restrictions d’accès ; une borne inversée est rejetée.
- **CA-EF23-3 :** zéro correspondance affiche un résultat vide explicite ; les caractères spéciaux d’un nom ne provoquent ni erreur ni extension du périmètre.
- **RF-EF23 :** appliquer un OU implicite ; confondre absence de résultat et défaillance ; résultat tronqué non signalé.
- **Dépendances :** EF03, EF08, EF17, EF22, EF24, ENF02, ENF03, ENF07.
- **Justification :** remplacer un refus incompréhensible par un contrat de recherche testable.

#### EF24 — Rapports opérationnels reproductibles

- **Groupe :** H. **Priorité proposée :** P2 ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q16, Q22, Q23.

- **Description détaillée :** produire une synthèse figée, datée et filtrée des missions, retards, attentes déclarées ou soldes autorisés, avec un format initial choisi par l’équipe. Plusieurs formats ne sont pas obligatoires.
- **Acteur :** responsable habilité ; lecture financière spécifique pour les créances.
- **Conditions préalables :** définitions, période, format et périmètre d’export approuvés ; données sources disponibles.
- **Comportement attendu :** rappeler date de génération, filtres, entreprise autorisée, mesures et unités ; indiquer les données manquantes ; préserver une cohérence d’ensemble si des saisies ont lieu pendant la génération. En cas d’échec d’écriture de fichier, ne pas annoncer un rapport disponible.
- **Règles métier :** attente moyenne calculée sur les missions ayant arrivée et début connus, avec nombre de valeurs exclues ; taux de retard seulement si dénominateur et définition du retard sont validés, sinon utiliser un nombre de retards signalés. Les soldes sont ceux d’EF20 à l’état de données utilisé. Un rapport de dépenses n’atteste pas une rentabilité nette.
- **Erreurs/exceptions :** période sans données, destination inaccessible, fichier existant, données modifiées durant calcul ; résultat vide explicite, confirmation d’écrasement si applicable, cohérence de l’extraction ou échec expliqué.
- **CA-EF24-1 :** pour un jeu fixe, filtres et totaux correspondent aux listes et soldes sources ; une mission liée à une vente n’est pas comptée deux fois.
- **CA-EF24-2 :** deux attentes connues de 10 et 30 minutes et une inconnue donnent moyenne 20 minutes, deux observations et une exclusion.
- **CA-EF24-3 :** l’échec d’écriture ne produit aucun message de succès ; le fichier obtenu avec le format retenu est lisible et n’expose aucune donnée hors droits.
- **RF-EF24 :** compter une attente inconnue comme zéro ; exporter des montants financiers à un rôle non habilité.
- **Dépendances :** EF15, EF16, EF20, EF21, EF23, ENF03, ENF05, ENF06.
- **Justification :** préserver les rapports tout en reportant un coût secondaire et en explicitant les incohérences des sources sur les exports.

## 5 Exigences non fonctionnelles par catégorie

### 5.1 Sécurité et confidentialité

#### ENF01 — Protection de l’authentification et des secrets

- **Catégorie :** sécurité. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q18.

- **Description détaillée :** protéger la vérification d’identité et les mots de passe dans l’application Desktop et dans les échanges nécessaires au déploiement retenu, sans imposer URL, jetons ou navigateur.
- **Acteur :** utilisateur ; administrateur pour récupération d’accès.
- **Conditions préalables :** mode de déploiement, politique d’essais et récupération approuvés.
- **Comportement attendu :** stocker un dérivé de mot de passe obtenu par un algorithme de hachage adapté aux mots de passe, salé et paramétré ; ne pas conserver de mot de passe récupérable ou en clair ; masquer les secrets dans journaux et messages. Protéger leur transport si des échanges réseau sont utilisés.
- **Règles :** mécanisme reconnu choisi/documenté par l’architecture, sans algorithme imposé ici. Seuil, fenêtre et durée de limitation des essais à valider ; cinq tentatives n’est qu’une proposition source. Prévoir déblocage sans révélation du mot de passe et sans verrouillage permanent abusif.
- **Erreurs/exceptions :** échec de vérification ou indisponibilité : aucun accès accordé ; récupération suivie sans divulguer les secrets.
- **CA-ENF01-1 :** inspection du stockage et des journaux de test : aucun mot de passe en clair ; deux comptes partageant un même mot de passe n’ont pas une représentation stockée identique grâce au sel propre.
- **CA-ENF01-2 :** selon politique approuvée, le dépassement des essais déclenche la limitation et la récupération prévue ; aucune fonction protégée n’est accessible après déconnexion.
- **CA-ENF01-3 :** dans un déploiement réseau de test, les secrets ne transitent pas en clair ; si le déploiement est strictement local, cette vérification réseau est justifiée comme non applicable.
- **RF-ENF01 :** mot de passe journalisé ; accès accordé lorsque la vérification échoue.
- **Dépendances :** EF01, EF02, ENF06, ENF08, ENF10.
- **Justification :** remplacer une sécurité Web présupposée par des propriétés vérifiables et distinguer hachage et chiffrement.

#### ENF02 — Autorisation effective de chaque opération

- **Catégorie :** contrôle d’accès. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q05.

- **Description détaillée :** appliquer la matrice de permissions à toute action métier au point où elle est réellement exécutée, indépendamment de l’affichage de l’interface.
- **Acteur :** tous les comptes ; administrateur pour la matrice.
- **Conditions préalables :** matrice action/rôle/donnée/entreprise approuvée ; rôle chauffeur non retenu sauf décision ultérieure.
- **Comportement attendu :** vérifier identité active, droit et périmètre lors de lecture, écriture, recherche, export et consultation d’historique ; appliquer les révocations aux actions suivantes.
- **Règles :** refus par défaut d’une opération non autorisée ; cumul de rôles limité au périmètre de l’entreprise. Masquer un bouton peut aider l’usage mais ne constitue pas la garantie de sécurité. La protection contre l’accès direct aux fichiers dépend aussi du déploiement et doit être documentée.
- **Erreurs/exceptions :** rôle retiré pendant ouverture d’un dossier, opération non déclarée dans la matrice : recontrôler puis refuser sans révéler de données protégées.
- **CA-ENF02-1 :** un compte lecteur ne peut ni enregistrer ni supprimer en appelant directement l’opération testée sans passer par les boutons.
- **CA-ENF02-2 :** un commercial non financier n’accède pas aux paiements via fiche, recherche, synthèse, historique ni export.
- **RF-ENF02 :** écriture réussie malgré retrait de permission ; lecture permise parce que le dossier était déjà ouvert.
- **Dépendances :** EF01, EF02, ENF03, ENF08, ENF13 ; tous les domaines.
- **Justification :** conserver l’objectif RBAC sans imposer serveur/API ni faux compte terrain.

#### ENF03 — Confidentialité et séparation des entreprises

- **Catégorie :** confidentialité. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q20.

- **Description détaillée :** empêcher qu’un utilisateur agissant pour une entreprise consulte ou modifie les dossiers d’une autre via les opérations du produit. L’exigence est une garantie de séparation, pas un choix obligatoire de base partagée ou de filtre tenant_id.
- **Acteur :** utilisateurs et administrateurs d’entreprise ; exploitant technique dans ses responsabilités documentées.
- **Conditions préalables :** périmètres d’accès et mode d’adoption par plusieurs entreprises définis ; surfaces de test recensées.
- **Comportement attendu :** appliquer la séparation aux références, liens, recherches, agrégats, journaux consultables, exports et accès aux copies de données. Aucun accès métier de l’éditeur ni collecte d’analyse centrale activés par défaut.
- **Règles :** une installation par entreprise ou des espaces isolés peuvent répondre au besoin ; le concepteur justifie le choix. Le prototype monoentreprise éventuel ne supprime pas cette obligation de conception et son plan de vérification. La conservation et l’effacement restent à décider ; pas de durée inventée.
- **Erreurs/exceptions :** référence d’un dossier tiers fournie à une opération, mauvais rattachement de lien, restauration sur mauvaise destination : refuser ou interrompre sans exposer les données.
- **CA-ENF03-1 :** avec deux jeux d’entreprises, aucune lecture/écriture croisée ne réussit sur fiches, recherche, historique, rapports et associations de références.
- **CA-ENF03-2 :** dans un modèle d’installations séparées, un compte et une configuration de l’installation A ne permettent pas d’ouvrir l’espace B par une opération ordinaire ; les contrôles d’accès au stockage et aux copies sont documentés et testés selon le déploiement.
- **CA-ENF03-3 :** aucune exportation automatique de données identifiantes vers une analyse de l’éditeur n’est active ; tout accès d’assistance éventuel est une décision séparée avec droits explicites.
- **RF-ENF03 :** lien valide vers une ressource d’une autre entreprise ; copie de secours librement consultable par les comptes métier non habilités.
- **Dépendances :** EF02, ENF02, ENF08, ENF09, ENF14 ; tous les domaines.
- **Justification :** distinguer confidentialité actuelle et architecture multi-tenant future, sans promesse d’impossibilité absolue face à toute menace système.

### 5.2 Ergonomie et efficacité de saisie

#### ENF04 — Ergonomie mesurée pour les opérations courantes

- **Catégorie :** utilisabilité. **Priorité proposée :** P1, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q23.

- **Description détaillée :** permettre aux employés formés de réaliser les tâches courantes avec des libellés compréhensibles, des champs utiles et une récupération claire des erreurs, dans les conditions d’affichage Desktop retenues.
- **Acteur :** utilisateurs représentatifs ; évaluateur de recette.
- **Conditions préalables :** scénarios A/B, niveau de formation, machine, résolution et méthode de mesure définis.
- **Comportement attendu :** ne demander à chaque étape que les champs nécessaires ; réutiliser les données selon ENF12 ; identifier les champs incorrects et préserver les autres saisies. Évaluer temps de réalisation, erreurs et aide nécessaire.
- **Règles :** moins de deux minutes, quinze champs et autocomplétion sont des propositions de [R], pas des seuils établis. Retenir des cibles après un essai pilote et les approuver avant recette. « Responsive » est remplacé par comportement vérifié dans les dimensions de fenêtre supportées ; aucun graphisme imposé.
- **Erreurs/exceptions :** saisie partielle, nom long, données nombreuses, fenêtre minimale supportée ; les actions essentielles restent accessibles.
- **CA-ENF04-1 :** sur les deux scénarios retenus, un utilisateur formé termine les tâches sans assistance non prévue ; temps et erreurs sont consignés puis comparés aux seuils approuvés.
- **CA-ENF04-2 :** une donnée invalide localise le champ et conserve les autres valeurs ; aucun contrôle essentiel n’est inaccessible dans les dimensions supportées.
- **RF-ENF04 :** annoncer un objectif de temps atteint sans protocole ; imposer des champs sans usage pour l’action courante.
- **Dépendances :** EF03, EF04, EF05, EF06, EF07, EF08, EF09, EF10, EF18, EF23, ENF06, ENF12.
- **Justification :** rendre l’ergonomie vérifiable sans transformer des préférences d’interface en obligations arbitraires.

#### ENF12 — Réutilisation des données et limitation de la double saisie

- **Catégorie :** efficacité et cohérence de saisie. **Priorité proposée :** P1, inchangée ; duplication avancée P2 optionnelle. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q02, Q03, Q17.

- **Description détaillée :** réutiliser clients, contacts et informations validées lors du passage demande/vente/livraison, tout en permettant de vérifier les données opérationnelles du dossier courant.
- **Acteur :** commercial et coordinateur.
- **Conditions préalables :** fiches existantes et liens EF05/07 définis.
- **Comportement attendu :** proposer les valeurs pertinentes, identifier leur provenance et permettre une adaptation autorisée ; ne pas demander de ressaisir les mêmes lignes de vente ou le même client pour créer sa livraison.
- **Règles :** adresse de siège non imposée comme lieu de chargement/déchargement ; changement de référence sans réécriture silencieuse du passé. Si duplication de mission retenue, elle crée un brouillon avec nouvelle référence, sans statuts réalisés, paiements, incidents ni réservation hérités. Cette duplication ne vaut pas planification récurrente.
- **Erreurs/exceptions :** client archivé, adresse obsolète, valeur inconnue, commande modifiée depuis préparation ; signaler et faire vérifier plutôt que recopier à l’aveugle.
- **CA-ENF12-1 :** une vente validée crée sa demande de livraison sans ressaisie du client et des articles utiles ; le lieu réel peut différer du siège sans modifier silencieusement la fiche d’origine.
- **CA-ENF12-2 :** si la duplication optionnelle est implémentée, le nouveau brouillon n’a ni règlement, ni réalisation, ni réservation ; tous les contrôles de confirmation sont réexécutés.
- **RF-ENF12 :** double saisie obligatoire des mêmes informations dans les deux dossiers liés ; copie d’un statut « terminée » comme nouvel état actif.
- **Dépendances :** EF03, EF05, EF06, EF07, EF10, EF18, ENF04, ENF07.
- **Justification :** conserver l’objectif de réduction de saisie sans imposer un raccourci risqué ou une adresse par défaut erronée.

### 5.3 Fiabilité et intégrité des opérations

#### ENF05 — Fiabilité de l’enregistrement et vérité des résultats de copie

- **Catégorie :** fiabilité de persistance. **Priorité proposée :** P0, inchangée. **Statut de révision :** divisée et clarifiée sous référence conservée.
- **Correspondance :** **ENF05a** reprend le besoin de fiabilité des enregistrements présent dans [S §7B] mais non couvert par l’ancienne ENF05 ; **ENF05b** conserve la vérification de résultat du backup de [R ENF05]. ENF09 garde l’organisation et la restauration. ENF05a est une précision ajoutée explicitement, pas une ancienne obligation prétendument déjà rédigée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q19.

- **Description détaillée :** ne déclarer un enregistrement métier réussi qu’après persistance cohérente de tous ses effets requis ; ne déclarer une copie de secours réussie qu’après les contrôles définis pour cette copie.
- **Acteur :** tout utilisateur qui enregistre ; administrateur pour la copie.
- **Conditions préalables :** effets attendus de chaque opération identifiés ; protocole de copie ENF09 défini.
- **Comportement attendu :** en cas d’échec, annuler les effets partiels incompatibles et informer ; si l’issue est inconnue après coupure, la signaler et vérifier l’état avant reprise. Pour le backup, vérifier présence, complétude/cohérence selon le mécanisme retenu et résultat d’exécution ; un checksum peut contrôler un transfert mais ne prouve pas seul la restaurabilité.
- **Règles :** aucun email obligatoire ; alerte d’échec consultable dans l’application et journal technique approprié. Les données saisies non encore persistées ne sont pas garanties contre un arrêt physique brutal, sauf mécanisme supplémentaire approuvé.
- **Erreurs/exceptions :** disque plein, droits insuffisants, erreur de données, perte de connexion après validation réelle ; pas de faux succès ni répétition aveugle.
- **CA-ENF05-1 :** un échec simulé pendant affectation ne laisse pas chauffeur réservé et véhicule libre ; un échec de paiement n’altère pas seulement le solde sans mouvement correspondant.
- **CA-ENF05-2 :** une opération persistée dont la réponse a été perdue est retrouvée avant reprise et n’est pas reproduite comme nouvelle opération.
- **CA-ENF05-3 :** copie vide ou exécution échouée donne un statut d’échec ; les contrôles de copie et le test de restauration ENF09 sont distinctement identifiés.
- **RF-ENF05 :** succès affiché malgré persistance échouée ; checksum seul présenté comme validation complète de la base restaurée.
- **Dépendances :** ENF06, ENF07, ENF08, ENF09, ENF13, EF05, EF07, EF10, EF18, EF20.
- **Justification :** résoudre le doublon de sauvegarde sans perdre le texte original et couvrir le risque de faux succès métier.

**Sous références :** ENF05a enregistrement métier est vérifiée par CA-ENF05-1 et CA-ENF05-2 ; ENF05b résultat de copie est vérifiée par CA-ENF05-3, avec restauration sous ENF09. Les statuts et garanties de la fiche parent s’appliquent aux deux.

#### ENF06 — Gestion explicite des erreurs et reprise sûre

- **Catégorie :** robustesse. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q19.

- **Description détaillée :** expliquer les erreurs de saisie, stockage et connexion utiles à l’utilisateur ; conserver autant que possible le travail non enregistré et permettre une reprise sans doublon ni fuite technique.
- **Acteur :** tout utilisateur ; personne chargée du diagnostic.
- **Conditions préalables :** sources de données et points de panne identifiés ; actions de reprise définies.
- **Comportement attendu :** distinguer échec certain, réussite vérifiée et issue incertaine ; fournir message compréhensible et référence de diagnostic ; conserver les traces techniques nécessaires sans mot de passe ni données excessives. L’existence d’un accès internet n’est pas supposée.
- **Règles :** retentative automatique d’une écriture seulement si l’absence de duplication est garantie ou l’état vérifié ; aucun délai « cinq secondes » imposé. Ne pas masquer un échec sous une liste vide ; pas de synchronisation hors connexion ajoutée par défaut.
- **Erreurs/exceptions :** connexion base interrompue, fichier inaccessible, service local arrêté, panne réseau uniquement si applicable ; action adaptée au mode retenu.
- **CA-ENF06-1 :** une coupure simulée avant enregistrement affiche un échec sans stacktrace utilisateur ; la saisie reste disponible tant que le processus fonctionne et que la sécurité le permet.
- **CA-ENF06-2 :** une coupure après écriture mais avant réponse entraîne vérification ou état incertain ; la reprise n’ajoute pas un second règlement.
- **CA-ENF06-3 :** une recherche en panne est distinguée d’une recherche sans résultat ; les journaux techniques permettent de relier l’erreur au message sans exposer les secrets.
- **RF-ENF06 :** crash sur une erreur récupérable de connexion ; réessai illimité d’une écriture sans contrôle.
- **Dépendances :** ENF01, ENF05, ENF08, ENF13 ; toutes les écritures et consultations.
- **Justification :** remplacer le scénario Web/internet par une gestion des pannes conforme à l’environnement réel.

#### ENF07 — Validation, unités et cohérence des références

- **Catégorie :** intégrité. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q07, Q09, Q13, Q17.

- **Description détaillée :** contrôler types, bornes, unités, liens et règles métier au moment de l’action, indépendamment de l’interface, tout en distinguant inconnu, zéro et correction.
- **Acteur :** tous les rédacteurs de données ; contrôles système.
- **Conditions préalables :** dictionnaire des champs, unités et règles approuvé.
- **Comportement attendu :** refuser une confirmation incohérente avec message ciblé ; préserver les brouillons licites. Recontrôler les références et contraintes lors des mises à jour et opérations concurrentes.
- **Règles :** téléphone stocké/traité comme texte de contact, conservant « + », zéros initiaux et séparateurs acceptés ; montant ordinaire positif selon action, montant zéro explicitement décidé, ajustement signé typé et autorisé ; calcul monétaire exact à la précision retenue. Dates-heures et capacités suivent EF06/09/11/16. Pas de référence orpheline ni interentreprise.
- **Erreurs/exceptions :** nombre hors plage, séparateur décimal, texte trop long, capacité modifiée, référence archivée ; contrôle contextualisé et pas de troncature silencieuse.
- **CA-ENF07-1 :** un téléphone de test « +212 06 00 00 00 00 » est conservé comme contact textuel sans conversion en entier ; les formats acceptés sont documentés.
- **CA-ENF07-2 :** un règlement ordinaire négatif est refusé ; un ajustement autorisé suit son type, son motif et sa règle de signe, sans contourner les droits.
- **CA-ENF07-3 :** charge supérieure à capacité retenue, date incohérente et référence d’une autre entreprise empêchent la confirmation ; aucune écriture partielle ne subsiste.
- **RF-ENF07 :** arrondi financier incohérent entre fiche et rapport ; inconnus convertis en zéro.
- **Dépendances :** EF03, EF04, EF06, EF09, EF11, EF16, EF18, EF19, EF20, EF21, ENF05, ENF13.
- **Justification :** corriger téléphone numérique, interdiction générale de négatifs et validation réduite aux écrans.

#### ENF13 — Cohérence en présence de modifications simultanées

- **Catégorie :** intégrité concurrente. **Priorité proposée :** P0 si les écritures concurrentes sont possibles ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q08, Q14.

- **Description détaillée :** prévenir écrasement silencieux d’un dossier, double engagement de ressource et duplication de règlement lorsque plusieurs utilisateurs ou opérations modifient le même état.
- **Acteur :** utilisateurs concernés ; système lors de la validation.
- **Conditions préalables :** mode de partage et possibilités de simultanéité identifiés ; données de référence et règles communes disponibles.
- **Comportement attendu :** détecter une version devenue périmée ou recontrôler l’état courant avant écriture ; informer l’utilisateur et préserver sa saisie pour comparaison lorsque possible ; garantir les contraintes partagées même si deux dossiers différents visent la même ressource.
- **Règles :** choix de verrouillage, versionnement ou autre mécanisme laissé à l’architecture. Détecter seulement deux éditions d’une même fiche ne suffit pas pour deux missions concurrentes utilisant le même véhicule. Dans un prototype strictement mono-écrivain, documenter et faire respecter cette limite ; ne pas revendiquer un usage multiposte complet sans le tester.
- **Erreurs/exceptions :** deux paiements sur le même solde, changement de prix pendant confirmation, deux affectations sur missions différentes ; une opération incompatible doit échouer proprement et être réexaminée.
- **CA-ENF13-1 :** deux lectures d’un dossier, première modification enregistrée, seconde tentative basée sur l’ancienne version : aucune première modification n’est écrasée silencieusement.
- **CA-ENF13-2 :** deux missions distinctes confirment simultanément le même véhicule sur période commune : au plus une réservation aboutit.
- **CA-ENF13-3 :** une confirmation de paiement répétée/concurrente ne compte qu’une fois le même mouvement et ne crée pas de trop-perçu masqué.
- **RF-ENF13 :** simple alerte affichée après que l’écrasement a déjà eu lieu ; limitation mono-écrivain annoncée mais non appliquée.
- **Dépendances :** EF02, EF09, EF10, EF11, EF18, EF20, ENF05, ENF06, ENF07, ENF08.
- **Justification :** protéger les invariants P0 sans présumer d’une architecture distribuée.

### 5.4 Traçabilité des opérations

#### ENF08 — Audit des opérations critiques et corrections

- **Catégorie :** traçabilité et protection de l’historique. **Priorité proposée :** P0 pour le noyau critique ; ancienne P1. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q11, Q20.

- **Description détaillée :** conserver une trace des opérations qui changent droits, montants, paiements, affectations, états et conditions opérationnelles importantes ; servir l’historique EF15 sans journaliser toute consultation par défaut.
- **Acteur :** système ; lecteur d’audit autorisé.
- **Conditions préalables :** catalogue d’événements, visibilité et conservation approuvés.
- **Comportement attendu :** enregistrer identifiant stable de l’auteur, dossier et entreprise, type, date-heure de saisie, valeurs utiles avant/après et motif lorsque requis. Protéger contre modification par les fonctions ordinaires ; tracer les actions d’administration pertinentes.
- **Règles :** aucun mot de passe ni secret ; collecte proportionnée ; une correction ajoute une trace. Les durées de conservation, accès techniques et procédure d’effacement autorisée restent à décider. « Inaltérable » n’est pas une garantie absolue contre l’administrateur du système de stockage.
- **Erreurs/exceptions :** compte désactivé, opération en échec, échec de création de la trace critique : ne pas présenter comme complète une opération qui exige cette trace ; diagnostic conservé selon possibilités.
- **CA-ENF08-1 :** une modification de prix de 3 000 à 3 500 conserve ancien/nouveau montant, auteur, date et motif ; même contrôle pour rôle, affectation et paiement.
- **CA-ENF08-2 :** un utilisateur ordinaire ne peut modifier ou supprimer une trace ; un lecteur de mission ne contourne pas ses restrictions financières via l’audit.
- **CA-ENF08-3 :** les journaux de test ne contiennent aucun secret ; la désactivation d’un compte ne détruit pas l’attribution historique.
- **RF-ENF08 :** changement critique sans trace ; ancien contenu financier exposé à un rôle non financier.
- **Dépendances :** EF02, EF15, EF18, EF19, EF20, EF21, ENF02, ENF03, ENF05, ENF09.
- **Justification :** la traçabilité minimale est un prérequis des corrections fiables ; la journalisation exhaustive demeure hors nécessité V1.

### 5.5 Continuité et récupération

#### ENF09 — Copie de secours et restauration vérifiée

- **Catégorie :** continuité technique. **Priorité proposée :** P0, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q19, Q20, Q24.

- **Description détaillée :** disposer d’une procédure documentée de copie cohérente et de restauration des données nécessaires au fonctionnement, compatible avec l’environnement Desktop et le mode de partage retenu.
- **Acteur :** administrateur ou responsable de sauvegarde désigné.
- **Conditions préalables :** données à inclure, emplacement autorisé, protection, responsable, fréquence et durée de conservation décidés ; perte admissible de données et délai de reprise définis.
- **Comportement attendu :** exécuter les copies selon la politique, rendre dernière réussite et échec consultables, conserver au moins une copie récupérable hors du seul support principal selon la solution approuvée ; restaurer sur une destination contrôlée et vérifier les données métier.
- **Règles :** les objectifs de perte admissible (RPO) et délai de reprise (RTO) sont à valider. Quotidien et moins de deux heures restent des candidats de [R], non des résultats établis. Pas d’horaire 02 h imposé sur un poste susceptible d’être éteint ; définir rattrapage d’une copie manquée. Automatisation seulement selon mécanisme exécutable retenu ; test manuel de récupération indispensable au prototype. Une restauration n’écrase pas une production sans précaution approuvée.
- **Erreurs/exceptions :** copie absente/corrompue, support indisponible, manque d’espace, restauration incomplète ; échec visible et procédure de reprise documentée, sans prétendre reconstruire des données jamais copiées.
- **CA-ENF09-1 :** un jeu contenant demandes A/B, affectations, événements et paiements est copié puis restauré sur environnement séparé ; nombres, liens, montants et historique sont cohérents.
- **CA-ENF09-2 :** copie manquée ou corrompue est signalée ; la procédure de rattrapage ou utilisation d’une copie antérieure est exécutée lors du test.
- **CA-ENF09-3 :** perte de données possible et durée mesurée de restauration sont consignées et comparées aux objectifs approuvés ; accès à la copie limité aux responsables autorisés.
- **RF-ENF09 :** simple existence du fichier présentée comme restauration éprouvée ; seule copie sur le disque dont on prétend couvrir la panne.
- **Dépendances :** ENF03, ENF05b, ENF08, ENF10 ; tous les domaines persistés.
- **Justification :** rendre la continuité concrète et distinguer validation d’une copie et preuve de restauration.

#### ENF11 — Continuité métier en cas d’absence

- **Catégorie :** continuité organisationnelle ; composante fonctionnelle rattachée à EF02.
- **Priorité proposée :** P1, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q04, Q18.

- **Description détaillée :** permettre à un employé habilité de poursuivre un dossier de l’entreprise même si son créateur est absent ou désactivé, sans partager un mot de passe ni perdre l’attribution historique.
- **Acteur :** administrateur pour les droits ; remplaçant habilité pour le dossier.
- **Conditions préalables :** dossiers partagés selon matrice et permissions de remplacement définies.
- **Comportement attendu :** attribuer au remplaçant les droits nécessaires via EF02 ; laisser accéder aux dossiers autorisés de l’entreprise indépendamment de leur créateur ; conserver ce dernier dans l’historique.
- **Règles :** aucune propriété exclusive par créateur sauf décision métier justifiée. Révocation des droits temporaires sous responsabilité de l’administrateur en V1 ; portefeuille, délégation automatique et échéance programmée ne sont pas obligatoires.
- **Erreurs/exceptions :** absence du seul administrateur, remplaçant sans compte, droits trop larges ; procédure de récupération/administration à documenter, sans compte partagé caché.
- **CA-ENF11-1 :** après désactivation du créateur, un remplaçant avec droits approuvés poursuit le dossier ; les anciens événements gardent l’auteur d’origine et les nouveaux le remplaçant.
- **CA-ENF11-2 :** retirer les droits du remplaçant empêche les actions suivantes sans effacer ses opérations passées.
- **RF-ENF11 :** compte partagé nécessaire pour retrouver une mission ; attribution globale de tous les droits pour un simple remplacement.
- **Dépendances :** EF01, EF02, EF15, ENF02, ENF08, ENF09.
- **Justification :** répondre à la dépendance à une personne sans ajouter un module complet de délégation.

### 5.6 Maintenabilité

#### ENF10 — Organisation du logiciel et maintenabilité vérifiable

- **Catégorie :** maintenabilité. **Priorité proposée :** P1, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05.

- **Description détaillée :** organiser le logiciel Java pour distinguer présentation, règles métier et accès aux données, documenter les responsabilités et rendre les règles critiques vérifiables, sans imposer un patron d’architecture définitif.
- **Acteur :** équipe de développement, architecture et maintenance.
- **Conditions préalables :** architecture décidée et justifiée par son responsable ; environnement de construction documenté.
- **Comportement attendu :** localiser les règles de planning, états et finance dans des responsabilités identifiées ; éviter leurs réimplémentations divergentes dans plusieurs écrans ; fournir procédures d’installation, construction et limites connues.
- **Règles :** MVC, couches ou autre organisation sont des options à examiner. Pas de séparation frontend/backend obligatoire ni de garantie d’aucun impact. Une modification locale doit avoir un impact explicable, limité et vérifié.
- **Erreurs/exceptions :** changement transversal légitime : documenter les modules concernés et tester les effets, plutôt que prétendre qu’il ne doit toucher qu’un fichier.
- **CA-ENF10-1 :** une revue retrouve un point de définition de la règle de solde et de la règle de chevauchement, utilisés par leurs consommateurs.
- **CA-ENF10-2 :** un membre suit les instructions pour construire et lancer la version de recette ; une modification témoin d’un champ client ne modifie pas les règles de calcul financier sans raison documentée, et les scénarios concernés restent valides.
- **RF-ENF10 :** règles de même nom contradictoires dans plusieurs écrans ; documentation ne correspondant pas à la version livrée.
- **Dépendances :** EF11, EF13, EF20, ENF05, ENF07, ENF09, ENF13.
- **Justification :** évaluer les responsabilités et l’évolution, sans confisquer le choix de conception.

### 5.7 Capacité et performance

#### ENF14 — Évolution de capacité et performance sur charge définie

- **Catégorie :** capacité/performance future. **Priorité proposée :** P2, inchangée. **Statut de révision :** modifiée et consolidée ; référence conservée.
- **Statut de validation :** À valider. Cadrage CAD applicable ; règles détaillées et critères proposés, sans approbation ni résultat de test présumé. Décisions liées : Q05, Q23.

- **Description détaillée :** préparer l’adoption par plusieurs entreprises sans présupposer une plateforme SaaS mutualisée. Évaluer les performances seulement pour un volume, un matériel et une concurrence explicitement définis.
- **Acteur :** équipe architecture et recette ; futur exploitant si évolution approuvée.
- **Conditions préalables :** choix d’extension décidé ; profil de charge et actions mesurées approuvés.
- **Comportement attendu :** documenter limites connues et paramètres de déploiement ; mesurer ouverture de planning, recherche, enregistrement et calcul de solde sur le profil retenu ; séparer temps de génération d’un rapport et temps des actions courantes.
- **Règles :** pas de réponse sous deux secondes « quel que soit le nombre d’entreprises ». Les dix minutes de provisionnement et cinquième entreprise de [R] sont des exemples non justifiés, retirés de la recette proposée. L’isolation reste immédiatement obligatoire via ENF03 ; l’hébergement partagé et le provisionnement automatisé sont futurs.
- **Erreurs/exceptions :** profil dépassé, stockage saturé, forte charge : ne pas corrompre les données ; ENF05/06 continuent de s’appliquer même si le délai dépasse la cible.
- **CA-ENF14-1 :** avant mesure, le protocole indique machine, volumes clients/missions/événements/paiements, nombre d’écrivains, opérations, répétitions, métrique de durée et seuils approuvés ; un rapport rend les résultats reproductibles.
- **CA-ENF14-2 :** sur le profil approuvé, les actions respectent leurs seuils ou l’écart est déclaré ; aucune conclusion de capacité illimitée n’est tirée.
- **RF-ENF14 :** proclamer la performance sans volume et environnement ; retarder l’isolation P0 sous prétexte qu’ENF14 est P2.
- **Dépendances :** ENF03, ENF05, ENF06, ENF10, ENF13, EF08, EF20, EF23, EF24.
- **Justification :** retirer l’exigence irréaliste de montée en charge illimitée et maintenir une obligation de mesure pertinente.

**Précision sur la performance V1 :** même si ENF14 future est P2, l’équipe doit observer les durées des parcours P0 lors de la recette. Si une lenteur empêche leur exécution pratique, elle devient un défaut bloquant du parcours, et non une amélioration de scalabilité à reporter. Aucun seuil chiffré n’est présenté comme validé avant ce protocole.

La performance des parcours V1 essentiels doit être observée pendant la recette. Une lenteur empêchant leur usage pratique constitue un défaut du parcours concerné ; elle ne peut être reportée au seul motif qu’ENF14 est P2. Aucun seuil chiffré n’est validé sans le protocole Q23.

## 6 Matrice de traçabilité

### 6.1 Objectifs et problèmes de référence

O-A centraliser ; O-B vérifier les ressources ; O-C partager une vue commune ; O-D enregistrer heures et attente ; O-E réduire saisies et appels ; O-F suivre montants ; O-G séparer les données et les droits [V §2.3]. PB1 retards ; PB2 disponibilités ; PB3 attente au déchargement ; PB4 dépendance à une personne ; PB5 charge de saisie ; PB6 paiements et soldes [V §4 ; S §2]. PB-T désigne un risque transversal identifié par l’audit, sans prétendre à un constat terrain supplémentaire.

### 6.2 Sources objectifs et critères

Chaque ligne conserve l’identifiant d’origine [R même identifiant], réécrit dans [A §6 même identifiant]. La colonne Sources précise les appuis Vision et Scope. Tous les critères identifiés dans la fiche correspondante font partie de la couverture proposée, y compris lorsqu’ils sont conditionnels.

| Référence | Sources complémentaires | Objectifs et problème | Critères de la fiche |
|---|---|---|---|
| EF01 | V §3 et §8 ; S §4 | O-C/O-G ; PB4 Information dépendant d’une personne | CA-EF01-1, CA-EF01-2, CA-EF01-3 |
| EF02 | V §3 et §8 ; S §4 | O-C/O-G ; PB4/PB5 Cumul de fonctions | CA-EF02-1, CA-EF02-2, CA-EF02-3 |
| EF03 | V §6.1 ; S §5A | O-A/O-E ; PB5 Recopie et contacts dispersés | CA-EF03-1, CA-EF03-2, CA-EF03-3 |
| EF04 | V §6.1 ; S §5A | O-A/O-B ; PB2 Ressources mal identifiées | CA-EF04-1, CA-EF04-2, CA-EF04-3 |
| EF05 | V §5 ; S §3 et §5A | O-A/O-E ; PB2/PB5 Livraison et transport externe confondus | CA-EF05-1, CA-EF05-2, CA-EF05-3 |
| EF06 | V §5 ; S §3 et §5A | O-B ; PB2 Charge ou horaires incertains | CA-EF06-1, CA-EF06-2, CA-EF06-3 |
| EF07 | V §5 ; S §3 et §5A | O-A/O-E ; PB5 Vente/livraison en double | CA-EF07-1, CA-EF07-2, CA-EF07-3 |
| EF08 | V §6.1 et BR-01 à BR-03 ; S §5A et R4 à R6 | O-B/O-C ; PB2 Disponibilité non visible | CA-EF08-1, CA-EF08-2, CA-EF08-3 |
| EF09 | V §6.1 et BR-01 à BR-03 ; S §5A et R4 à R6 | O-B ; PB2 Ressource supposée libre | CA-EF09-1, CA-EF09-2, CA-EF09-3 |
| EF10 | V §6.1 et BR-01 à BR-03 ; S §5A et R4 à R6 | O-B ; PB2 Engagement incohérent | CA-EF10-1, CA-EF10-2, CA-EF10-3 |
| EF11 | V §6.1 et BR-01 à BR-03 ; S §5A et R4 à R6 | O-B/O-C ; PB1/PB2 Retard propagé | CA-EF11-1, CA-EF11-2, CA-EF11-3 |
| EF12 | V §6.1 et BR-01 à BR-03 ; S §5A et R4 à R6 | O-B ; PB2 Panne ou absence inconnue | CA-EF12-1, CA-EF12-2, CA-EF12-3 |
| EF13 | V §5.2 ; S §5B et R7 à R8 | O-C ; PB1/PB4 État difficile à retrouver | CA-EF13-1, CA-EF13-2, CA-EF13-3 |
| EF14 | V §5.2 ; S §5B et R7 à R8 | O-C ; PB1 Communication tardive | CA-EF14-1, CA-EF14-2, CA-EF14-3 |
| EF15 | V §5.2 ; S §5B et R7 à R8 | O-C/O-D ; PB4 Information non vérifiable | CA-EF15-1, CA-EF15-2, CA-EF15-3 |
| EF16 | V §6.2 ; S §5C et R9 | O-D/O-B ; PB3 Attente bloquant la suite | CA-EF16-1, CA-EF16-2, CA-EF16-3 |
| EF17 | V §5.2 ; S §5B et R7 à R8 | O-C/O-E ; PB4 Appels pour connaître l’état | CA-EF17-1, CA-EF17-2 |
| EF18 | V §6.3 ; S §5D et R10 à R12 | O-F ; PB6 Montants et acomptes confondus | CA-EF18-1, CA-EF18-2, CA-EF18-3 |
| EF19 | V §6.3 ; S §5D et R10 à R12 | O-F ; PB6 Règlements non justifiables | CA-EF19-1, CA-EF19-2, CA-EF19-3 |
| EF20 | V §6.3 ; S §5D et R10 à R12 | O-F ; PB6 Solde peu fiable | CA-EF20-1, CA-EF20-2, CA-EF20-3, CA-EF20-4 |
| EF21 | V §6.3 ; S §5D et R10 à R12 | O-F ; PB6 Dépenses oubliées | CA-EF21-1, CA-EF21-2, CA-EF21-3 |
| EF22 | V §6.4 et §9 ; S §5E | O-C/O-F ; PB1/PB4/PB6 Suivi dispersé | CA-EF22-1, CA-EF22-2, CA-EF22-3 |
| EF23 | V §6.4 et §9 ; S §5E | O-E ; PB4/PB5 Recherche lente/manuelle | CA-EF23-1, CA-EF23-2, CA-EF23-3 |
| EF24 | V §6.4 et §9 ; S §5E | O-C/O-D/O-F ; PB1/PB3/PB6 Analyse peu reproductible | CA-EF24-1, CA-EF24-2, CA-EF24-3 |
| ENF01 | V §3 et §8 ; S §4 | O-G ; PB-T Accès par identité compromise | CA-ENF01-1, CA-ENF01-2, CA-ENF01-3 |
| ENF02 | V §3 et §8 ; S §4 | O-G ; PB-T Contournement de permissions | CA-ENF02-1, CA-ENF02-2 |
| ENF03 | V §3 et §8 ; S §4 | O-G ; PB-T Fuite interentreprises | CA-ENF03-1, CA-ENF03-2, CA-ENF03-3 |
| ENF04 | V §3 et §6.1 ; S §7A | O-E ; PB5 Charge de saisie | CA-ENF04-1, CA-ENF04-2 |
| ENF05 | S §6 R12 et §7B ; V §7 | O-A/O-F ; PB-T Faux succès ou effet partiel | CA-ENF05-1, CA-ENF05-2, CA-ENF05-3 |
| ENF06 | S §6 R12 et §7B ; V §7 | O-A/O-F ; PB-T Panne et opération répétée | CA-ENF06-1, CA-ENF06-2, CA-ENF06-3 |
| ENF07 | S §6 R12 et §7B ; V §7 | O-A/O-B/O-F ; PB-T Données incohérentes | CA-ENF07-1, CA-ENF07-2, CA-ENF07-3 |
| ENF08 | V §3, §5.2 et §15 ; S §7B à §7D | O-C/O-F/O-G ; PB4/PB6 Correction non attribuée | CA-ENF08-1, CA-ENF08-2, CA-ENF08-3 |
| ENF09 | V §3, §5.2 et §15 ; S §7B à §7D | O-A/O-C/O-F ; PB-T Perte des dossiers | CA-ENF09-1, CA-ENF09-2, CA-ENF09-3 |
| ENF10 | V §3, §5.2 et §15 ; S §7B à §7D | O-A/O-B/O-F ; PB-T Évolutions divergentes du code | CA-ENF10-1, CA-ENF10-2 |
| ENF11 | V §3, §5.2 et §15 ; S §7B à §7D | O-C/O-G ; PB4 Créateur absent | CA-ENF11-1, CA-ENF11-2 |
| ENF12 | V §3 et §6.1 ; S §7A | O-E ; PB5 Double saisie | CA-ENF12-1, CA-ENF12-2 |
| ENF13 | S §6 R12 et §7B ; V §7 | O-B/O-F ; PB-T Écritures simultanées incompatibles | CA-ENF13-1, CA-ENF13-2, CA-ENF13-3 |
| ENF14 | V §8 et §15 ; S §8 | O-G et continuité technique de la solution ; PB-T Extension future non maîtrisée | CA-ENF14-1, CA-ENF14-2 |

### 6.3 Traitement de chaque référence originale

Aucune référence principale n’est supprimée ni fusionnée. Cette table distingue reformulation, redistribution, division et retrait proposé d’un détail. Un retrait proposé n’est pas une décision métier acquise. Les justifications complètes figurent dans les fiches.

| Référence | Traitement et justification | Points restant à valider |
|---|---|---|
| EF01 | Réécriture conservée : conserver la fonction essentielle et retirer l’hypothèse de navigation Web et le délai arbitraire non justifié. | Q04, Q18 |
| EF02 | Réécriture conservée : respecter les petites équipes et supprimer l’assimilation d’un rôle à une personne ou à un compte chauffeur validé. | Q04, Q18, Q20 |
| EF03 | Réécriture conservée : éviter la rigidité administrative et la corruption rétroactive des opérations. | Q17, Q20 |
| EF04 | Réécriture conservée : séparer les objets, conserver les unités et déplacer les contrôles d’éligibilité vers l’affectation. | Q07, Q09, Q17 |
| EF05 | Réécriture conservée : compléter le cycle et éviter la confusion demande/engagement et les trajets dupliqués. | Q02, Q03, Q06, Q15 |
| EF06 | Réécriture conservée : rendre les calculs fondés et définir le minimum nécessaire à chaque étape. | Q07, Q09, Q12, Q13 |
| EF07 | Réécriture conservée : indispensable à un parcours A réel ; préserver Basic Business Management sans construire un ERP. | Q02, Q03, Q06, Q13, Q15 |
| EF08 | Réécriture conservée : supprimer la duplication des transitions tout en conservant la vue de travail essentielle. | Q06, Q10, Q21 |
| EF09 | Réécriture conservée : couvrir le temps réellement immobilisé et séparer conseil de disponibilité et engagement. | Q07, Q08, Q09 |
| EF10 | Réécriture conservée : faire d’EF10 le point unique d’engagement, sans imposer l’architecture ni un livrable d’impression. | Q03, Q04, Q05, Q06, Q08, Q10 |
| EF11 | Réécriture conservée : éliminer les variantes de règle et rendre explicite l’impact des aléas réels. | Q05, Q07, Q08 |
| EF12 | Réécriture conservée : une vérification P0 n’est fiable que si ses entrées d’indisponibilité sont disponibles en V1. | Q07, Q08, Q09 |
| EF13 | Réécriture conservée : remplacer deux listes incompatibles par une proposition unique et vérifiable. | Q06, Q10, Q11, Q12 |
| EF14 | Réécriture conservée : le traitement des retards répond à un problème central et conditionne la fiabilité du planning ; il ne nécessite ni GPS ni prédiction. | Q07, Q08, Q21 |
| EF15 | Réécriture conservée : rendre les exigences de suivi et de correction testables, avec une seule capture transversale. | Q11, Q20 |
| EF16 | Réécriture conservée : traiter l’un des problèmes centraux des sources et séparer responsabilité, événements et hypothèse commerciale. | Q07, Q10, Q11, Q12 |
| EF17 | Réécriture conservée : distinguer consultation détaillée, synthèse et observation physique. | Q21, Q22 |
| EF18 | Réécriture conservée : lever les ambiguïtés ayant un effet direct sur les soldes et respecter la gestion commerciale simple. | Q04, Q13, Q14, Q15 |
| EF19 | Réécriture conservée : les données de preuve minimales sont nécessaires au cycle P0 des paiements ; éviter la fausse équivalence référence/encaissement. | Q14, Q24 |
| EF20 | Réécriture conservée : définir une règle reproductible couvrant corrections et remboursements sans construire une comptabilité générale. | Q13, Q14, Q15, Q16 |
| EF21 | Réécriture conservée : conserver l’utilité financière sans prétention comptable et corriger le refus injustifié des frais d’annulation. | Q13, Q15, Q24 |
| EF22 | Réécriture conservée : utile mais non indispensable si les listes sources P0 rendent le parcours complet utilisable. | Q16, Q21, Q22 |
| EF23 | Réécriture conservée : remplacer un refus incompréhensible par un contrat de recherche testable. | Q07, Q21, Q22 |
| EF24 | Réécriture conservée : préserver les rapports tout en reportant un coût secondaire et en explicitant les incohérences des sources sur les exports. | Q16, Q22, Q23 |
| ENF01 | Réécriture conservée : remplacer une sécurité Web présupposée par des propriétés vérifiables et distinguer hachage et chiffrement. | Q05, Q18 |
| ENF02 | Réécriture conservée : conserver l’objectif RBAC sans imposer serveur/API ni faux compte terrain. | Q04, Q05 |
| ENF03 | Réécriture conservée : distinguer confidentialité actuelle et architecture multi-tenant future, sans promesse d’impossibilité absolue face à toute menace système. | Q05, Q20 |
| ENF04 | Réécriture conservée : rendre l’ergonomie vérifiable sans transformer des préférences d’interface en obligations arbitraires. | Q23 |
| ENF05 | Réécriture conservée : résoudre le doublon de sauvegarde sans perdre le texte original et couvrir le risque de faux succès métier. | Q05, Q19 |
| ENF06 | Réécriture conservée : remplacer le scénario Web/internet par une gestion des pannes conforme à l’environnement réel. | Q05, Q19 |
| ENF07 | Réécriture conservée : corriger téléphone numérique, interdiction générale de négatifs et validation réduite aux écrans. | Q07, Q09, Q13, Q17 |
| ENF08 | Réécriture conservée : la traçabilité minimale est un prérequis des corrections fiables ; la journalisation exhaustive demeure hors nécessité V1. | Q04, Q11, Q20 |
| ENF09 | Réécriture conservée : rendre la continuité concrète et distinguer validation d’une copie et preuve de restauration. | Q05, Q19, Q20, Q24 |
| ENF10 | Réécriture conservée : évaluer les responsabilités et l’évolution, sans confisquer le choix de conception. | Q05 |
| ENF11 | Réécriture conservée : répondre à la dépendance à une personne sans ajouter un module complet de délégation. | Q04, Q18 |
| ENF12 | Réécriture conservée : conserver l’objectif de réduction de saisie sans imposer un raccourci risqué ou une adresse par défaut erronée. | Q02, Q03, Q17 |
| ENF13 | Réécriture conservée : protéger les invariants P0 sans présumer d’une architecture distribuée. | Q05, Q08, Q14 |
| ENF14 | Réécriture conservée : retirer l’exigence irréaliste de montée en charge illimitée et maintenir une obligation de mesure pertinente. | Q05, Q23 |

### 6.4 Divisions redistributions et détails non retenus en l’état

| Référence ancienne | Référence proposée | Traitement |
|---|---|---|
| EF01–EF03, EF05–EF24 | Identifiants inchangés | Réécriture ; aucune suppression |
| EF04 | EF04a et EF04b, sous EF04 | Division véhicule/chauffeur ; une seule référence de traçabilité conservée |
| EF08, EF13 | EF08 consultation ; EF13 cycle | Redistribution de responsabilités, pas suppression de capacité |
| EF17, EF22 | EF17 liste ; EF22 synthèse | Déduplication, pas fusion silencieuse |
| ENF05 | ENF05a, ENF05b, lien ENF09 | Besoin d’enregistrement métier ajouté depuis le Scope ; contrôle de copie conservé ; stratégie/restauration ENF09 |
| ENF01–04, ENF06–14 | Identifiants inchangés | Garanties reformulées ; solutions prématurées retirées avec explication |
| Aucun nouvel EF numéroté | Scénarios intégrés aux EF existantes | Pas de module supplémentaire réputé validé ; idées nouvelles marquées REC ou HYP |

| Détail original | Traitement proposé et justification | Effet et suivi |
|---|---|---|
| EF01 durée 30 minutes ; ENF01 cinq essais | Valeurs candidates non justifiées par l’usage | Q18 ; seuils requis avant recette correspondante |
| EF02 et ENF02 rôle chauffeur | Écarté du cadrage V1 par CAD04 | Ressource chauffeur conservée dans EF04b ; saisie par employé |
| EF03 fiscal et coordonnées toujours obligatoires | Minimum contextualisé selon client et étape | Q17 ; pas de valeur fiscale fictive |
| EF06 tonnage déduit des seules quantités | Calcul conditionné à des unités et poids compatibles | Q09 ; total déclaré distingué du calcul |
| EF07 fractionnement implicite ; EF10 feuille de route | Cardinalité à décider ; impression non imposée faute de contenu défini | Q03 et Q22 ; liens et réservation conservés |
| EF13 cycle linéaire imposant attente | Transitions conditionnelles proposées ; arrêt en cours ouvert | Q10 et Q11 ; aucun état exceptionnel officialisé |
| EF14 cause ETA et couleur rouge imposées | Inconnus autorisés ; signalement visuel laissé à la conception | Q21 ; pas de donnée inventée |
| EF15 et ENF08 journal totalement inaltérable | Protection contre opérations ordinaires, corrections par ajout | Q20 ; pas de garantie contre tout accès système |
| EF17 temps réel et utilisation avancée | Dernière information datée ; indicateurs avancés reportables | Q21 et Q22 ; absence de GPS explicite |
| EF18 avoir automatique et EF20 en souffrance | Régularisations et échéance non définies restent ouvertes | Q15 et Q16 ; aucun remboursement automatique |
| EF21 marge nette et refus des frais de mission annulée | Total de frais déclarés, frais réels d’annulation conservés | Q15 ; aucun indicateur de rentabilité comptable |
| EF24 formats multiples et ENF12 duplication en un clic | Un format éventuel ; duplication optionnelle avec données remises à zéro | Q22 ; aucun export ou raccourci avancé réputé approuvé |
| ENF01 ENF02 ENF06 ENF10 vocabulaire Web | Garanties Desktop exprimées sans URL API ou séparation frontend backend obligatoire | CAD01 et CAD05 ; architecture à justifier en Q05 |
| ENF03 tenant_id imposé | Garantie de séparation conservée, mécanisme libre | Q05 ; ENF03 ne dépend pas du report d’ENF14 |
| ENF04 deux minutes quinze champs et responsive | Protocole Desktop et seuils à approuver, autocomplétion non obligatoire | Q23 ; aucune performance annoncée atteinte |
| ENF05 checksum seul et email obligatoire | Vérification de copie et restauration distinctes ; alerte interne | Q19 ; email externe hors V1 |
| ENF06 retentative automatique sans condition | Reprise après vérification pour éviter un doublon | Q05 ; pas de synchronisation hors connexion ajoutée |
| ENF07 téléphone numérique et interdiction de tout négatif | Téléphone textuel et ajustement financier signé typé | Q13 et Q17 ; règles de validation conservées |
| ENF09 copie à 02 heures et restauration sous deux heures | Horaire fréquence et objectifs candidats à valider avec rattrapage | Q19 ; copie et test de récupération conservés |
| ENF10 absence totale d’impact et ENF11 portefeuille délégué | Responsabilités vérifiables ; remplacement par droits, automatisation non exigée | Q04 et Q05 ; continuité métier conservée |
| ENF14 dix minutes et performance indépendante de charge | Extension future reportée, mesures sur profil défini | Q05 et Q23 ; aucune capacité illimitée promise |

## 7 Tableau des priorités avec justifications

### 7.1 Répartition proposée

P0 : minimum cohérent indispensable aux parcours V1 ; P1 : valeur opérationnelle importante ; P2 : secondaire ou reportable. Ce classement ne vaut ni accord de réalisation ni autorisation de retirer une dépendance essentielle. EF07 est P0 car le parcours A est maintenu par CAD02 ; ses limites restent à valider.

| Niveau | EF | ENF |
|---|---|---|
| P0 | EF01 à EF16, EF18 à EF20 | ENF01 à ENF03, ENF05 à ENF09, ENF13 si écritures concurrentes possibles |
| P1 | EF17, EF21, EF22, EF23 | ENF04, ENF10, ENF11, ENF12 |
| P2 | EF24 | ENF14 |

Comptage : 19 EF P0, 4 EF P1 et 1 EF P2 ; 9 ENF classées P0 dont ENF13 conditionnelle, 4 ENF P1 et 1 ENF P2. Les sous références ne sont pas comptées comme exigences principales supplémentaires. Les recherches élémentaires indispensables restent incluses dans EF03 et EF08 même si les filtres avancés d’EF23 sont P1. De même, les liens sans ressaisie nécessaires au parcours A restent dans EF07 même si ENF12 est P1.

### 7.2 Priorité de chaque référence

| Référence | Originale | Proposée | Justification |
|---|---|---|---|
| EF01 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF02 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF03 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF04 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF05 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF06 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF07 | P1 | P0 | Vente simple et liaison nécessaires au parcours A maintenu |
| EF08 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF09 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF10 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF11 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF12 | P1 | P0 | Indisponibilités indispensables au contrôle fiable des ressources |
| EF13 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF14 | P1 | P0 | Signalement de retard et effet sur les engagements au cœur du besoin |
| EF15 | P1 | P0 | Noyau de trace requis pour états et corrections |
| EF16 | P1 | P0 | Conditions et immobilisation nécessaires au parcours annoncé |
| EF17 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| EF18 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF19 | P1 | P0 | Métadonnées minimales requises pour confirmer les encaissements |
| EF20 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| EF21 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| EF22 | P0 | P1 | Synthèse complémentaire si planning et listes essentielles sont disponibles |
| EF23 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| EF24 | P1 | P2 | Rapport exporté secondaire ; contenu et format encore ouverts |
| ENF01 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF02 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF03 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF04 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| ENF05 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF06 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF07 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF08 | P1 | P0 | Corrections critiques de droits et montants exigent une trace |
| ENF09 | P0 | P0 | Accès données planification exécution ou intégrité indispensables aux parcours |
| ENF10 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| ENF11 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| ENF12 | P1 | P1 | Améliore l’exploitation et l’usage sans conditionner chaque action du noyau |
| ENF13 | P1 | P0 conditionnelle | Intégrité critique si simultanéité ; sinon limite mono écrivain documentée et effective |
| ENF14 | P2 | P2 | Extension future et mesures sur charge définie |

### 7.3 Dépendances et limites de report

Les garanties de sécurité, persistance, audit et cohérence s’intègrent aux opérations qu’elles protègent. Elles ne sont pas un lot final facultatif. Le report d’EF24 ne supprime pas les consultations ; celui d’ENF14 ne supprime pas l’isolation ENF03 ni l’observation des temps des parcours essentiels. La saisie des dépenses reste un domaine V1 annoncé : sa priorité P1 ordonne l’effort, sans l’exclure automatiquement du livrable universitaire. Toute réduction effective de périmètre requiert un arbitrage consigné.

## 8 Décisions et questions restant à valider

### 8.1 Décisions explicites retenues et éléments ouverts

CAD01 à CAD05 proviennent de la mission actuelle. Ils précisent le cadrage sans convertir les recommandations métier en approbations. Les exclusions de [S §8] et de la mission restent applicables. Les décisions détaillées n’ont pas été fournies ; toutes les questions ci dessous portent le statut À valider, sauf leur partie déjà résolue explicitement par le cadrage.

Pour chaque décision, le responsable de projet consigne réponse retenue, auteur de l’approbation, date, références et critères affectés. L’équipe désigne le responsable métier compétent avant validation ; aucun nom, délai ni accord n’est inventé. Une priorité P0 ne remplace pas cette approbation.

### 8.2 Registre des questions ouvertes

| Décision et statut | Question à trancher | Proposition non approuvée | Références et effet |
|---|---|---|---|
| Q01 — Bloquante — À valider | CAD01 à CAD05 et les parcours A et B sont fixés par la mission. Quels détails du périmètre, critères et délais l’équipe approuve-t-elle ? | Définir le minimum détaillé A et B conforme au cadrage puis estimer les P1 et P2 | Toutes ; empêche une fausse déclaration de périmètre validé |
| Q02 — Bloquante — À valider | La vente V1 contient-elle réellement des lignes produit ou seulement une référence externe ? | Lignes simples si le parcours A annoncé doit être réalisé ; si référence externe seulement, l’annoncer explicitement | EF05–07/18 ; modèle commercial |
| Q03 — Bloquante — À valider | Une demande/commande peut-elle avoir plusieurs missions ? Groupage, fractionnement, plusieurs véhicules ? | Au plus une mission active par demande et un couple de ressources par mission en V1 ; cas multiples non engagés avant arbitrage | EF05/07/10 ; cardinalités UML |
| Q04 — Bloquante — À valider | Qui saisit, confirme, annule, corrige et confirme un encaissement ? Qui remplace un absent ? | Matrice opérations/commercial/finance/admin ; cumul autorisé ; chauffeur sans compte | EF01/02, ENF02/11 |
| Q05 — Bloquante — À valider | Quel mode de partage : un poste, plusieurs postes, quel stockage, combien d’écrivains ? Une ou deux entreprises dans la démonstration ? | Décision d’architecture explicite, sans hypothèse Web ; ENF03 reste une garantie à vérifier | ENF03/05/06/09/13/14 |
| Q06 — Bloquante — À valider | À quel instant une demande est-elle acceptée et une mission réservée/confirmée ? | Enregistrement de demande ≠ engagement ; confirmation après validation EF09–11 | EF05/08/10/13 |
| Q07 — Bloquante — À valider | Quelles durées composent l’occupation et comment estimer transit/retour et fin inconnue ? | Inclure les phases nécessaires ; estimation manuelle ; aucun libre automatique sur une fin inconnue | EF06/09/11/12/16 |
| Q08 — Bloquante — À valider | Quelle convention de limites et quel traitement d’un conflit apparu après retard ? Exceptions autorisées ? | Intervalles [début, fin[ ; aucune double réservation confirmée ; conflit réel conservé et résolu humainement | EF10–12/14/16 |
| Q09 — Bloquante — À valider | Quelles capacités et qualifications sont pertinentes ; que faire d’une charge inconnue ? | Contrôles sur les dimensions utiles, pas de surcharge connue ; données nécessaires exigées avant confirmation | EF04/06/09, ENF07 |
| Q10 — Bloquante — À valider | Quels états et transitions ; attente facultative ; déchargement non applicable ; arrêt après départ ? | Cycle EF13 proposé ; arrêt exceptionnel à définir ou limite explicite du prototype | EF13/16 ; diagramme d’états |
| Q11 — Bloquante — À valider | Quelle procédure corrige un événement ou rouvre une mission close ? Peut-on enregistrer tard des étapes reçues ensemble ? | Ajout traçable, pas d’effacement ; pas d’obligation d’inventer une heure inconnue | EF13/15/16, ENF08 |
| Q12 — Bloquante — À valider | Qui organise le déchargement, avec quels moyens ; quelles données requises à confirmation et à clôture ? | Conditions convenues ; arrivée/début/fin si connus ; aucun service payant ni supplément automatique | EF06/13/16 |
| Q13 — Bloquante — À valider | Le prix est-il global ou ventilé vente/transport ? Quelle devise/précision ; zéro autorisé dans quels cas ? | Une dette unique avec composantes identifiées ; une devise V1 ; arrondi unique | EF07/18/20, ENF07 |
| Q14 — Bloquante — À valider | Quels modes, références et preuves permettent la confirmation d’encaissement ; qui la fait ? | Séparer annonce, enregistrement et confirmation ; règles contextualisées par mode | EF18–20 |
| Q15 — Bloquante — À valider | Comment traiter prix corrigé après paiement, annulation, remboursement et trop-perçu ? | Mouvements tracés et ajustements distincts ; refus du trop-perçu tant que non défini ; pas d’avoir automatique | EF18/20 ; usage financier opérationnel impossible à déclarer complet avant décision |
| Q16 — À valider | Faut-il une échéance de paiement et une notion d’impayé échu ? | Rester « solde restant » tant que date d’échéance et règle ne sont pas approuvées | EF20/22/24 ; éviter « en souffrance » ambigu |
| Q17 — À valider | Quels clients et identifiants administratifs ; qui peut archiver ou fusionner ? | Fiscal selon catégorie ; archivage des références utilisées ; fusion automatique exclue | EF03/04, ENF07 |
| Q18 — À valider | Quelle durée d’inactivité, politique d’essais et récupération d’accès ; cas du dernier administrateur ? | Fixer valeurs après examen de l’usage ; pas de compte partagé | EF01/02, ENF01/11 |
| Q19 — Bloquante pour recette — À valider | Qui sauvegarde, où, quand, combien de temps ; perte et délai de reprise admissibles ; poste éteint ? | Politique compatible avec exploitation et test de restauration sur environnement séparé | ENF05/09 |
| Q20 — À valider | Quelles données garder dans l’audit, quels lecteurs et quelle durée de conservation ? | Noyau critique, minimisation, pas de secrets ; durée à décider | EF15, ENF03/08/09 |
| Q21 — À valider | Quelle fréquence de mise à jour et quel seuil d’ancienneté utile ; qui contacte le client ? | Afficher les dates ; contact par employé ; seuils seulement s’ils sont justifiés | EF14/17/22 |
| Q22 — À valider | Quel rapport V1, quel format ; indicateurs et dénominateurs ; export vraiment demandé par le cours ? | Listes d’abord ; un seul format si retenu ; valeurs manquantes visibles | EF22/24 |
| Q23 — Bloquante pour objectifs chiffrés — À valider | Quelle machine, résolution, volume et simultanéité servent à mesurer ergonomie/performance ? | Jeu d’essai réaliste, pilote puis seuils signés ; aucune charge illimitée | ENF04/14 |
| Q24 — À valider | Une référence de justificatif suffit-elle ; les pièces jointes sont-elles nécessaires ? | Référence textuelle au minimum ; fichier joint seulement si besoin et coût acceptés | EF19/21, ENF09 |

Q02 ne remet pas en cause l’existence du parcours vente avec livraison : il précise le contenu commercial minimal, notamment lignes produits ou référence à une vente externe. Q03 reste un arbitrage de cardinalité. Q05 ne permet pas de substituer une architecture Web ou SaaS au cadrage Desktop. Q12 n’autorise ni service payant ni frais automatiques. Les propositions de régularisation Q15 ne deviennent pas une comptabilité générale ou un transfert bancaire.

### 8.3 Contradictions et écarts non résolus

| Écart entre sources | Traitement dans cette version | Effet restant |
|---|---|---|
| V §15 technique à confirmer contre R supposant URL API et serveur | Cadrage Desktop confirmé par la mission ; vocabulaire Web reformulé | Q05 fixe stockage partage et mécanismes ; aucune architecture finale choisie |
| R EF02 et ENF02 compte chauffeur contre S §4 compte non retenu | Résolu au niveau du cadrage : CAD04 exclut ce compte | Q04 définit quel employé saisit et quels droits il reçoit |
| V BR-08 paiements enregistrés contre S R10 encaissements confirmés | REC : seuls les encaissements confirmés réduisent le solde | Non résolu métier ; Q14 et Q15 à valider avant recette financière |
| V BR-01 exception de chevauchement possible contre S R5 et R EF11 blocage | REC : aucun nouvel engagement incompatible confirmé sans règle approuvée | Q08 fixe bornes, exceptions éventuelles et traitement des conflits réels |
| États différents V §5.2 S §5B R EF08 et EF13 | Cycle unique proposé sous EF13, attente facultative et déchargement explicite | Q10 et Q11 bloquent l’approbation du diagramme d’états ; arrêt en cours non décidé |
| V §6.4 et §9 rapports et exports futurs contre R EF24 plusieurs formats | EF24 conservée P2 ; un format initial seulement si retenu | Q22 décide rapport V1 et export ; aucune suppression ni activation implicite |
| R EF17 temps réel contre V §6.4 et S §5B saisies manuelles | Informations déclarées datées et ancienneté affichée | Q21 précise fréquence et responsabilités sans ajouter GPS |
| R EF21 marge nette et refus des frais annulés contre V §6.3 et S §5D à §5E | REC : frais réellement engagés conservés ; pas de marge nette annoncée | Validation des frais et corrections en Q15 et Q24 |
| R ENF05 email et checksum contre S §8 exclusions externes et besoin de récupération | Email hors V1 ; alerte interne, copie et restauration distinguées | Q19 fixe politique réellement exécutable et preuve de restauration |
| Adoption par plusieurs entreprises contre mode Desktop et partage non décidé | Séparation conservée ENF03 sans imposer de plateforme mutualisée | Q05 fixe démonstration et stockage ; essai monoentreprise seul ne prouve pas une isolation croisée |

### 8.4 Conditions avant approbation de la référence

Les cardinalités Q03, permissions Q04, partage Q05, engagement Q06, occupation et compatibilité Q07 à Q09, états et correction Q10 à Q12, finance Q13 à Q15 doivent recevoir une décision pour les scénarios concernés. La politique de récupération Q19 et le protocole de mesure Q23 sont nécessaires à une recette de qualité complète. Les autres points restent des limites explicites jusqu’à arbitrage ; ils ne peuvent être remplacés par des valeurs supposées.

Les règles proposées de la Vision BR-01 à BR-10 et du Scope R1 à R12 se retrouvent dans EF02, EF05 à EF16, EF18 à EF20 et ENF02 à ENF08. Leur statut source À valider est maintenu. Les éléments utiles aux UML sont le glossaire, les acteurs, les préconditions, liens et transitions ; les tests reprennent les CA identifiés et les refus particuliers avec les règles RC. L’équipe de conception reste responsable du modèle technique.

Le présent document conserve les 24 EF et 14 ENF, y compris les sous références explicitement divisées, et ne supprime aucune référence principale. Les propositions de report et de retrait de détails sont justifiées en section 6. L’approbation détaillée et les résultats de tests d’une application restent à produire par l’équipe.
