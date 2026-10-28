# Cahier des charges 

Le TMS organise le travail d’une petite entreprise depuis la réception d’une demande jusqu’au suivi de la mission et des sommes restant à recevoir. Le transport constitue le cœur de l’application. Une gestion commerciale simple permet de relier une vente à sa livraison.

Ce cahier décrit les besoins métier, les parcours, les informations à conserver et les limites du produit. **Requirements.md** précise les comportements, les permissions, les contrôles et les critères d’acceptation sous les références **EF01 à EF24** et **ENF01 à ENF14**. Les deux documents utilisent les mêmes termes et le même périmètre.

Les options recensées sous **Q01 à Q24** restent des décisions à consigner. Une présentation prête pour le développement ne vaut pas approbation implicite de ces options. Les règles concernées sont appliquées après leur validation ; les points ouverts ne doivent pas être remplacés par des choix supposés.

## Sommaire

1. Contexte et problème à résoudre
2. Objectifs et résultats attendus
3. Périmètre de la première version
4. Utilisateurs et accès
5. Vocabulaire et informations métier
6. Parcours de vente avec livraison
7. Parcours de transport seul
8. Planification et engagement des ressources
9. Exécution et déchargement
10. Suivi financier
11. Consultation et qualité d’utilisation
12. Protection fiabilité et continuité
13. Réalisation et réception
14. Décisions de fonctionnement
15. Correspondance avec Requirements

## 1 Contexte et problème à résoudre

Une petite entreprise peut utiliser les mêmes véhicules pour livrer ses propres ventes et pour transporter les marchandises d’autres clients. Les employés doivent donc partager une vision commune des moyens disponibles, même lorsque les activités commerciales sont différentes.

La difficulté ne se limite pas à créer une fiche de mission. Il faut vérifier si les moyens sont réellement engageables, conserver les conditions convenues, suivre les changements et comprendre les montants encore dus. Dans une petite équipe, une personne peut assurer plusieurs fonctions ; son absence ne doit pas rendre les dossiers inaccessibles.

Les difficultés suivantes constituent le point de départ du projet. Leur fréquence et leur importance restent à vérifier auprès des entreprises visées ; elles ne sont pas présentées comme des constats établis pour tout le marché.

| Difficulté de départ | Conséquence possible | Réponse attendue du TMS |
|---|---|---|
| Disponibilité mal connue, notamment pendant les missions extérieures | Accepter une livraison sans moyens disponibles | Planning commun des missions, affectations et indisponibilités |
| Retard de trajet ou changement d’horaire | Information contradictoire et engagements suivants fragilisés | Événements manuels datés, estimations identifiées et réévaluation du planning |
| Attente chez le client avant déchargement | Véhicule immobilisé au-delà de la période prévue | Conditions de déchargement et heures réelles connues, avec visibilité sur les missions touchées |
| Information détenue par une seule personne | Appels répétés et interruption du travail en cas d’absence | Dossiers accessibles aux employés autorisés et historique des changements |
| Saisie longue ou répétée | Dossiers incomplets et erreurs de recopie | Fiches réutilisables et liaison directe entre vente et livraison |
| Paiements partiels et dépenses difficiles à distinguer | Solde client incorrect ou encaissement compté deux fois | Dette unique, encaissements confirmés et dépenses suivies séparément |

## 2 Objectifs et résultats attendus

L’objectif général est de permettre à l’équipe de préparer, exécuter et suivre les deux types d’activité avec les mêmes informations de transport, sans double saisie ni double comptabilisation.

| Objectif | Résultat observable dans l’application |
|---|---|
| Centraliser les informations utiles | Retrouver un client, sa demande, la mission liée et les événements disponibles |
| Mieux préparer les engagements | Connaître les occupations et incompatibilités avant de confirmer les ressources |
| Partager une information compréhensible | Identifier l’état déclaré d’une mission, la date du dernier événement et les informations manquantes |
| Rendre les attentes visibles | Distinguer arrivée, attente et déchargement lorsque les heures sont connues |
| Simplifier la saisie | Créer une livraison liée sans recopier le client et les lignes de vente |
| Expliquer les montants | Retrouver l’origine de la dette, les mouvements confirmés et le calcul du solde |
| Assurer la continuité du travail | Reprendre un dossier autorisé sous le compte du remplaçant, sans effacer l’auteur initial |

Ces résultats sont vérifiés sur des scénarios représentatifs. Les gains de temps, la diminution des appels ou l’amélioration de la ponctualité devront être mesurés ; aucun gain chiffré n’est garanti.

Le TMS apporte une aide à l’organisation. Il ne garantit ni une heure d’arrivée, ni une position physique du véhicule, ni une disponibilité que l’entreprise n’a pas renseignée.

## 3 Périmètre de la première version

### 3.1 Fonctions couvertes

| Domaine | Contenu de la V1 |
|---|---|
| Accès | Comptes individuels, connexion, déconnexion, désactivation et rôles cumulables |
| Référentiels | Clients, coordonnées utiles, véhicules, capacités et chauffeurs avec qualifications nécessaires |
| Demandes | Vente avec livraison ou transport seul ; souhaits du client distincts des engagements |
| Vente simple | Informations commerciales minimales et lien avec la livraison, sans ERP complet |
| Organisation du transport | Planning commun, disponibilité connue, affectations, réaffectations et indisponibilités |
| Suivi | États manuels, incidents, retards, estimations, historique et corrections |
| Déchargement | Responsabilités, conditions, créneau et jalons réels connus |
| Finance | Montants convenus, règlements partiels, confirmations, soldes et dépenses de mission |
| Consultation | Dossiers, listes d’exploitation, recherche, filtres et synthèse légère |
| Continuité | Protection des données, enregistrement fiable, reprise après erreur, sauvegarde et restauration |

