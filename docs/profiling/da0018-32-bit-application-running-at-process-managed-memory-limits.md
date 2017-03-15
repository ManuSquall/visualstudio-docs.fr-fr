---
title: "DA0018&#160;: application 32&#160;bits s&#39;ex&#233;cutant aux limites de la m&#233;moire manag&#233;e du processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.18"
  - "vs.performance.DA0018"
  - "vs.performance.rules.DA0018"
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0018&#160;: application 32&#160;bits s&#39;ex&#233;cutant aux limites de la m&#233;moire manag&#233;e du processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0018|  
|Catégorie|Utilisation des outils de profilage|  
|Méthode de profilage|Échantillonnage|  
|Message|Les allocations de mémoire managée sont proches de la limite pour un processus 32 bits.  Votre application peut être liée à la mémoire.|  
|Type de règle|Avertissement|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Cause  
 Les données système collectées pendant l'exécution du profilage indiquent que les tas de mémoire .NET Framework ont approché de la taille maximale autorisée pour les tas managés dans un processus 32 bits.  Cette taille maximale est une valeur par défaut.  Elle est basée sur la quantité totale de l'espace d'adressage du processus qui peut être allouée pour les octets privés.  La valeur signalée représente la valeur maximale observée des tas pendant que le processus profilé était actif.  Considérez un nouveau profilage à l'aide de la méthode des profils de mémoire .NET et une optimisation de l'utilisation des ressources managées par l'application.  
  
 Lorsque la taille des tas managés approche de la limite par défaut, le processus de garbage collection automatique devra peut\-être être plus fréquemment appelé.  Cela augmente la surcharge de gestion de la mémoire.  
  
 La règle se déclenche seulement pour les applications 32 bits qui s'exécutent sur des ordinateurs 32 bits.  
  
## Description de la règle  
 Le CLR \(Common Language Runtime\) Microsoft.NET offre un mécanisme de gestion automatique de la mémoire qui utilise un garbage collector pour libérer la mémoire des objets que l'application n'utilise plus.  Le garbage collector est orienté génération, basé sur l'hypothèse que de nombreuses allocations ont une courte durée de vie.  Les variables locales, par exemple, doivent avoir une courte durée de vie.  Les objets nouvellement créés commencent à la génération 0 \(gen 0\),puis progressent jusqu'à la génération 1 lorsqu'ils survivent à une exécution de garbage collection et effectuent enfin une transition vers la génération 2 si l'application les utilise encore.  
  
 Objets managés supérieurs à 85 Ko sont alloués sur le segment d'objets volumineux, où ils sont soumis au nettoyage et à compression moins fréquents de plus petits objets. des objets sont gérés séparément car elle suppose qu'ils sont plus persistants comme combiner les objets persistants et les avec plusieurs petits objets souvent alloués peut produire une fragmentation de mauvais\- conversion du segment.  
  
 Lorsque la taille totale des tas managés approche de la limite par défaut, la surcharge de gestion de la mémoire augmente généralement jusqu'à une possible affectation de la réactivité et de l'extensibilité de l'application.  
  
## Comment examiner un avertissement  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à l'affichage [Marques](../profiling/marks-view.md).  Recherchez les colonnes **Mémoire CLR .NET\\Nombre d'octets dans tous les tas** et **Nombre total d'octets validés**.  Déterminez s'il existe des phases spécifiques d'exécution du programme où l'allocation de mémoire managée est plus importante que d'autres phases.  Comparez les valeurs de la colonne **Nombre d'octets dans tous les tas** au taux de garbage collection signalé dans les colonnes **Mémoire CLR .NET\\Nombre de collections de la génération 0**, **Mémoire CLR .NET\\Nombre de collections de la génération 1** et **Mémoire CLR .NET\\Nombre de collections de la génération 2** pour déterminer si le modèle des allocations de mémoire managée affecte le taux de garbage collection.  
  
 Dans une application .NET Framework, le CLR limite la taille totale des tas managés à légèrement moins de la moitié de la taille maximale de la partie de zone privée d'un espace d'adressage de processus.  Pour les processus 32 bits qui s'exécutent sur un ordinateur 32 bits, 2 Go représente la limite supérieure de la partie privée de l'espace d'adressage du processus.  Lorsque la taille totale des tas managés commence à approcher de sa limite par défaut, la surcharge de gestion de la mémoire peut augmenter et la performance de l'application peut diminuer.  
  
 Si la surcharge excessive de la mémoire managée pose un problème, considérez l'une ou l'autre de ces options :  
  
-   optimisation de l'utilisation de l'application de ressources mémoire managées  
  
     ou  
  
-   prise de mesures pour soulager les contraintes architecturales de taille maximale de mémoire virtuelle pour un processus 32 bits  
  
 Pour optimiser l'utilisation de l'application de ressources mémoire managées, rassemblez les données d'allocation de mémoire managée dans une exécution de profilage d'Allocation de mémoire .NET.  Examinez les rapports [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md) pour comprendre le modèle d'allocation de mémoire de l'application.  
  
 Utilisez le [Mode Durée de vie de l'objet](../profiling/object-lifetime-view.md) pour déterminer quels sont les objets de données du programme qui survivent dans la génération et qui sont ensuite libérés.  
  
 Utilisez l'[Mode Allocations](../profiling/dotnet-memory-allocations-view.md) pour déterminer le chemin d'exécution ayant entraîné ces allocations.  
  
 Pour plus d'informations sur l'amélioration des performances du garbage collection, consultez l'article technique du .NET Framework : [Notions de base et conseils de performance relatifs au Garbage Collector \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177946) sur le site MSDN.  
  
 Pour un assouplissement des contraintes architecturales de mémoire virtuelle sur la taille de la partie privée d'un espace d'adressage de processus, essayez d'exécuter ce processus 32 bits sur un ordinateur 64 bits.  Un processus 32 bits sur un ordinateur 64 bits peut acquérir jusqu'à 4 Go de mémoire virtuelle privée.  
  
 Un processus 64 bits exécuté sur un ordinateur 64 bits peut acquérir jusqu'à 8 To de mémoire virtuelle privée.  Envisagez de re\-compiler l'application pour une exécution en tant qu'application 64 bits native.  Cette règle est fournie uniquement à titre d'information et peut ne pas exiger d'action corrective.