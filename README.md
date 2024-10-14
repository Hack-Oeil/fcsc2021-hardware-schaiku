# FCSC 2021 Revaulting

Un équipement embarqué, une tablette, comportant un système d'échanges sécurisés avec un serveur 
de données vient d'être analysé par un de nos apprentis en canaux auxiliaires.

Pour authentifier le serveur, un système de défi-response est implémenté comme défense en profondeur. 
Plus exactement, ce système se compose des étapes suivantes. Le serveur envoie un défi **P**  
(un bloc aléatoire de 128 bits) à la tablette. 

Elle calcule un chiffré **C** à partir de **P** et une clé secrète **K** (partagée entre la tablette et le serveur) :

<code>C = AES128-ECB(K, P)</code>
et renvoie C au serveur pour s'authentifier. (Les même étapes étapes sont réalisées dans l'autre sens pour une authentification mutuelle).

En parallèle du chiffrement, la tablette affiche une image sur l'écran. Notre collègue s'est apercu que des interférences apparaissaient sur une partie de l'image au moment de ce calcul.

Arriverez-vous à retrouver la clé à partir de ces potentielles fuites d'information ?

Pour cela, il vous a préparé un PNG animé (**SCHaiku.png**) montrant l'image de référence et celles correspondant à différents chiffrements. 
La liste ordonnée des défis correspondants à chacune des images parasitées y est associée (**challenges.txt**).

**Information technique complémentaire** : l'affichage est effectué par blocs 
élémentaires de 4 pixels. La synchronisation entre l'affichage des blocs élémentaires 
et le calcul cryptographique n'est pas parfaite : la seule chose dont on est sûr est 
que l'interférence n'a lieu que sur exactement un pixel parmi les 4 d'un bloc.

Le flag est obtenu en retrouvant le défi correspondant à ce chiffré envoyé par le serveur : 
<code>d048821b99bca6758115e7a403bff427</code>.

Auteur : Guena

Origine : [SCHaiku](https://hackropole.fr/fr/challenges/hardware/fcsc2021-hardware-schaiku/)



-----------

## Installation manuel
Vous n'utilisez pas l'application **les CTFs de Cyrhades** ? C'est dommage !
Mais voici comment installer ce CTF manuellement :

> git clone https://github.com/Hack-Oeil/fcsc2021-hardware-schaiku.git

> cd fcsc2021-hardware-schaiku


-----------

## Sur le site officiel hackropole.fr
> https://hackropole.fr/fr/challenges/hardware/fcsc2021-hardware-schaiku/