Les recherches élémentaires nécessaires au travail quotidien font partie des fonctions qu’elles accompagnent. La génération d’un rapport exporté relève d’EF24 et de la décision Q22 ; elle ne conditionne pas l’existence des listes de consultation.

### 3.2 Limites explicites

La V1 ne comprend pas :

- le GPS, la localisation automatique ou le suivi physique en temps réel ;
- la prévision météo, le calcul automatique d’arrivée ou l’optimisation par intelligence artificielle ;
- une application mobile, un compte chauffeur ou un portail client ;
- des notifications externes automatiques par SMS, messagerie ou email ;
- le paiement en ligne, la connexion bancaire ou une comptabilité complète ;
- une gestion complète des achats, fournisseurs, stocks, maintenance ou paie ;
- un service payant de déchargement ou des pénalités automatiques d’attente ;
- une plateforme SaaS, son provisionnement, un abonnement ou une collecte centrale des données clients.

Certaines fonctions proches ne sont pas engagées non plus : livraisons fractionnées, groupage, plusieurs véhicules pour une même mission, délégation automatique, duplication avancée, planification récurrente et exports multiples. Leur absence n’autorise pas à les simuler avec des liens ou des mouvements financiers incohérents.

Une période d’entretien peut rendre un véhicule indisponible sans créer un module de maintenance. De même, une référence de justificatif ne suppose pas un stockage de fichiers joints.

### 3.3 Priorités et dépendances

Les niveaux P0, P1 et P2 conservent le sens défini dans Requirements :

- **P0 :** minimum cohérent des parcours et de leurs garanties ;
- **P1 :** fonctions importantes pour l’exploitation et la qualité d’usage ;
- **P2 :** fonctions secondaires ou extensions reportables.

Les dépenses, la consultation et les qualités d’usage restent dans le périmètre annoncé même si certaines exigences sont P1. Toute réduction effective doit être décidée explicitement. La sécurité, la fiabilité et la trace accompagnent les fonctions qu’elles protègent ; elles ne sont pas un ajout facultatif de fin de projet.

## 4 Utilisateurs et accès

### 4.1 Fonctions métier

| Fonction | Usage principal |
|---|---|
| Administration de l’entreprise | Gérer les comptes, attribuer les rôles et désactiver les accès |
| Coordination du transport | Préparer les missions, vérifier les ressources, confirmer les affectations et suivre l’exécution |
| Commercial | Gérer les clients, les demandes et la vente simple ; consulter les informations utiles pour répondre au client |
| Suivi financier | Enregistrer les montants et dépenses, confirmer les encaissements et effectuer les corrections autorisées |
| Consultation et pilotage | Retrouver les dossiers et synthèses autorisés |
| Sauvegarde et récupération | Exécuter ou contrôler les copies et les restaurations selon la procédure retenue |

Il s’agit de fonctions d’utilisation, pas de postes obligatoirement séparés. Une personne peut cumuler plusieurs rôles explicitement attribués. Le rôle d’administrateur des comptes ne donne pas automatiquement un accès métier ou financier complet.

Le chauffeur est une ressource de transport et une source d’information pour l’employé. Il ne possède pas de compte V1. Le client est une partie du dossier et ne dispose pas non plus d’un accès logiciel.

### 4.2 Principes d’accès

Chaque utilisateur agit avec son propre compte. Les permissions contrôlent les consultations autant que les modifications, y compris dans la recherche, les historiques, les compteurs et les exports. Un bouton masqué ne suffit pas à protéger une opération.

Le cumul de rôles reste limité à l’entreprise autorisée. Il ne permet ni l’accès aux dossiers d’une autre entreprise ni l’attribution de permissions supplémentaires non prévues par la matrice.

Un compte désactivé ne peut plus exécuter d’action protégée, même si une session était déjà ouverte. Ses actions passées gardent leur auteur. Lors d’un remplacement, le collègue utilise son propre compte avec les droits nécessaires ; il n’emprunte pas l’identité du créateur du dossier.

**Références :** EF01, EF02, ENF01, ENF02, ENF03 et ENF11. La matrice des droits et les modalités de récupération d’accès sont précisées par Q04 et Q18.

## 5 Vocabulaire et informations métier

### 5.1 Objets du travail quotidien

| Terme | Sens dans le TMS |
|---|---|
| Client | Personne ou organisation à l’origine de la vente ou du transport |
| Demande | Besoin reçu avec ses souhaits ; elle ne réserve aucune ressource par elle-même |
| Commande de vente | Accord commercial minimal sur des produits, quantités et montants |
| Mission | Opération de transport planifiée et suivie, commune aux deux parcours |
| Affectation | Engagement daté des ressources nécessaires pour une mission |
| Indisponibilité | Période pendant laquelle une ressource ne peut pas être engagée |
| Événement | Information sur un fait ou une action, avec auteur et date de saisie |
| Correction | Action qui rectifie une information tout en conservant son état antérieur |
| Dette ou obligation financière | Somme due identifiée une seule fois pour un dossier et ses composantes |
| Paiement annoncé | Information ou intention de payer sans encaissement confirmé |
| Règlement enregistré | Mouvement saisi dont le statut détermine son effet sur le solde |
| Encaissement confirmé | Réception de fonds confirmée par une personne habilitée |
| Dépense de mission | Frais réellement engagés pour une mission, distincts de la dette du client |

L’employé, son éventuel compte et la fiche chauffeur sont des notions distinctes. De même, la demande, la commande et la mission ne partagent pas automatiquement le même état.

### 5.2 Informations nécessaires

