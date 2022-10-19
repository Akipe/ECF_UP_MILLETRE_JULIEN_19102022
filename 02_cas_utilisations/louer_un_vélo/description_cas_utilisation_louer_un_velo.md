A Bicyclettre - Cas d'utilisations
======

ECF_UP_MILLETRE_JULIEN_19102022

## Description

Un ***Utilisateur*** peut payer une location de vélo grace à un compte bancaire connecté au ***Système Bancaire*** depuis une borne, qui lui permet de prendre le vélo et de le déposer ensuite à une autre borne.

## Acteurs

L'acteur principal pour ce cas d'utilisation est un ***Utilisateur***.

Il y a un acteur secondaire, qui est le ***Système Bancaire***.

Il peut également en fonction des scénarios exceptionnels avoir d'autres acteurs secondaires : le ***Service Client*** et le ***Service Technique***.

## Pré-condition
Un ***Utilisateur*** dispose d'une carte.

## Post-condition
L'***Utilisateur*** à rendu le vélo loué et n'a pas à régler financierement la location. 

## Scénarios

### Scénario nominal

1. Un Utilisateur rentre sa carte bancaire dans le lecteur de la borne.
1. Le Système vérifie qu'il y a bien un vélo à la borne.
1. Le Système reconnait la carte bancaire.
1. Le Système vérifie si cette carte bancaire est autorisé.
1. Le Système demande à l'Utilisateur de rentrer son code de carte bancaire.
1. L'Utilisateur rentre son code de carte bancaire.
1. Le Système valide le code de la carte bancaire.
1. Le Système contacte Système Bancaire pour demande un pré-payement.
1. Le Système Bancaire valide l'opération.
1. Le Système débloque la borne.
1. L'Utilisateur prend le vélo.
1. L'Utilisateur dépose le vélo à une borne.
1. Le Système bloque le vélo.
1. Le Système calcul la somme d'argent à récupérer en fonction du temps d'utilisation du vélo.
1. Le Système contacte Système Bancaire pour valider le pré-payement avec le somme d'argent calculé.
1. Le Système Bancaire valide l'opération.

### Scénarios alternatifs

#### A1 - La carte bancaire n'est pas reconnu
Remplacement de l'étape 3 :

1. Le Système ne reconnait pas la carte bancaire de l'Utilisateur.
1. Le Système informe l'utilisateur qu'une carte bancaire est nécessaire.

Reprise du scénario nominal à l'étape 1.

#### A2 - Le code de la carte bancaire est incorrecte
Remplacement de l'étape 6 :

1. L'Utilisateur rentre un mauvais code de carte bancaire.
1. Le Système invalide le code de la carte bancaire.
1. Le Système informe l'Utilisateur que le code bancaire est invalide.

Reprise du scénario nominal à l'étape 5.

#### A3 - Le prélévement bancaire échoue
Remplacement de l'étape 16 :

1. Le Système Bancaire ne répond pas.
1. Le Système attend une heure.

Reprise du scénario nominal à l'étape 15.

### Scénarios exceptionnels

#### E1 - Il n'y a pas de vélo
Remplacement de l'étape 2 :

1. Le Système ne trouve pas de vélo à cette borne.
1. Le Systeme informe à l'utilisateur qu'il n'y a pas de vélo.

#### E2 - L'opération bancaire a été refusé
Remplacement de l'étape 9 :

1. Le Système Bancaire ne valide pas l'opération de pré-prélévement.
1. Le Système informe que l'opération bancaire à échoué.

#### E3 - La borne n'arrive pas à débloquer le vélo
Remplacement de l'étape 10 :

1. Le Système n'arrive pas à débloqué le vélo.
1. Le Système annule l'opération bancaire.
1. Le Système informe l'utilisateur d'une erreur de déblocage.
1. Le Système envoie une notification d'intervention au Service Technique. 

#### E4 - Le vélo est laissé à la borne débloqué après 10 secondes
Remplacement de l'étape 11 :

1. L'Utilisateur ne prend pas le vélo après 10 secondes.
1. Le Système bloque le vélo.
1. Le Système annule l'opération bancaire.

#### E5 - Le vélo n'est pas déposé en borne après 24 heures.
Remplacement de l'étape 12 :

1. L'Utilisateur ne rend pas le vélo après 24 heures de location.
1. Le Système informe le Service Client d'un vélo manquant avec les informations bancaires de l'Utilisateur.

#### E6 - Le prélévement bancaire à échoué de trop nombre fois.
A partir de 3 fois pour le scénario alternatif A3 (étape A3.1) :

1. Enregistrement de la carte bancaire comme Utilisateur n'ayant pas régler la location.
1. Le Système notifie le Service Client que l'Utilisateur n'a pas réglé sa location


#### E7 - Annulation
De l'étape 4 à l'étape 7 :

1. L'Utilisateur utilise la fonction "Annulation" de la borne.
1. Le Système confirme l'annulation.

#### E8 - Location déjà en cours 
Remplace l'étape 4 :

1. Le Système informe l'Utilisateur qu'une location est déjà en cours.

#### E9 - Location non autorisé car non payement de l'ancienne location
Remplace l'étape 4 :

1. Le Système informe l'Utilisateur qu'il ne pourra pas louer de vélo tant qu'il n'aura pas régler la dernière location, et qu'il doit contacter le Service Client.
