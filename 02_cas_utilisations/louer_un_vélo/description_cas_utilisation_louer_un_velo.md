A Bicyclettre - Cas d'utilisations
======

ECF_UP_MILLETRE_JULIEN_19102022

## Description

Un ***Utilisateur*** peut louer un vélo en réalisant une demande d'autorisation prélévement bancaire (à l'aide du ***Système Bancaire***) depuis une borne. Il pourra ensuite prendre le vélo et de le déposer à une autre borne une fois son trajet terminé.

## Acteurs

L'acteur principal pour ce cas d'utilisation est un ***Utilisateur***.

Il y a un acteur secondaire, qui est le ***Système Bancaire***.

Il peut également y avoir, en fonction des scénarios exceptionnels, d'autres acteurs secondaires : le ***Service Client*** et le ***Service Technique***.

## Pré-condition
Un ***Utilisateur*** dispose d'une carte et la borne est prête à recevoir une carte.

## Post-condition
L'***Utilisateur*** à rendu le vélo et il a payé la location.

## Scénarios

### Scénario nominal

1. Un Utilisateur rentre sa carte bancaire dans le lecteur de la borne.
2. Le Système vérifie qu'il y a bien un vélo à la borne.
3. Le Système reconnait la carte bancaire.
4. Le Système vérifie si cette carte bancaire est autorisé.
5. Le Système demande à l'Utilisateur de rentrer son code de carte bancaire.
6. L'Utilisateur rentre son code de carte bancaire.
7. Le Système valide le code de la carte bancaire.
8. Le Système contacte Système Bancaire pour réaliser une demande initial de prélévement.
9. Le Système Bancaire valide l'opération.
10. Le Système débloque la borne et enregistre la date et l'heure de ce déblocage.
11. Le Système enregistre le carte bancaire comme "en cours de location".
12. L'Utilisateur prend le vélo.
13. L'Utilisateur dépose le vélo à une borne.
14. Le Système détecte qu'un vélo est dans la borne.
15. Le Système bloque le vélo et enregistre la date et l'heure du blocage.
16. Le Système retire carte bancaire des enregistrements "en cours de location".
17. Le Système calcul le prix total de la location en fonction du temps d'utilisation du vélo.
18. Le Système contacte Système Bancaire pour valider le prélévement avec le prix de la location.
19. Le Système Bancaire valide l'opération.

### Scénarios alternatifs

#### A1 - La carte bancaire n'est pas reconnu
Remplacement de l'étape 3 :

1. Le Système ne reconnait pas la carte bancaire de l'Utilisateur.
2. Le Système informe l'utilisateur qu'une carte bancaire est nécessaire.

Reprise du scénario nominal à l'étape 1.

#### A2 - Le code de la carte bancaire est incorrecte
Remplacement de l'étape 6 :

1. L'Utilisateur rentre un mauvais code de carte bancaire.
2. Le Système invalide le code de la carte bancaire.
3. Le Système informe l'Utilisateur que le code bancaire est invalide.

Reprise du scénario nominal à l'étape 5.

#### A3 - Le prélévement bancaire échoue
Remplacement de l'étape 19 :

1. Le Système Bancaire ne répond pas.
2. Le Système attend une heure.

Reprise du scénario nominal à l'étape 18.

#### A4 - Impossible de bloquer du vélo
Remplacement de l'étape 15 :

1. Le Système n'arrive pas à bloquer le vélo.
2. Le Système informe l'utilisateur qu'il doit reessayer de remettre le vélo.

Reprise du scénario nominal à l'étape 13.

### Scénarios exceptionnels

#### E1 - Il n'y a pas de vélo
Remplacement de l'étape 2 :

1. Le Système n'a pas de vélo bloqué à cette borne.
2. Le Systeme informe à l'utilisateur qu'il n'y a pas de vélo.

#### E2 - L'opération bancaire a été refusé
Remplacement de l'étape 9 :

1. Le Système Bancaire ne valide pas l'opération de prélévement initial.
2. Le Système informe que l'opération bancaire à échoué.

#### E3 - La borne n'arrive pas à débloquer le vélo
Remplacement de l'étape 10 :

1. Le Système n'arrive pas à débloqué le vélo.
2. Le Système annule l'opération bancaire.
3. Le Système informe l'utilisateur d'une erreur de déblocage.
4. Le Système envoie une notification d'intervention au Service Technique. 

#### E4 - Le vélo est laissé à la borne débloqué après 10 secondes
Remplacement de l'étape 12 :

1. L'Utilisateur ne prend pas le vélo après 10 secondes.
2. Le Système bloque le vélo.
3. Le Système annule l'opération bancaire.
4. Le Système retire la carte bancaire des enregistrement de carte "location en cours". 

#### E5 - Le vélo n'est pas déposé en borne après 24 heures.
Remplacement de l'étape 13 :

1. L'Utilisateur ne rend pas le vélo après 24 heures de location.
2. Le Système informe le Service Client d'un vélo manquant avec les informations bancaires de l'Utilisateur.
3. Le Système enregistre le numéro de carte bancaire en tant que location non réglé.

#### E6 - Le prélévement bancaire à échoué de trop nombre fois.
A partir de 3 fois pour le scénario alternatif A3 (étape A3.1) :

1. Enregistrement de la carte bancaire comme Utilisateur n'ayant pas régler la location.
2. Le Système notifie le Service Client que l'Utilisateur n'a pas réglé sa location
3. Le Système enregistre le numéro de carte bancaire en tant que location non réglé.


#### E7 - Annulation
De l'étape 4 à l'étape 7 :

1. L'Utilisateur utilise la fonction "Annulation" de la borne.
2. Le Système confirme l'annulation.

#### E8 - Location déjà en cours 
Remplace l'étape 4 :

1. Le Système detecte que la carte bancaire n'est pas autorisé car il y a déjà une location en cours.
2. Le Système informe l'Utilisateur qu'une location est déjà en cours.

#### E9 - Location non autorisé car non payement de l'ancienne location
Remplace l'étape 4 :

1. Le Système detecte que la carte bancaire n'est pas autorisé car le réglement de la dernière location n'a pu être réaliser.
2. Le Système informe l'Utilisateur qu'il ne pourra pas louer de vélo tant qu'il n'aura pas régler la dernière location, et qu'il doit contacter le Service Client.

#### E10 - Impossible de contacter le Système Bancaire
Remplace l'épte 9 :

1. Le Système Bancaire ne répond pas.
2. Le Système annule l'opération.
