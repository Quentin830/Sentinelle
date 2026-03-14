# Sentinelle

Présentation du projet : 

Ce projet consiste en la conception et la fabrication d'un robot tout-terrain et amphibie dédié à la surveillance. Capable de se déplacer sur terre grâce à un système de chenilles et de naviguer sur l'eau via une coque de bateau intégrée, ce robot combine robotique mobile, mécanique, électronique et intelligence artificielle.

Sa particularité réside dans son système de suivi autonome : grâce à une caméra embarquée et une carte NVIDIA Jetson, le robot est capable de détecter et de suivre un humain de manière autonome. S'il perd sa cible ou n'en détecte aucune, il bascule automatiquement en mode radiocommandé (RC) classique.
 Architecture Système : 

Le système repose sur une architecture maître/esclave pour séparer l'intelligence du contrôle bas niveau :

    Haut niveau (NVIDIA Jetson) : Traitement de l'image (Computer Vision), détection d'humains, prise de décision.

    Bas niveau (Arduino) : Réception des ordres de la Jetson ou de la radiocommande, contrôle des drivers moteurs et gestion des capteurs de sécurité.

 Grandes étapes de la construction :
1. Conception & Modélisation

    Étude des besoins : Contraintes d'un système amphibie (légèreté, flottabilité, centre de gravité) et de surveillance (champ de vision de la caméra).

    Choix des matériaux : Matériaux étanches pour la coque et robustes pour le châssis terrestre.

    Modélisation 3D (Fusion 360) : * Conception de la coque et du système de chenilles.

        Création de supports sur mesure pour l'électronique (Jetson, Arduino, Caméra) incluant la dissipation thermique pour la Jetson.

2. Fabrication & Assemblage

    Impression 3D / Découpe : Fabrication des pièces mécaniques (châssis, supports internes, fixations moteurs).

    Étanchéification : Traitement de la coque et isolation stricte des compartiments électroniques (les cartes NVIDIA étant très sensibles à l'humidité).

    Intégration mécanique : Montage du système de chenilles et des propulseurs aquatiques.

3. Électronique & Alimentation

    Motorisation : Sélection et intégration des moteurs terrestres et des propulseurs aquatiques.

    Cerveau & Contrôle : * Carte de calcul IA : NVIDIA Jetson.

        Carte de contrôle bas niveau : Arduino.

    Capteurs : Intégration de la caméra de vision au centre du dispositif.

    Énergie : * Batteries LiPo à haute capacité.

        Gestion de l'alimentation (Régulateurs/BEC) pour fournir les bonnes tensions à la Jetson (qui consomme beaucoup) et à l'Arduino.

    Câblage : Soudure, routage propre et étanchéité des passages de câbles vers l'extérieur.

4. Programmation & Intelligence Artificielle

    Vision par ordinateur (Jetson) : Implémentation d'un modèle de reconnaissance d'objets pour la détection spécifique des humains utilisant le CNN ResNet.

    Logique de contrôle (Jetson -> Arduino) : Mise en place d'une communication série pour envoyer les commandes de direction et de vitesse de l'IA vers les moteurs.

    Machine à états (Modes de fonctionnement) :

        Mode Autonome : Détection de l'humain, et suivi dynamique.

        Mode Manuel (RC) : Prise de contrôle via la télécommande si aucune cible n'est détectée ou en cas de reprise en main manuelle.

        Gestion des environnements : Adaptation de la propulsion selon le milieu (Terrestre vs Aquatique).
