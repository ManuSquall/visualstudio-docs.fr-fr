---
title: "DA0010&#160;: GetHashCode co&#251;teux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0010&#160;: GetHashCode co&#251;teux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0010|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Mémoire .NET|  
|Message|Les fonctions GetHashCode ne doivent pas être coûteuses et ne doivent pas allouer de mémoire.  Réduisez la complexité de la fonction de code de hachage si possible.|  
|Type de message|Avertissement|  
  
## Cause  
 Les appels à la méthode GetHashCode du type représentent une proportion significative des données de profilage ou la méthode alloue de la mémoire.  
  
## Description de la règle  
 Le hachage est une technique pour la recherche rapide d'un élément particulier dans une grande collection.  Étant donné que les tables de hachage peuvent être très grandes et devoir prendre en charge des taux très élevés d'accès, les tables de hachage doivent être extrêmement efficaces.  Une conséquence de cette spécification est que les méthodes GetHashCode dans le .NET Framework ne doivent pas allouer de mémoire.  L'allocation de la mémoire augmente la charge sur le garbage collector et expose la méthode à des délais potentiels s'il devient nécessaire d'exécuter le garbage collection fonctionné en raison de la demande d'allocation.  
  
## Comment corriger les violations  
 Réduisez la complexité de la méthode.