---
title: "DA0506&#160;: nombre maximal d&#39;octets priv&#233;s allou&#233;s pour le processus en cours de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0506"
  - "vs.performance.DA0506"
  - "vs.performance.506"
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0506&#160;: nombre maximal d&#39;octets priv&#233;s allou&#233;s pour le processus en cours de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0506|  
|Catégorie|Analyse de ressource|  
|Méthode de profilage|Tous|  
|Message|Ces informations ont été rassemblées à titre d'information uniquement.  Le compteur Traiter les octets privés mesure la mémoire virtuelle allouée par le processus que vous profilez qui ne peut pas être partagée avec d'autres processus.  La valeur signalée est la valeur maximale observée parmi tous les intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Description de la règle  
 Ce message signale la quantité maximale de mémoire virtuelle actuellement allouée en octets par le processus \(octets privés\).  Octets privés représente les emplacements de mémoire virtuelle alloués par le processus et accessibles uniquement par les threads en cours d'exécution dans le processus.  
  
 Pour les processus 32 bits qui s'exécutent sur un ordinateur 32 bits, la limite supérieure de la partie privée de l'espace d'adressage du processus est 2 Go.  À l'aide du commutateur [\/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini, les processus 32 bits peuvent acquérir jusqu'à 3 Go de mémoire virtuelle.  Un processus 32 bits qui s'exécute sur un ordinateur 64 bits peut acquérir jusqu'à 4 Go de mémoire virtuelle privée.  
  
 Un processus 64 bits qui s'exécute sur un ordinateur 64 bits peut acquérir jusqu'à 8 To de mémoire virtuelle privée.  
  
 La valeur signalée est la valeur maximale de tous les intervalles de mesure dans lesquels le processus profilé était actif.  
  
 Pour plus d'informations sur les espaces d'adresses de processus, consultez [Espace d'adresse virtuelle \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177832) dans la documentation de Windows Memory Management.  
  
## Comment utiliser des données de règle  
 Utilisez la valeur signalée pour comparer les performances de différentes versions du programme ou pour comprendre les performances de l'application selon des scénarios de profilage différents.  
  
 Une valeur maximale d'octets privés de processus qui approche de la limite architecturale de taille maximale d'espace d'adressage de processus peut mener à des exceptions de mémoire insuffisante.  Pour plus d'informations, consultez [Analyser des problèmes de mémoire](http://go.microsoft.com/fwlink/?LinkID=177833) dans le magazine MSDN.