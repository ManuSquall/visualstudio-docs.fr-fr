---
title: 'DA0018 : Application 32 bits s’exécutant aux limites de la mémoire managée du processus | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6418a39d7e53a3edaa48b3cd003d35d95cba386e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773285"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018 : application 32 bits s'exécutant aux limites de la mémoire managée du processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID de règle | DA0018 |  
| Catégorie | Utilisation des outils de profilage |  
| Méthode de profilage | Échantillonnage |  
| Message | Géré les allocations de mémoire proche de la limite par défaut pour un processus 32 bits. Votre application peut être liée à la mémoire.|  
| Type de règle | Avertissement |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Les données système collectées pendant le profilage indiquent que les tas de mémoire .NET Framework approchent de la taille maximale autorisée pour les tas managés d’un processus 32 bits. Cette taille maximale est une valeur par défaut. Elle est basée sur la quantité totale d’espace d’adressage de processus pouvant être allouée pour les octets privés. La valeur signalée correspond à la valeur maximale des tas qui a été observée quand le processus profilé était actif. Effectuez un nouveau profilage à l’aide de la méthode de profilage de mémoire .NET et optimisez la manière dont l’application utilise les ressources managées.  
  
 Si la taille des tas managés approche de la limite définie par défaut, il se peut que vous deviez appeler plus fréquemment le processus de garbage collection automatique. La surcharge de la gestion de la mémoire sera ainsi augmentée.  
  
 Cette règle se déclenche uniquement pour les applications 32 bits s’exécutant sur des ordinateurs 32 bits.  
  
## <a name="rule-description"></a>Description de la règle  
 Le common language runtime (CLR) Microsoft .NET fournit un mécanisme de gestion automatique de la mémoire qui utilise un récupérateur de mémoire pour récupérer la mémoire des objets que l’application n’utilise plus. Le récupérateur de mémoire est orienté génération et repose sur l’hypothèse que de nombreuses allocations sont de courte durée. Les variables locales, par exemple, doivent avoir une durée de vie courte. Les objets récemment créés commencent à la génération 0 (gen 0), puis progressent jusqu’à la génération 1 lorsqu’ils survivent à l’exécution d’un garbage collection. Enfin, ils passent à la génération 2 si l’application les utilise toujours.  
  
 Les objets managés dont la taille est supérieure à 85 Ko sont alloués sur le tas des objets volumineux, où ils sont soumis à des garbage collections et à des compactages moins fréquents que les objets moins volumineux. Les objets volumineux sont gérés séparément, car ils sont supposés être plus persistants, et que l’association d’objets persistants et volumineux à des objets plus petits et fréquemment alloués peut causer une grave fragmentation du tas.  
  
 Lorsque la taille totale des tas managés approche de la limite définie par défaut, la surcharge de la gestion de mémoire augmente généralement jusqu’à affecter la réactivité et la scalabilité de l’application.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue [Marques](../profiling/marks-view.md). Accédez aux colonnes **Mémoire CLR .NET\\Nombre d’octets dans tous les tas** et **Nombre total d’octets validés**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles l’allocation de mémoire allouée est plus importante. Comparez les valeurs de la colonne **Nombre d’octets dans tous les tas** au taux de garbage collection signalé dans les colonnes **Mémoire CLR .NET\\Nombre de collections de la génération 0**, **Mémoire CLR .NET\\Nombre de collections de la génération 1** et **Mémoire CLR .NET\\Nombre de collections de la génération 2**, pour déterminer si le modèle des allocations de mémoire managée affecte le taux de garbage collection.  
  
 Dans une application .NET Framework, le common language runtime limite la taille totale des tas managés à une taille légèrement inférieure à la moitié de la taille maximale de la partie privée d’un espace d’adressage de processus. Pour un processus 32 bits s’exécutant sur un ordinateur 32 bits, la taille maximale de la partie privée de l’espace d’adressage de processus est de 2 Go. Lorsque la taille totale des tas managés commence à approcher de la limite par défaut, la surcharge de la gestion de mémoire peut augmenter et entraîner une baisse des performances de l’application.  
  
 Si une charge excessive de mémoire managée constitue un problème, envisagez l’une des options suivantes :  
  
- Optimisez la manière dont l’application utilise les ressources de mémoire managée.  
  
   - ou -  
  
- Allégez les contraintes architecturales associées à la taille maximale de la mémoire virtuelle d’un processus 32 bits.  
  
  Pour optimiser la manière dont l’application utilise les ressources de mémoire managée, collectez des données d’allocation de mémoire managée lors d’une exécution de profilage par allocation de mémoire .NET. Consultez les rapports [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md) pour comprendre le modèle d’allocation de mémoire de l’application.  
  
  Consultez la [vue Durée de vie des objets](../profiling/object-lifetime-view.md) pour déterminer quels objets de données du programme passent d’une génération à une autre, puis sont récupérés.  
  
  Consultez la [vue Allocations](../profiling/dotnet-memory-allocations-view.md) pour connaître le chemin d’exécution qui a entraîné ces allocations.  
  
  Pour plus d’informations sur l’amélioration des performances du garbage collection, consultez l’article technique .NET Framework [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=177946) sur le site MSDN.  
  
  Pour alléger les contraintes architecturales de mémoire virtuelle associées à la taille de la partie privée d’un espace d’adressage de processus, exécutez ce processus 32 bits sur un ordinateur 64 bits.  Un processus 32 bits exécuté sur un ordinateur 64 bits peut acquérir jusqu’à 4 Go de mémoire virtuelle privée.  
  
  Un processus 64 bits exécuté sur un ordinateur 64 bits peut acquérir jusqu’à 8 To de mémoire virtuelle. Recompilez l’application pour qu’elle s’exécute comme une application 64 bits native. Cette règle possède un caractère informatif et ne nécessite pas forcément d’action corrective.
