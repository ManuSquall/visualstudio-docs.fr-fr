---
title: "Fonctionnement de l’allocation de m&#233;moire et des informations de dur&#233;e de vie des objets dans les outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage de la mémoire .NET (méthode)"
  - "Outils de profilage, méthode de mémoire .NET"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Fonctionnement de l’allocation de m&#233;moire et des informations de dur&#233;e de vie des objets dans les outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode de profilage *d'allocation de mémoire .NET*des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] collecte des informations sur la taille et le nombre d'objets qui ont été créés dans une allocation ou ont été détruits dans un garbage collection, ainsi que des informations supplémentaires à propos de la *pile des appels* de fonction lorsque l'événement s'est produit.  Une *pile des appels* est une structure dynamique qui stocke des informations sur les fonctions exécutées sur le processeur.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 La méthode de profilage d'allocation de mémoire .NET interrompt le processeur de l'ordinateur à chaque allocation d'un objet .NET Framework dans une application profilée.  Lorsque les données de durée de vie de l'objet sont également collectées, le profileur interrompt le processeur après chaque garbage collection .NET Framework.  Les données sont regroupées pour chaque fonction profilée et pour chaque type d'objet.  
  
## Données d'allocation  
 Lorsqu'un événement .memory se produit, le nombre total et la taille de tous les objets mémoire alloués ou détruits sont incrémentés.  
  
 Lorsqu'un événement d'allocation .memory se produit, le profileur incrémente le nombre d'échantillons pour chaque fonction sur la pile des appels.  Lors de la collecte des données, une seule fonction sur la pile des appels exécute actuellement le code dans son corps.  Les autres fonctions de la pile sont des parents dans la hiérarchie des appels de fonction qui attendent le retour des fonctions qu'ils ont appelées.  
  
-   Pour l'événement d'allocation, le profileur incrémente le nombre d'échantillons *exclusifs* de la fonction qui exécute actuellement ses instructions.  Étant donné qu'un échantillon exclusif fait également partie du nombre total d'échantillons \(*inclusifs*\) de la fonction, le nombre d'échantillons inclusifs de la fonction actuellement active est également incrémenté.  
  
-   Le profileur incrémente le nombre d'échantillons inclusifs de toutes les autres fonctions dans la pile des appels.  
  
## Données de durée de vie  
 Le garbage collector \(également appelé ramasse\-miettes\) du .NET Framework manage l'allocation et la libération de mémoire dans votre application.  Pour optimiser les performances du garbage collector, le tas managé est divisé en trois générations : 0, 1 et 2.  Le garbage collector du runtime stocke les nouveaux objets dans la génération 0.  Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.  
  
 Le garbage collector libère de la mémoire en libérant une génération entière d'objets.  Pour les objets créés par l'application profilée, le mode Durée de vie de l'objet affiche le nombre et la taille des objets, ainsi que la génération depuis laquelle ils sont libérés.