---
title: "DA0505&#160;: nombre moyen d&#39;octets priv&#233;s allou&#233;s pour le processus en cours de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0505"
  - "vs.performance.rules.DA0505"
  - "vs.performance.505"
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0505&#160;: nombre moyen d&#39;octets priv&#233;s allou&#233;s pour le processus en cours de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0505|  
|Catégorie|Gestion des ressources|  
|Méthode de profilage|Tous|  
|Message|Ces informations ont été rassemblées à titre d'information uniquement.  Le compteur Traiter les octets privés mesure la mémoire virtuelle allouée par le processus que vous profilez qui ne peut pas être partagée avec d'autres processus.  La valeur signalée correspond à la moyenne pour tous les intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Description de la règle  
 Ce message signale la quantité moyenne de mémoire virtuelle actuellement allouée en octets par le processus \(octets privés\).  Octets privés représente les emplacements de mémoire virtuelle alloués par le processus et accessibles uniquement par les threads en cours d'exécution dans le processus.  
  
 Pour les processus 32 bits qui s'exécutent sur un ordinateur 32 bits, la limite supérieure de la partie privée de l'espace d'adressage du processus est 2 Go.  À l'aide du commutateur [\/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini, les processus 32 bits peuvent acquérir jusqu'à 3 Go de mémoire virtuelle.  Un processus 32 bits qui s'exécute sur un ordinateur 64 bits peut acquérir jusqu'à 4 Go de mémoire virtuelle privée.  
  
 Un processus 64 bits qui s'exécute sur un ordinateur 64 bits peut acquérir jusqu'à 8 To de mémoire virtuelle privée.  
  
 La valeur signalée est la moyenne de tous les intervalles de mesure dans lesquels le processus profilé était actif.  
  
 Pour plus d'informations sur les espaces d'adresses de processus, consultez [Espace d'adresse virtuelle \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177832) dans la documentation de Windows Memory Management.  
  
## Comment utiliser des données de règle  
 Utilisez la valeur signalée pour comparer les performances de différentes versions du programme ou pour comprendre les performances de l'application selon des scénarios de profilage différents.