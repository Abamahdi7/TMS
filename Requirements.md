
# Exigences — TMS (Transport Management System) V1

Application **Java Desktop**. Deux parcours : **A) vente avec livraison**, **B) transport seul**.

## 1. Périmètre

**Inclus :** comptes et droits ; clients, véhicules, chauffeurs ; demandes A et B ; vente minimale liée à sa livraison ; planning, affectation, conflits, indisponibilités ; états de mission, retards, incidents, historique ; temps de déchargement ; montants, paiements, soldes, dépenses ; listes et recherche ; sécurité, intégrité, sauvegarde.

**Exclu :** GPS/temps réel, mobile, compte chauffeur, portail client, notifications externes, paiement en ligne, comptabilité, stocks/achats, SaaS, exports multiples, pièces jointes.

## 2. Acteurs

| Acteur | Rôle |
|---|---|
| Administrateur | Comptes, rôles |
| Coordinateur | Planning, affectation, suivi |
| Commercial | Clients, demandes, vente |
| Financier | Montants, paiements, dépenses |
| Lecteur autorisé | Consultation selon droits |
| Chauffeur / Client | Ressource / partie métier — **aucun compte logiciel** |

## 3. Règles communes

- **Autorisation** : toute action vérifie droits + entreprise, au point d'exécution (pas seulement l'interface).
- **Écriture** : une opération réussit entièrement ou échoue explicitement. Une correction garde l'ancienne valeur, l'auteur, la date, un motif.
- **Inconnus** : une valeur inconnue reste absente et signalée — jamais remplacée par zéro.
- **Minimum par étape** : brouillon incomplet autorisé ; confirmation = champs nécessaires à l'action seulement.

## 4. Fonctionnalités (10)

### F1 — Authentification et comptes
Connexion/déconnexion, expiration après inactivité. Comptes individuels, rôles cumulables. Désactivation → accès révoqué aux actions suivantes ; historique conservé.
- Un compte actif accède uniquement à ses permissions.
- Mot de passe faux / compte absent / désactivé → même message, aucun accès.
- Après déconnexion ou expiration → reconnexion requise.

### F2 — Données de référence
**Clients** : identifiant stable, nom, contacts, adresses ; recherche et contrôle des doublons ; archivage si utilisé ; modification ne réécrit pas une mission confirmée.
**Véhicules** : immatriculation unique, type, capacités.
**Chauffeurs** : identité, contact, permis/validité. Ressource distincte d'un compte.
- Homonymes = fiches distinctes ; identifiants fiscaux identiques signalés.
- Corriger un client ne modifie pas le lieu convenu d'une mission confirmée.
- Chauffeur sans qualification valable sur la période non confirmable.

### F3 — Demandes (deux parcours)
Créer une demande « transport seul » ou « vente avec livraison », compléter, valider, annuler. Cycle : brouillon → validée → clôturée / annulée. Une demande ne confirme ni date ni ressource.
- Transport seul validé planifiable sans commande.
- Annuler une demande affectée conserve mission et historique ; réservations futures libérées.
- Demande similaire signalée, jamais fusionnée automatiquement.

### F4 — Contenu opérationnel et charge
Biens, quantités, unités, lieux, fenêtres souhaitées. Distinguer souhaité / planifié / réel. Calcul de poids seulement si unités compatibles ; sinon total déclaré identifié.
- 100 × 20 kg = 2 000 kg ; 100 unités sans poids = aucun tonnage inventé.
- Fin < début refusée ; trajet traversant minuit accepté si dates cohérentes.
- Modification de charge après affectation → recontrôle de la compatibilité.

### F5 — Vente minimale et livraison liée
Commande simple (client, lignes, quantités, montants) → création/liaison de sa mission de livraison. Lien consultable dans les deux sens. Affectation ≠ livrée ≠ payée.
- Relancer « créer la livraison » retrouve la mission existante (pas de doublon).
- Le montant de la vente n'est pas facturé une seconde fois par la mission.
- Affectation ne change pas le statut commercial.