| Ensemble | Informations métier à pouvoir retrouver |
|---|---|
| Client | Référence stable, nom ou libellé, contacts utiles et coordonnées nécessaires au dossier |
| Ressources | Véhicule, immatriculation, type et capacités utiles ; chauffeur, contact et qualification requise |
| Demande | Type de parcours, client, charge, lieux réels, fenêtres souhaitées et informations encore manquantes |
| Vente | Référence, contenu commercial minimal, quantités, montants et lien de livraison |
| Mission | Période prévue, ressources engagées, état, conditions convenues et liens vers le dossier d’origine |
| Exécution | Faits connus, heures prévues et réelles, estimations successives, incidents et conditions de déchargement |
| Finance | Montant dû, ajustements autorisés, règlements et statuts, confirmations, dépenses et références utiles |
| Trace | Auteur stable, date de saisie, information rectifiée et motif lorsque requis |

Cet inventaire exprime les informations nécessaires au métier. Il n’impose ni classes, ni noms de tables, ni schéma SQL.

### 5.3 Saisie selon l’étape

Une demande peut commencer avec des données incomplètes. Le système doit distinguer ce brouillon d’un dossier prêt à être confirmé. Les données nécessaires sont exigées au moment où l’action en dépend, sans obliger l’utilisateur à inventer une valeur pour avancer.

Une valeur inconnue reste inconnue. Elle ne devient ni zéro, ni l’heure de saisie, ni une capacité supposée. Les quantités et capacités portent des unités comparables : des cartons ne deviennent pas des tonnes sans poids ou conversion connue.

La fiche client ne doit pas imposer une adresse de siège comme lieu de déchargement. Deux personnes portant le même nom ne sont pas fusionnées automatiquement. Un identifiant fiscal n’est demandé que pour les catégories et usages qui le nécessitent.

Une modification de fiche ne réécrit pas silencieusement le passé. Les lieux ou conditions d’une mission confirmée suivent leur propre procédure de correction. Les références utilisées sont conservées par archivage ou traitement équivalent préservant les liens.

**Références :** EF03 à EF07, ENF07 et ENF12 ; décisions Q02, Q03, Q09 et Q17.

## 6 Parcours de vente avec livraison

### 6.1 Déroulement

1. **Identifier le client.** Rechercher la fiche existante ou créer une fiche minimale pour éviter une ressaisie inutile.
2. **Enregistrer la vente.** Conserver les produits, quantités et montants nécessaires à la gestion commerciale simple. Le contenu commercial exact est arrêté dans Q02.
3. **Préparer la livraison.** Créer ou relier la demande de livraison en reprenant les données utiles, puis vérifier la charge, les lieux réels, les souhaits horaires et les conditions de déchargement.
4. **Évaluer les moyens.** Examiner les véhicules, chauffeurs, occupations et indisponibilités sur toute la période nécessaire.
5. **Confirmer la mission.** Engager les ressources et la période après les contrôles, en conservant le lien avec la vente.
6. **Suivre l’exécution.** Enregistrer manuellement les informations reçues, le trajet, les incidents et les étapes de déchargement applicables.
7. **Clôturer l’opération et suivre les montants.** Conserver le résultat de la livraison, puis poursuivre le suivi financier tant qu’un montant reste dû.

Le passage de la vente à la livraison ne recopie pas un dossier indépendant. Les deux dossiers doivent rester consultables dans les deux sens. Relancer une création de livraison après une interruption doit retrouver le lien existant, sans créer une seconde mission par inadvertance.

### 6.2 Relations à préserver

La mission n’ajoute pas une deuxième dette déjà portée par la vente. Le prix des produits et le prix du transport peuvent être distingués, mais un même montant dû ne doit pas être tenu dans deux totaux autonomes.

Modifier les lignes après confirmation peut affecter la charge, le prix ou la période. La correction doit donc déclencher les contrôles concernés ; elle ne conserve pas silencieusement une affectation devenue incompatible.

La simplification proposée dans Requirements est **au plus une mission active par demande, avec un véhicule et un chauffeur par mission**. Cette cardinalité reste soumise à Q03. Le groupage ou le fractionnement n’est pas ajouté implicitement.

Une affectation n’indique ni une vente payée ni une livraison réalisée. La fin du transport ne clôture pas automatiquement la dette.

**Références :** EF03, EF05 à EF10, EF13, EF16 et EF18 à EF20.

## 7 Parcours de transport seul

### 7.1 Déroulement

1. **Identifier le client et sa demande.** Décrire les biens à déplacer, les lieux, la fenêtre souhaitée, les conditions utiles et le prix du transport.
2. **Compléter les données d’engagement.** Vérifier les informations nécessaires sur la charge et les ressources, sans créer de commande de vente fictive.
3. **Planifier et confirmer.** Utiliser le même planning et les mêmes contrôles que pour une livraison liée à une vente.
4. **Suivre la mission.** Enregistrer les événements manuels, les retards et le déchargement applicable.
5. **Clôturer et suivre les règlements.** Conserver les dépenses engagées, les encaissements et le solde de la prestation.

La différence entre les deux parcours se situe à l’entrée commerciale. Ils partagent ensuite les ressources, les règles de disponibilité, les états de mission, les événements et les principes financiers.

Une mission extérieure réalisée avec les mêmes ressources doit apparaître dans le planning et les contrôles d’occupation. Elle ne doit pas devenir un engagement invisible qui permettrait de promettre deux prestations incompatibles.

**Références :** EF05, EF06, EF08 à EF21. EF07 concerne la vente liée et n’est pas une condition du transport seul.

## 8 Planification et engagement des ressources

### 8.1 Trois informations à distinguer

| Information | Ce qu’elle signifie |
|---|---|
| Date ou fenêtre souhaitée | Préférence exprimée par le client, sans réservation |
| Période confirmée | Occupation acceptée après vérification et engagement des ressources |
| Estimation actualisée | Prévision manuelle fondée sur les informations connues, sans garantie d’arrivée |

Le planning rassemble les missions des deux parcours, les ressources engagées et les indisponibilités. Une mission à planifier sans date reste retrouvable ; elle ne reçoit pas de période fictive pour apparaître dans une vue.

