---
title: "Onglet M&#233;moire de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés du processus pour Windows NT"
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet M&#233;moire de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Mémoire** pour voir la façon dont un processus utilise la mémoire.  Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus sur une fenêtre [Vue Processus](../debugger/processes-view.md).  Sélectionnez n'importe quel nœud de processus dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Mémoire** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Octets virtuels**|Taille actuelle \(en octets\) de l'espace d'adressage virtuel utilisé par le processus.  L'utilisation d'un espace d'adressage virtuel n'implique pas nécessairement l'utilisation correspondante de pages mémoire principale ou sur disque.  Toutefois, l'espace virtuel a une limite, et son utilisation excessive peut restreindre la capacité du processus à charger les bibliothèques.|  
|**Nombre d'octets virtuels maximal**|Nombre maximal d'octets de l'espace d'adressage virtuel que le processus a utilisé à un moment donné.|  
|**Jeu de travail**|Jeu de pages mémoire utilisées récemment par les threads du processus.  Si la mémoire disponible de l'ordinateur est supérieure à un certain seuil, les pages sont laissées dans le jeu de travail d'un processus même si elles ne sont pas en cours d'utilisation.  Lorsque la mémoire disponible chute en dessous d'un certain seuil, les pages sont supprimées du jeu de travail.  Si nécessaire, elles sont ramenées après un défaut de page logiciel dans le jeu de travail avant de quitter la mémoire principale.|  
|**Nombre de jeux de travail maximal**|Nombre maximal de pages dans le jeu de travail de ce processus à tout moment.|  
|**Octets regroupés paginés**|Taille actuelle de réserve paginée que le processus a allouée.  La réserve paginée est une zone de mémoire système où les composants du système d'exploitation occupent de l'espace lors de l'accomplissement de leurs tâches attitrées.  Les pages de la réserve paginée peuvent être paginées dans le fichier d'échange lorsque le système n'y a pas accès pendant des périodes prolongées.|  
|**Octets regroupés non paginés**|Nombre actuel d'octets de la réserve non paginée alloués par le processus.  La réserve non paginée est une zone de mémoire système où l'espace est occupé par les composants du système d'exploitation lors de l'accomplissement de leurs tâches attitrées.  Les pages de la réserve non paginée ne peuvent pas être paginées dans le fichier d'échange ; elles restent en mémoire principale tant qu'elles sont allouées.|  
|**Octets privés**|Nombre actuel d'octets alloués par ce processus et qui ne peuvent pas être partagés avec d'autres processus.|  
|**Octets libres**|Total de l'espace d'adressage virtuel inutilisé de ce processus.|  
|**Octets réservés**|Quantité totale de mémoire virtuelle réservée à une utilisation ultérieure par ce processus.|  
|**Octets d'image libres**|Quantité d'espace d'adressage virtuel qui n'est pas utilisée ou réservée par des images dans ce processus.|  
|**Octets d'image réservés**|Somme de toute la mémoire virtuelle réservée par l'exécution d'images dans ce processus.|