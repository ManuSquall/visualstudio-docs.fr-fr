---
title: Directive CleanUpBehavior T4 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 8b56d7be76e9cf43434f2f7d4c5fc2fa9a3222b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="t4-cleanupbehavior-directive"></a>Directive CleanUpBehavior T4
Pour supprimer l'appDomain après avoir traité un modèle de texte, insérez la ligne suivante :  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Les modèles de texte sont traités dans un appDomain indépendant du processus hôte. Dans la plupart des cas, lorsqu'un modèle de texte a été traité, l'appdomain sert à nouveau pour traiter le modèle suivant. Mais si vous spécifiez CleanupBehavior, l'appDomain est supprimé et le modèle suivant est traité dans un nouvel appDomain.  
  
 Cela ralentit le traitement du texte. Toutefois, cela peut s'avérer utile pour garantir la suppression des ressources.  
  
 Cette directive fonctionne uniquement dans l'hôte Visual Studio.