### F6 — Planning et affectation
Vue commune A et B : période, ressources, état, conflits. Évaluer véhicule + chauffeur sur toute la période (chargement, trajet, déchargement, retour). Affectation confirmée après contrôle ; réaffectation conserve l'historique ; échec = ancienne affectation intacte.
- Indisponibilité ou mission sur un sous-intervalle → période incompatible.
- Chevauchement : [10h,12h[ et [11h,13h[ incompatibles ; [12h,13h[ adjacent.
- Deux confirmations concurrentes incompatibles ne peuvent pas toutes deux aboutir.
- Ressource indisponible (panne, absence) : enregistrable même si elle contredit une mission ; missions impactées listées, réaffectation manuelle.

### F7 — Cycle de vie de la mission
États proposés : **À planifier → Planifiée → En cours → Arrivée → (En attente →) En déchargement → Terminée**, ou **Annulée**. Retard et incident sont des événements, pas des états. Chaque changement crée un événement consultable (auteur, heure de saisie, heure réelle).
- À planifier → Terminée sans justification refusé ; départ sans ressources confirmées refusé.
- Arrivée sans attente → déchargement direct ; attente jamais imposée.
- Correction après clôture conserve l'état antérieur.

### F8 — Déchargement et temps
Responsabilités et conditions convenues, fenêtre prévue, dates-heures réelles (arrivée, début, fin). Attente = début − arrivée ; durée = fin − début, seulement si bornes connues. Prolongation → recontrôle des missions suivantes.
- Arrivée 9h15, début 9h30, fin 10h15 → attente 15 min, déchargement 45 min.
- Début inconnu → attente/durée indisponibles, pas zéro.
- Aucun montant dû créé automatiquement par une attente.

### F9 — Suivi financier
Une dette unique par dossier, composantes vente/transport distinguées. Cycle paiement : **annoncé → enregistré en attente → encaissement confirmé** (ou rejet/annulation motivé ; correction par contre-mouvement). Un paiement saisi n'est pas confirmé du seul fait de la saisie. Dépenses rattachées à une mission, avec catégorie, date, montant, référence.
- Vente 4 000 + transport 1 000 = dette 5 000 ; pas de seconde dette via la mission.
- Seuls les encaissements **confirmés** réduisent le solde.
- Solde = dette − encaissements confirmés + régularisations. Dépenses ≠ réduction de dette.
- Corriger un encaissement conserve l'original + mouvement lié.

### F10 — Consultation et recherche
Listes filtrées par référence, client, état, ressource, période ; critères combinés par ET. Afficher la dernière mise à jour (une info ancienne reste datée). Synthèse simple : missions à planifier, en cours, retards signalés, soldes autorisés.
- « Trois missions en retard signalé » correspond aux trois dossiers sous mêmes filtres.
- Utilisateur sans droit financier ne reçoit aucun montant.
- Résultat vide distingué d'une erreur technique.

## 5. Exigences non fonctionnelles (résumé)

| Exigence | Attendu |
|---|---|
| **Sécurité** | Mots de passe salés et hachés, jamais en clair ; secrets masqués dans journaux ; limitation des essais de connexion. |
| **Autorisation** | Vérifiée à chaque action, pas seulement dans l'UI ; refus par défaut ; séparation des entreprises appliquée aux liens, recherches, exports. |
| **Persistance** | Succès affiché seulement après enregistrement effectif ; échec → pas d'effet partiel ; issue incertaine vérifiée avant reprise. |
| **Erreurs** | Message compréhensible + référence ; saisie conservée ; pas de retentative automatique sans garantie d'absence de doublon. |
| **Validation** | Types, bornes, unités, liens vérifiés à l'action ; téléphone = texte ; montants exacts à la précision retenue. |
| **Audit** | Trace des changements critiques (droits, montants, affectations, états) avec auteur/date/avant-après/motif. |
| **Sauvegarde** | Copie documentée + test de restauration sur environnement séparé ; échec visible ; accès restreint. |
| **Ergonomie** | Tâches courantes réalisables sans assistance ; champ invalide localisé, autres valeurs préservées. |

## 6. Décisions à prendre (5)

| # | Question | Proposition |
|---|---|---|
| D1 | Une demande = combien de missions ? | **Une mission active par demande** en V1 (pas de fractionnement/groupage). |
| D2 | Qui confirme un encaissement ? | **Financier habilité uniquement** ; commercial peut saisir un « annoncé ». |
| D3 | Statuts de paiement | **Annoncé / En attente / Confirmé** (+ Rejeté/Annulé motivé). |
| D4 | Durée d'inactivité avant expiration de session | Valeur à fixer (proposition : 30 min). |
| D5 | Déploiement | **Un poste ou plusieurs postes partagés ?** → conditionne la concurrence et le stockage. |

## 7. Hors périmètre V1 (rappel)

Pas de GPS, mobile, notifications automatiques, paiement en ligne, comptabilité, stocks, exports multiples, pièces jointes. Une référence de justificatif suffit.