### 8.2 Période d’occupation

La disponibilité s’évalue sur la période pendant laquelle la ressource ne peut pas assurer une autre mission. Cette période comprend les phases nécessaires : chargement, trajet, déchargement et, selon le cas, retour ou déplacement vers le lieu suivant.

Les occupations du véhicule et du chauffeur doivent correspondre au fonctionnement retenu. Aucune durée standard ni marge fixe n’est inventée. Les estimations sont manuelles ; la V1 ne calcule pas automatiquement les itinéraires et les temps de déplacement.

Une capacité connue insuffisante, une qualification non valable ou des données indispensables manquantes ne permettent pas de présenter la ressource comme compatible. Le résultat distingue **compatible**, **incompatible** et **information insuffisante**, avec une raison compréhensible.

Consulter les disponibilités ne réserve rien. Le contrôle doit être renouvelé à la confirmation, car un autre utilisateur peut avoir engagé la même ressource entre-temps.

### 8.3 Confirmation et réaffectation

La confirmation engage ensemble les ressources requises et la période. Une sélection partielle peut rester au brouillon, mais elle ne doit pas produire une mission présentée comme entièrement planifiée.

Lors d’un remplacement, le nouveau couple de ressources est contrôlé avant de remplacer l’ancien engagement. Si la réaffectation échoue, l’affectation précédente reste cohérente. Le système ne laisse pas une réservation partielle ou un dossier dont l’écran et le planning se contredisent.

L’annulation avant départ libère les réservations futures selon la procédure définie. Un changement pendant une mission demande une date d’effet et la conservation des faits antérieurs, ou une limite explicite si ce cas n’est pas pris en charge par la procédure standard.

### 8.4 Chevauchements et retards réels

