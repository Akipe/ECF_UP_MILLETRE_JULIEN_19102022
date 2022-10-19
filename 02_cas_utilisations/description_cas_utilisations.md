A Bicyclettre - Cas d'utilisations
======

ECF_UP_MILLETRE_JULIEN_19102022

## Liste des cas d'utilisation

- Louer un vélo
- Connaitre le taux de remplissage de vélos des stations
- Accéder au Système depuis une borne
- Vérifier l'état d'une borne
- Définir une intervention
- Gérer le compte d'un Utilisateur

## Description

### ***Louer un vélo***
Un ***Utilisateur*** peut payer une location de vélo grace à un compte bancaire connecté au ***Système Bancaire** depuis une borne, qui lui permet de prendre le vélo et de le déposer ensuite à une autre borne. Il devra réaliser un prélévement initial avant de louer le vélo pour être sûr que l'utilisateur sera autorisé à régler se location une fois terminé.

### ***Connaitre le taux de remplissage de vélos des stations***
Le ***Service Dispatcher*** peut connaitre le nombre de bornes libres (c'est à dire sans vélo) et occupés. Il peut savoir s'il y a trop ou pas assez de vélo dans toutes les stations.

### ***Accéder au Système depuis une borne***
Le ***Service Dispatcher*** peut accéder depuis n'importe quel borne à des fonctionnalités de maintenance du ***Système***. Par exemple il peut *connaitre le taux de remplissage de vélos des stations*.

### ***Vérifier l'état d'une borne***
Le ***Service Client*** peut vérifier si une borne est libre ou non, en plus de vérifier si elle est défaillante.

### ***Définir une intervention***
Le ***Service Client*** peut faire une demande d'intérvention auprès du ***Service Technique*** de l'entreprise pour réparer une borne suite à la découverte d'une défaillance.

### ***Gérer le compte d'un Utilisateur***
Le ***Service Client*** peut vérifier si un utilisateur est en cours le location de vélo, ainsi que de changer cet etat pour pouvoir ré-autoriser un ***Utilisateur*** à faire une nouvelle location de vélo.
