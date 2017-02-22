---
title: "DA0021&#160;: Taux &#233;lev&#233; de garbage collection Gen 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0021&#160;: Taux &#233;lev&#233; de garbage collection Gen 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0021|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Tous|  
|Message|Taux relativement élevé de garbage collection Gen 1.  Si, par conception, la plupart des structures de données de votre programme sont allouées et persistent pour longtemps, cela ne pose pas de problème.  Cependant, si ce comportement est involontaire, votre application peut épingler des objets.  Si vous n'êtes pas sûr, vous pouvez regrouper les données d'allocation de mémoire .NET et les informations de durée de vie des objets afin de comprendre le modèle d'allocation de mémoire utilisé par votre application.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Cause  
 Les données des performances système collectées pendant le profilage indiquent qu'une proportion significative de mémoire pour les objets .NET Framework a été libérée pendant la génération 1 du garbage collection comparée à la collecte de données de la génération 0.  
  
## Description de la règle  
 Le CLR \(Common Language Runtime\) Microsoft.NET offre un mécanisme de gestion automatique de la mémoire qui utilise un garbage collector pour libérer la mémoire des objets que l'application n'utilise plus.  Le garbage collector est orienté génération, basé sur l'hypothèse que de nombreuses allocations ont une courte durée de vie.  Les variables locales, par exemple, doivent avoir une courte durée de vie.  Les objets nouvellement créés commencent à la génération 0 \(gen 0\),puis progressent jusqu'à la génération 1 lorsqu'ils survivent à une exécution de garbage collection et effectuent enfin une transition vers la génération 2 si l'application les utilise encore.  
  
 Les objets de la génération 0 sont collectés fréquemment et généralement de façon très efficace.  Les objets de la génération 1 sont collectés moins fréquemment et de façon moins efficace.  Enfin, les objets à longue durée de vie dans la génération 2 doivent être collectés moins fréquemment encore.  La collection de génération 2, qui est une exécution de garbage collection complet, est également l'opération la plus coûteuse.  
  
 Cette règle se déclenche lorsque proportionnellement trop de garbage collections de génération 1 se sont produits.  Si trop d'objets relativement éphémères subsistent de la collection de génération 0 mais sont ensuite capables d'être collectés dans une collection de génération 1, le coût de gestion de la mémoire peut devenir excessif.  Pour plus d'informations, consultez la publication [Crise de la cinquantaine \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177835) dans Rico Mariani's Performance Tidbits sur le site Web MSDN.  
  
## Comment examiner un avertissement  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à l'[Marques, vue](../profiling/marks-view.md) des données de profilage.  Recherchez les colonnes **Mémoire CLR .NET\\Nombre de collections de la génération 0** et **Mémoire CLR .NET\\Nombre de collections de la génération 1**.  Déterminez s'il existe des phases spécifiques de l'exécution du programme où l'opération garbage collection se produit plus fréquemment.  Comparez ces valeurs à la colonne **% Temps dans le GC** pour déterminer si le modèle des allocations de mémoire managée provoque une surcharge de gestion de mémoire excessive.  
  
 Pour comprendre le modèle d'utilisation de la mémoire managée de l'application, exécutez un nouveau profilage à l'aide d'un profil d'allocation de mémoire .NET et demandez des mesures de Durée de vie des objets.  
  
 Pour plus d'informations sur l'amélioration des performances d'une opération garbage collection, consultez [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) \(page éventuellement en anglais\) sur le site Web Microsoft.  Pour plus d'informations sur la surcharge d'une opération garbage collection automatique, consultez [Le tas des objets volumineux dévoilé](http://go.microsoft.com/fwlink/?LinkId=177836).