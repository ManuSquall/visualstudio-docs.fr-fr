---
title: "Mode Allocations de m&#233;moire .NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.allocation"
helpviewer_keywords: 
  - "Allocations (mode)"
  - "rapports de performances, mode Allocation"
  - "rapports d'outils de profilage, Allocation (mode)"
  - "outils de profilage, Allocation (mode)"
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Allocations de m&#233;moire .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Allocations répertorie les types créés au cours de l'exécution du profilage.  Chaque type est le nœud racine d'une arborescence des appels qui affiche les chemins d'accès d'exécution de fonctions qui ont entraîné les allocations du type.  
  
 Les données d'une ligne de type affichent le nombre total d'objets du type créés lors de l'exécution du profilage et le nombre total d'octets alloué pour les objets de ce type.  Les valeurs inclusives et exclusives pour un type sont toujours les mêmes.  
  
-   Les valeurs inclusives sont pour les objets créés dans les instances de la fonction et ses fonctions enfants appelées par la fonction parent dans l'arborescence des appels.  
  
-   Les valeurs exclusives sont pour les objets créés directement par la fonction lorsqu'ils ont été appelés par la fonction parent.  Les objets créés dans les fonctions enfants ne sont pas inclus.  
  
 Les données d'une fonction affichent le nombre d'objets créés et le nombre d'octets alloués pour les objets du type parent.  
  
## Mise en surbrillance du chemin réactif d'exécution  
 Vous pouvez trouver le chemin d'exécution de l'arborescence des appels qui a créé le plus d'objets du type parent.  
  
-   Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le type ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom du type ou de la fonction alloué\(e\).|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient le type ou la fonction.|  
|**Chemin de module**|Chemin du module qui contient le type ou la fonction.|  
|**Source File**|Fichier source qui contient la définition du type ou de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette définition de type ou fonction dans le fichier source.|  
|**Niveau**|Indique si les données sont pour un type ou une fonction.|  
|**Allocations inclusives**|-   Pour une fonction, nombre total d'objets du type parent créés par la fonction.  Ce nombre inclut les objets créés dans les fonctions enfants.<br />-   Pour un type, nombre total d'instances de ce type créées.|  
|**Allocations inclusives %**|-   Pour une fonction, pourcentage de tous les objets créés lors de l'exécution du profilage qui étaient des allocations inclusives du type parent par la fonction.<br />-   Pour un type, pourcentage du nombre total d'objets créés lors de l'exécution du profilage qui étaient des instances du type.|  
|**Allocations exclusives**|-   Pour une fonction, nombre d'objets créés lorsque la fonction s'exécutait directement au haut de la pile des appels.  Ce nombre n'inclut pas les objets créés dans les fonctions enfants.<br />-   Pour un type, nombre total d'instances de ce type créées.|  
|**Allocations exclusives %**|-   Pour une fonction, pourcentage de tous les objets créés lors de l'exécution du profilage qui étaient des allocations exclusives du type parent par la fonction.<br />-   Pour un type, pourcentage du nombre total d'objets créés lors de l'exécution du profilage qui étaient des instances du type.|  
|**Octets inclusifs**|-   Pour une fonction, nombre total d'octets de mémoire alloués par la fonction pour les objets du type parent.  Ce nombre inclut la mémoire allouée par ses fonctions enfants.<br />-   Pour un type, nombre total d'octets alloués lors de l'exécution du profilage pour les instances du type.|  
|**Octets inclusifs %**|-   Pour une fonction, pourcentage de la mémoire allouée lors de l'exécution du profilage qui était des allocations inclusives du type parent par la fonction.<br />-   Pour un type, pourcentage de la mémoire allouée lors de l'exécution du profilage pour les instances du type.|  
|**Octets exclusifs**|-   Pour une fonction, nombre total d'octets de mémoire alloués par la fonction pour les objets du type parent.  Ce nombre n'inclut pas la mémoire allouée par ses fonctions enfants.<br />-   Pour un type, nombre total d'octets alloués lors de l'exécution du profilage pour les instances du type.|  
|**Octets exclusifs %**|-   Pour une fonction, pourcentage de la mémoire allouée lors de l'exécution du profilage qui était des allocations exclusives du type parent par la fonction.<br />-   Pour un type, pourcentage de la mémoire allouée lors de l'exécution du profilage pour les instances du type.|