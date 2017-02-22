---
title: "DA0005&#160;: Collections GC2 fr&#233;quentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0005&#160;: Collections GC2 fr&#233;quentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Id de la règle|DA0005|  
|Catégorie|Utilisation du .NET Framework|  
|Méthode de profilage|Mémoire .NET|  
|Message|De nombreux objets sont collectés dans un garbage collection gen2.|  
|Type de message|Avertissement|  
  
## Cause  
 Un nombre élevé d'objets mémoire .NET est libéré dans le garbage collection de 2e génération.  
  
## Description de la règle  
 Le CLR Microsoft .NET offre un mécanisme de gestion automatique de la mémoire qui utilise un garbage collector pour libérer la mémoire des objets que l'application n'utilise plus.  Le garbage collector est orienté génération, basé sur l'hypothèse que de nombreuses allocations ont une courte durée de vie.  Les variables locales, par exemple, doivent avoir une courte durée de vie.  Les objets nouvellement créés commencent à la génération 0 \(gen 0\),puis progressent jusqu'à la génération 1 lorsqu'ils survivent à une exécution de garbage collection et effectuent enfin une transition vers la génération 2 si l'application les utilise encore.  
  
 Les objets de la génération 0 sont collectés fréquemment et généralement de façon très efficace.  Les objets de la génération 1 sont collectés moins fréquemment et de façon moins efficace.  Enfin, les objets à longue durée de vie dans la génération 2 doivent être collectés moins fréquemment encore.  La collection de génération 2, qui est une exécution de garbage collection complet, est également l'opération la plus coûteuse.  
  
 Cette règle se déclenche lorsque proportionnellement trop de garbage collections de génération 2 se sont produits.  Si trop d'objets relativement éphémères subsistent de la collection de génération 1 mais sont ensuite capables d'être collectés dans une collection complète de génération 2, le coût de gestion de la mémoire peut facilement devenir excessif.  Pour plus d'informations, consultez la publication [Crise de la cinquantaine \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177835) dans Rico Mariani's Performance Tidbits sur le site Web MSDN.  
  
## Comment examiner un avertissement  
 Examinez les rapports [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md) pour comprendre le modèle d'allocation de mémoire de l'application.  Utilisez l'[Mode Durée de vie de l'objet](../profiling/object-lifetime-view.md) pour déterminer quels sont les objets de données du programme qui survivent dans la génération 2 et qui sont ensuite récupérés.  Utilisez l'[Mode Allocations](../profiling/dotnet-memory-allocations-view.md) pour déterminer le chemin d'exécution ayant entraîné ces allocations.  
  
 Pour plus d'informations sur l'amélioration des performances d'une opération garbage collection, consultez [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) \(page éventuellement en anglais\) sur le site Web Microsoft.  Pour plus d'informations sur la surcharge d'une opération garbage collection automatique, consultez [Le tas des objets volumineux dévoilé](http://go.microsoft.com/fwlink/?LinkId=177836).