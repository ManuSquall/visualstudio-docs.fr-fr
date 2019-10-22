---
title: Directive CleanUpBehavior T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 856c98f1462b1474d1d38656375d93d5301717f6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661788"
---
# <a name="t4-cleanupbehavior-directive"></a>Directive CleanUpBehavior T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour supprimer l'appDomain après avoir traité un modèle de texte, insérez la ligne suivante :

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

 Les modèles de texte sont traités dans un appDomain indépendant du processus hôte. Dans la plupart des cas, lorsqu'un modèle de texte a été traité, l'appdomain sert à nouveau pour traiter le modèle suivant. Mais si vous spécifiez CleanupBehavior, l'appDomain est supprimé et le modèle suivant est traité dans un nouvel appDomain.

 Cela ralentit le traitement du texte. Toutefois, cela peut s'avérer utile pour garantir la suppression des ressources.

 Cette directive fonctionne uniquement dans l'hôte Visual Studio.