La convention proposée dans EF11 utilise des périodes **[début, fin[** : le début est inclus, la fin exclue. Deux périodes se chevauchent si le début de chacune précède la fin de l’autre. Cette convention est à confirmer dans Q08.

Deux périodes qui se touchent ne sont acceptables que si les temps nécessaires entre les missions sont déjà couverts. Finir à un lieu et commencer immédiatement à un autre ne devient pas possible par le seul calcul des horaires.

Il faut distinguer deux situations :

| Situation | Réponse attendue |
|---|---|
| Nouvelle confirmation incompatible | Refuser l’engagement et expliquer les occupations concernées |
| Conflit apparu après une panne, un retard ou une attente | Conserver le fait réel, afficher les engagements touchés et permettre leur traitement humain |

Le logiciel ne doit pas refuser une panne réelle pour préserver artificiellement son planning. Il ne décale ni n’annule automatiquement les missions suivantes. Une ressource encore occupée n’est pas libérée au seul dépassement de l’heure prévue ; une fin inconnue ne permet pas de conclure automatiquement à sa disponibilité.

### 8.5 Exemple de situation

Un véhicule doit finir une livraison à 12 h et repartir pour une autre mission à 13 h. À 11 h 45, l’employé apprend que le déchargement n’a pas commencé et actualise la fin estimée à 14 h.

Le TMS conserve cette information, réévalue l’occupation et signale la mission de 13 h comme concernée. Il ne déplace pas cette mission à 14 h, ne prévient pas le client automatiquement et ne modifie pas les heures prévues pour masquer le conflit. L’employé examine les solutions puis enregistre la décision autorisée.

**Références :** EF04, EF06, EF08 à EF12, EF14, EF16 et ENF13 ; décisions Q03, Q05 à Q09.

## 9 Exécution et déchargement

### 9.1 Informations reçues du terrain

L’employé habilité enregistre les informations après leur réception, par exemple lors d’un appel. Chaque événement important conserve son auteur et son heure de saisie. L’heure réelle est conservée séparément lorsqu’elle est connue.

Un départ à 9 h saisi à 9 h 20 doit donc pouvoir être compris comme tel. L’heure de saisie ne remplace pas le départ réel et ne devient pas une heure librement modifiable dans l’application.

L’affichage distingue la date du dernier événement métier et la date à laquelle l’utilisateur a actualisé sa consultation. Cliquer sur « actualiser » ne rend pas plus récente une information reçue la veille.

### 9.2 Cycle de mission

Le cycle ci-dessous est celui proposé par EF13. Les transitions exactes et les conditions de clôture sont arrêtées dans Q10 à Q12.

| Situation | Évolution et condition |
|---|---|
| À planifier | Devient planifiée après confirmation des ressources et de la période |
| Planifiée | Peut revenir à planifier avant départ avec retrait motivé ; passe en cours lorsque le départ est signalé |
| En cours | Passe à arrivée après déclaration de l’arrivée |
| Arrivée | Passe en attente si une attente réelle existe, ou directement en déchargement si celui-ci commence |
| En attente de déchargement | Passe en déchargement après signalement du début |
| En déchargement | Passe à terminée après déclaration de fin et satisfaction des conditions de clôture |
| Arrivée sans déchargement applicable | Peut passer à terminée selon les conditions retenues |
| À planifier ou planifiée | Peut être annulée avant départ, avec motif et traitement des réservations |
| Mission déjà commencée | Arrêt exceptionnel à définir ; ne pas l’assimiler à une annulation ordinaire avant départ |
| Terminée ou annulée | Pas de retour ordinaire effaçant le passé ; correction ou réouverture selon procédure autorisée |

Le retard et l’incident complètent le suivi ; ils ne remplacent pas l’état opérationnel. Une mission peut subir un incident sans être en retard, et être en retard sans nouvelle estimation disponible.

Un appel tardif peut apporter plusieurs faits à la fois. La saisie doit conserver les événements connus dans un ordre cohérent, sans obliger l’utilisateur à inventer une attente ou une heure inconnue.

### 9.3 Retards et estimations

Le suivi conserve le prévu initial, les estimations successives et les heures réelles disponibles. Une cause inconnue ou une estimation indisponible reste acceptable et visible.

Une ETA est une estimation manuelle de l’arrivée. Elle n’est ni une localisation GPS ni une promesse automatique. Si l’information change l’occupation prévue, les ressources et missions suivantes sont réévaluées. L’employé reste chargé de contacter le client par les moyens habituels.

### 9.4 Déchargement et immobilisation

Avant la mission, les conditions utiles précisent qui organise le déchargement, les moyens attendus et le créneau convenu. Elles peuvent être nécessaires pour apprécier si la prestation est réalisable ; l’application ne suppose pas que le transporteur fournit du personnel.

Le suivi distingue quatre informations : arrivée, attente réelle, début et fin du déchargement. Les durées sont calculées seulement avec des bornes connues et cohérentes :

- **attente = début du déchargement − arrivée** ;
- **durée du déchargement = fin − début**.

Avec une arrivée à 9 h 15, un début à 9 h 30 et une fin à 10 h 15, l’attente vaut 15 minutes et le déchargement 45 minutes. Si le début est inconnu, ces deux durées ne sont pas inventées. Une fin connue peut être conservée sans faire croire que la durée est connue.

Les dates complètes permettent de traverser minuit. Une attente nulle signifie que le début coïncide avec l’arrivée ; elle ne signifie pas qu’aucune information n’a été reçue.

Le déchargement prolongé peut maintenir l’occupation des ressources et affecter la suite du planning. Il ne produit pas de frais ou de prestation payante automatiquement.

### 9.5 Historique et corrections

Les créations, confirmations, affectations, changements d’état, incidents et corrections importants restent consultables selon les droits. Une correction ajoute une trace liée au fait corrigé ; les fonctions ordinaires ne réécrivent pas l’historique en supprimant la valeur précédente.

L’identité historique est conservée après désactivation d’un compte. L’ordre de saisie doit permettre de distinguer deux événements enregistrés à la même minute. La visibilité de la chronologie ne doit pas donner indirectement accès aux montants réservés aux utilisateurs financiers.

**Références :** EF13 à EF17, ENF07 et ENF08 ; décisions Q10 à Q12, Q20 et Q21.

## 10 Suivi financier

### 10.1 Une dette identifiable une seule fois

Chaque somme due appartient à un dossier identifiable. Pour une vente avec livraison, le prix des produits et celui du transport peuvent former les composantes d’une même obligation financière. Consulter la vente puis sa mission ne crée pas une seconde créance.

Dans un transport seul, le montant dû correspond à la prestation convenue. Les règles de prix global ou ventilé, de devise, de précision et de montant nul sont définies dans Q13. Aucun calcul complet de taxes, remises ou documents comptables n’est ajouté par défaut.

Le montant au brouillon peut rester à négocier ; cet état doit être clair. Il ne doit pas être affiché comme un accord définitif sans validation.

### 10.2 Annonce enregistrement et confirmation

| Situation | Sens | Effet sur le solde |
|---|---|---|
| Paiement annoncé | Le client ou un employé annonce une intention ou un envoi | Aucun encaissement déduit |
| Règlement enregistré en attente | Le mouvement est saisi, mais sa réception n’est pas confirmée | Aucun encaissement déduit |
| Encaissement confirmé | La réception est confirmée avec les droits et éléments requis | Le mouvement entre dans le calcul |
| Mouvement non confirmé rejeté ou annulé | L’annonce ou le règlement en attente est écarté avec motif | Pas de réduction de dette par ce mouvement |
| Mouvement confirmé rectifié | Correction par mouvement lié et autorisé | Effet net explicable, sans double correction |

L’enregistrement et la confirmation peuvent se faire dans la même action si les permissions et éléments nécessaires sont présents. Il n’existe pas d’obligation de passage artificiel par une attente ; à l’inverse, toute saisie ne vaut pas automatiquement encaissement.

Les modes documentés sont les espèces, le chèque et le virement. Les références et preuves nécessaires dépendent du mode et de l’étape. Un numéro de chèque n’atteste pas son encaissement. Une annonce de virement ne prouve pas la réception des fonds.

Les doublons probables sont signalés, sans refuser deux paiements légitimes sur le seul motif qu’ils ont le même montant. La référence n’est pas supposée universellement unique. Après une interruption technique, l’état existant doit être vérifié avant une nouvelle saisie ou confirmation.

### 10.3 Calcul du solde

La règle proposée par EF20 est la référence commune des fiches, listes et synthèses :

**D = montant initial + ajustements de dette validés signés**  
**E = encaissements confirmés − annulations ou contre-mouvements d’encaissement confirmés − remboursements confirmés**  
**S = D − E**

Chaque correction intervient une seule fois. Le remboursement d’un encaissement et son contre-mouvement ne sont pas soustraits deux fois pour le même effet. Les dépenses de mission n’entrent ni dans D ni dans E.

| Valeur du solde | Lecture métier |
|---|---|
| S > 0 | Somme restant à recevoir |
| S = 0 | Dossier soldé au sens du suivi financier |
| S < 0 | Trop-perçu à traiter uniquement selon la politique approuvée |

Le solde se calcule ; il ne constitue pas une deuxième valeur saisie manuellement. Un total client reprend les obligations sans compter deux fois une vente et sa livraison. Le terme « impayé échu » exige une échéance et une règle de retard approuvées ; à défaut, l’application affiche un solde restant.

### 10.4 Exemples de lecture

**Paiement partiel.** Une vente de 4 000 MAD et un transport de 1 000 MAD donnent une dette unique de 5 000 MAD. Avec 2 000 MAD confirmés, 1 000 MAD annoncés et 300 MAD de dépenses, le solde reste 3 000 MAD.

**Réduction du prix.** Un ajustement de dette validé de −500 MAD réduit la dette à 4 500 MAD. Si les encaissements nets restent de 2 000 MAD, le solde devient 2 500 MAD. Cette réduction ne crée pas un remboursement à elle seule.

**Annulation et restitution.** Pour une dette initiale de 5 000 MAD avec 2 000 MAD reçus, l’annulation commerciale autorisée peut porter la dette à zéro. Si les 2 000 MAD sont ensuite remboursés et ce remboursement confirmé, les encaissements nets deviennent nuls et le solde est nul. L’accord, l’annulation et le remboursement restent distincts et consultables.

Ces exemples décrivent le calcul ; les autorisations, justificatifs et procédures de régularisation sont arrêtés dans Q14 et Q15.

### 10.5 Dépenses et régularisations

Les dépenses correspondent aux frais réellement engagés pour une mission. Elles conservent la catégorie, la date, le montant, l’auteur et une référence de justificatif si disponible. Une correction préserve la trace et les doublons probables sont signalés.

Une mission annulée peut conserver des frais réels de carburant ou de déplacement. Ces frais ne réactivent pas la mission et ne diminuent pas la somme due par le client. Leur total ne doit pas être présenté comme une marge nette.

L’annulation d’une mission ne supprime pas automatiquement sa dette ou ses encaissements. La correction du prix, l’annulation commerciale et le remboursement sont des décisions distinctes. Le traitement du trop-perçu doit être défini avant l’usage financier concerné ; la proposition d’EF18 bloque sa confirmation tant qu’aucune politique n’est approuvée, sans créer d’avoir automatique.

Le TMS enregistre des faits financiers. Il ne transfère pas d’argent, ne réalise pas de rapprochement bancaire automatique, ne certifie pas la conformité comptable et ne protège pas le transport physique des espèces.

**Références :** EF18 à EF21, ENF05, ENF07, ENF08 et ENF13 ; décisions Q13 à Q16 et Q24.

## 11 Consultation et qualité d’utilisation

### 11.1 Retrouver une information utile

La consultation doit permettre de passer d’une liste au dossier qui explique le résultat : demande, mission, événement, vente liée ou mouvement financier autorisé.

| Vue | Usage attendu |
|---|---|
| Planning | Examiner les engagements, ressources et indisponibilités sur une période |
| Liste d’exploitation | Identifier missions à suivre, retards déclarés, attentes et conflits |
| Synthèse légère | Résumer l’activité et permettre de retrouver les éléments comptés |
| Recherche et filtres | Retrouver les dossiers par référence, client, état, ressource et période |
| Rapport si retenu | Produire une restitution figée avec date, périmètre, filtres et limites |

Le tableau de bord reprend les mêmes règles que les dossiers sources. Une ressource indisponible n’est pas comptée plusieurs fois pour un même indicateur. Des catégories qui se recoupent ne sont pas additionnées comme si elles formaient des ensembles séparés.

Un compteur ne doit pas révéler un montant ou un dossier inaccessible à l’utilisateur. Les droits s’appliquent aux totaux et au détail.

### 11.2 Dates filtres et données manquantes

Les filtres actifs sont visibles, combinés par ET et réinitialisables. La signification de la date est explicite : date de création, début prévu ou arrivée réelle selon l’opération.

Pour le planning, la proposition d’EF23 retient les occupations qui intersectent la période recherchée. Les dossiers sans date ne correspondent pas à un filtre temporel ; cette exclusion doit être compréhensible. Une limite de résultats ne doit pas être présentée comme une liste complète.

Il faut distinguer **aucun résultat**, **information absente**, **ancienne information affichée** et **échec de lecture**. Une panne de recherche ne devient pas une liste vide ; un échec d’actualisation ne devient pas un compteur à zéro.

### 11.3 Rapports et indicateurs

Si un rapport est retenu, il indique la date de génération, l’entreprise concernée, les filtres, les unités et les données manquantes. Son contenu doit rester cohérent si d’autres saisies ont lieu pendant sa production. Un fichier qui n’a pas pu être écrit n’est pas annoncé comme disponible.

Une moyenne d’attente utilise seulement les observations dont les bornes sont connues et indique les exclusions. Un taux de retard nécessite une définition et un dénominateur approuvés. En leur absence, utiliser un nombre de retards signalés plutôt qu’un taux trompeur.

### 11.4 Utilisation quotidienne

Les formulaires demandent les informations utiles à l’action, avec des libellés simples. Ils réutilisent les fiches existantes, identifient les erreurs et préservent les autres saisies lorsque c’est possible.

Les actions de confirmation, annulation et correction doivent avoir un effet compréhensible. L’utilisateur doit savoir si une opération a été enregistrée et ce qu’il reste à compléter. Une duplication avancée éventuelle ne reprendrait pas les paiements, incidents, réservations ou étapes réalisées ; elle n’est pas requise par défaut.

L’ergonomie se mesure sur les deux parcours, avec un matériel, des dimensions de fenêtre et un niveau de formation définis. Aucun seuil de durée ni nombre maximal de champs n’est réputé validé sans le protocole correspondant.

**Références :** EF08, EF17, EF22 à EF24, ENF04 et ENF12 ; décisions Q21 à Q23.

## 12 Protection fiabilité et continuité

### 12.1 Protection et séparation des entreprises

Les mots de passe ne sont pas conservés en clair ou sous une forme récupérable. Leur vérification repose sur un mécanisme adapté, salé et documenté. Les secrets ne figurent pas dans les messages ou journaux ; leur transport est protégé si le déploiement utilise des échanges réseau.

La séparation des entreprises est une garantie de confidentialité, pas l’obligation d’utiliser une plateforme centrale. Une installation par entreprise ou des espaces isolés peuvent répondre au besoin selon l’étude de déploiement. Les protections couvrent aussi les liens, recherches, agrégats, historiques consultables, exports et copies.

Un prototype limité à une entreprise ne prouve pas, à lui seul, la résistance aux accès croisés. La conception et la vérification de cette garantie restent à prévoir selon Q05 et ENF03 ; son report n’est pas justifié par le seul classement P2 d’une extension de capacité.

L’éditeur ne dispose d’aucun accès métier ni droit de réutilisation des données par défaut. La conservation et les accès techniques doivent être définis ; une future collecte d’analyse nécessite un cadrage distinct.

### 12.2 Enregistrement et reprise

Une opération importante ne doit être déclarée réussie que si ses effets nécessaires sont enregistrés de façon cohérente. Une affectation ne laisse pas un véhicule réservé sans le reste de l’engagement requis ; une confirmation de règlement ne doit pas produire un solde incompatible avec ses mouvements.

| Résultat connu | Message et suite attendus |
|---|---|
| Réussite vérifiée | Confirmer l’enregistrement et rendre le résultat consultable |
| Échec certain | Expliquer l’échec, éviter les effets partiels contradictoires et permettre la correction ou la reprise |
| Résultat incertain après une coupure | Signaler l’incertitude et vérifier ce qui existe avant de relancer l’écriture |

La reprise ne doit pas créer une seconde demande, affectation ou confirmation financière. Une répétition automatique n’est acceptable que si son absence d’effet en double est garantie ou si l’état a été vérifié.

Les données non encore enregistrées ne sont pas garanties contre un arrêt physique brutal. Leur préservation lorsque possible ne constitue pas une promesse de synchronisation hors connexion.

### 12.3 Écritures simultanées

Si plusieurs utilisateurs peuvent modifier les données, le système empêche les écrasements silencieux et les confirmations incompatibles. Deux missions différentes visant le même véhicule doivent être contrôlées ensemble, même si les utilisateurs n’éditent pas la même fiche.

Une version devenue périmée est signalée pour réexamen. Le mécanisme technique est laissé à la conception. Si le prototype est limité à un seul écrivain, cette restriction doit être effective et documentée ; il ne peut pas être présenté comme un usage multiposte complet.

### 12.4 Trace et récupération

La trace couvre les changements critiques de droits, montants, règlements, ressources, états et conditions. Elle conserve les informations utiles à l’explication, sans mots de passe ni collecte exhaustive des lectures par défaut. Sa protection contre les fonctions ordinaires ne constitue pas une garantie absolue contre tout accès d’administration système.

Une sauvegarde de secours est différente de l’enregistrement d’un formulaire. Elle doit permettre de restaurer les données utiles avec leurs liens, montants et historiques. Un fichier présent ou un checksum correct ne prouve pas, seul, que cette restauration fonctionne.

La procédure précise qui réalise et contrôle les copies, les données incluses, l’emplacement, la protection, la fréquence, la conservation et le rattrapage d’une copie manquée. Elle définit aussi la perte admissible et le délai de reprise. Aucun horaire nocturne ou délai chiffré n’est imposé sans décision adaptée au poste et à son usage.

La restauration est vérifiée sur une destination contrôlée, sans écrasement non maîtrisé des données en exploitation.

**Références :** ENF01 à ENF03, ENF05 à ENF09, ENF11 et ENF13 ; décisions Q04, Q05 et Q18 à Q20.

## 13 Réalisation et réception

### 13.1 Cadre technique

Le produit est une application **Java Desktop**. JavaFX, le SGBD, les mécanismes d’accès aux données et la topologie de stockage restent des choix à instruire. Ce cahier ne prescrit ni API Web, ni architecture SaaS, ni patron de conception particulier.

Le logiciel distingue les responsabilités de présentation, de règles métier et d’accès aux données. Les règles de disponibilité, de cycle et de solde ne doivent pas être réimplémentées différemment dans plusieurs écrans.

Le déploiement précise les postes, le stockage, les possibilités de partage et le nombre d’écrivains. Les instructions de construction, installation, lancement et récupération doivent correspondre à la version livrée.

Les capacités et performances sont évaluées sur un matériel, un volume et une simultanéité définis. Le classement P2 d’ENF14 n’autorise pas à laisser un parcours essentiel inutilisable ou à promettre une charge illimitée.

### 13.2 Résultat à livrer

Le dossier de conception comprend le cadrage métier, les exigences détaillées, les modèles UML utiles, les choix de réalisation justifiés et les maquettes des parcours. Il doit rendre possibles les décisions nécessaires au développement, sans présenter le code final comme déjà réalisé.

La livraison de l’application comprend le code source, les éléments nécessaires au stockage retenu, les instructions de construction et d’installation, la documentation d’utilisation, la procédure de sauvegarde et les résultats de tests avec leurs limites connues. Les contraintes pédagogiques et échéances applicables doivent être confirmées ; aucun livrable ne peut être déclaré terminé par sa seule présence dans une liste.

### 13.3 Scénarios globaux de réception

Les critères détaillés restent ceux de Requirements. Les scénarios suivants vérifient que les domaines fonctionnent ensemble.

| Scénario | Résultat global attendu |
|---|---|
| Vente avec livraison | Vente minimale et livraison liées, données réutilisées, mission suivie et dette comptée une fois |
| Transport seul | Mission réalisable sans commande de vente, avec le même traitement des ressources et événements |
| Double engagement | Deux confirmations incompatibles d’une même ressource ne peuvent pas toutes deux réussir |
| Retard et déchargement prolongé | Fait réel conservé, occupations réévaluées, missions touchées visibles et aucun supplément automatique |
| Règlement partiel | Annonce distincte de la confirmation, solde explicable et dépenses exclues du montant restant dû |
| Correction ou annulation | Historique, faits réalisés et mouvements financiers conservés ; absence de remboursement implicite |
| Remplacement et droits | Reprise nominative autorisée et refus des actions ou lectures non attribuées |
| Coupure et reprise | Aucun faux succès ni doublon après vérification du résultat incertain |
| Sauvegarde et restauration | Jeu restauré avec liens, événements et montants cohérents, selon la politique approuvée |
| Confidentialité | Accès et liens croisés refusés suivant le déploiement ; les limites d’un essai monoentreprise sont indiquées |

Les essais utilisent des données fictives. Une fuite de données, un calcul financier faux, un écrasement silencieux ou un effet partiel contradictoire empêche d’accepter le scénario concerné. Un critère dépendant d’une décision ouverte n’est pas déclaré satisfait sur une hypothèse non approuvée.

**Références :** critères CA et RF de Requirements, règles communes RC-1 à RC-5, ENF10 et ENF14.

## 14 Décisions de fonctionnement

Les identifiants ci-dessous sont ceux de Requirements. Les réponses doivent être consignées au même endroit, avec date, approbation et références affectées, pour éviter deux règles concurrentes dans les deux documents.

Le cadrage Java Desktop, les deux parcours et l’absence de comptes chauffeur et client sont établis. Les questions suivantes portent sur leurs modalités ; elles ne réouvrent pas implicitement ces choix.

| Décisions | Réponse attendue | Domaine conditionné |
|---|---|---|
| Q01 | Minimum détaillé des deux parcours, critères et délais effectivement retenus | Périmètre de réalisation et engagement de réception |
| Q02 | Contenu commercial minimal : lignes simples ou référence externe explicitement décidée | Vente et lien de livraison ; le parcours A reste présent |
| Q03 | Nombre de missions par demande, ressources par mission et traitement éventuel des cas multiples | Liens métier et cardinalités ; la simplification proposée ne vaut pas validation |
| Q04 | Matrice des lectures, saisies, confirmations, annulations, corrections et remplacements | Permissions et responsabilités d’utilisation |
| Q05 | Nombre d’entreprises de démonstration, postes, stockage, partage et possibilités d’écritures simultanées | Déploiement, confidentialité et concurrence |
| Q06 à Q09 | Moment de l’engagement ; périodes, transit et fins inconnues ; bornes et conflits ; capacités et qualifications nécessaires | Confirmation fiable et disponibilité |
| Q10 à Q12 | États et transitions ; correction et réouverture ; déchargement et conditions de clôture | Exécution normale et cas exceptionnels |
| Q13 à Q15 | Prix global ou ventilé, devise et précision ; modes et preuves ; régularisations et trop-perçus | Calcul financier et usage opérationnel des mouvements |
| Q16 | Échéance de paiement et éventuelle notion d’impayé échu | Libellés et indicateurs de suivi des soldes |
| Q17 | Types de clients, données administratives et règles d’archivage ou fusion | Qualité des référentiels et conservation des liens |
| Q18 | Inactivité, essais de connexion, récupération et continuité du dernier accès administrateur | Gestion des sessions et accès de secours |
| Q19 et Q20 | Copie, restauration et objectifs de reprise ; contenu, lecteurs et conservation des traces | Récupération et confidentialité des données |
| Q21 et Q22 | Fréquence utile des mises à jour, contact client ; rapport, format, indicateurs et export retenus | Information d’exploitation et restitutions |
| Q23 | Matériel, dimensions de fenêtre, volume, simultanéité et protocole de mesure | Objectifs chiffrés d’ergonomie et de performance |
| Q24 | Référence textuelle de justificatif ou besoin explicite de pièces jointes | Étendue du stockage et des sauvegardes |

Une question ouverte ne bloque pas nécessairement tout travail : les éléments indépendants peuvent être préparés. Elle empêche en revanche de figer la règle concernée, de promettre le cas non défini ou d’en prononcer la réception. Les paramètres manquants ne sont pas remplacés par des nombres arbitraires.

## 15 Correspondance avec Requirements

Cette correspondance permet de passer du besoin expliqué ici aux fiches détaillées, sans créer une deuxième numérotation d’exigences.

| Sujet du cahier | Sections | Exigences associées |
|---|---|---|
| Connexion comptes rôles et remplacement | 4 et 12 | EF01, EF02 ; ENF01, ENF02, ENF11 |
| Clients et ressources | 5 et 8 | EF03, EF04a, EF04b sous EF04 ; ENF07, ENF12 |
| Demandes contenu et vente liée | 5 à 7 | EF05, EF06, EF07 ; ENF12 |
| Planning disponibilité et affectation | 8 | EF08, EF09, EF10, EF11, EF12 ; ENF13 |
| États retards et historique | 9 | EF13, EF14, EF15 ; ENF08 |
| Déchargement et occupation | 8 et 9 | EF16, avec EF06, EF11 et EF13 |
| Liste d’exploitation et information connue | 9 et 11 | EF17, avec EF08, EF14 et EF15 |
| Dette règlements et soldes | 10 | EF18, EF19, EF20 ; ENF05, ENF07, ENF08, ENF13 |
| Dépenses de mission | 10 | EF21 |
| Synthèse recherche et rapports | 11 | EF22, EF23, EF24 |
| Confidentialité et séparation | 4 et 12 | ENF02, ENF03 |
| Ergonomie et réutilisation | 5 et 11 | ENF04, ENF12 |
| Enregistrement erreurs et intégrité | 12 | ENF05a et ENF05b sous ENF05, ENF06, ENF07 |
| Traçabilité et récupération | 9 et 12 | ENF08, ENF09 |
| Maintenabilité capacité et mesures | 13 | ENF10, ENF14 |
| Arbitrages de fonctionnement | 14 | Q01 à Q24 |

Le cahier explique le fonctionnement d’ensemble ; les fiches EF et ENF portent leurs critères vérifiables. Toute décision affectant un parcours, une limite ou une règle commune doit se retrouver dans les deux documents avant la réception correspondante.
