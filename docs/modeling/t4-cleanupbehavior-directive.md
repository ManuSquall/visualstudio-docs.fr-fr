---
title: Directive CleanUpBehavior T4 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f773f04799ec1ec975626699f37089c3c5b59b2d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Directive CleanUpBehavior T4
Pour supprimer l'appDomain après avoir traité un modèle de texte, insérez la ligne suivante :  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Les modèles de texte sont traités dans un appDomain indépendant du processus hôte. Dans la plupart des cas, lorsqu'un modèle de texte a été traité, l'appdomain sert à nouveau pour traiter le modèle suivant. Mais si vous spécifiez CleanupBehavior, l'appDomain est supprimé et le modèle suivant est traité dans un nouvel appDomain.  
  
 Cela ralentit le traitement du texte. Toutefois, cela peut s'avérer utile pour garantir la suppression des ressources.  
  
 Cette directive fonctionne uniquement dans l'hôte Visual Studio.