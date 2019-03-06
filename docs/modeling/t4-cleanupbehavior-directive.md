---
title: Directive CleanUpBehavior T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27df15c0b935ff4bae497940c095dba1598bc4c1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970567"
---
# <a name="t4-cleanupbehavior-directive"></a>Directive CleanUpBehavior T4

Pour supprimer l'appDomain après avoir traité un modèle de texte, insérez la ligne suivante :

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Les modèles de texte sont traités dans un appDomain indépendant du processus hôte. Dans la plupart des cas, lorsqu'un modèle de texte a été traité, l'appdomain sert à nouveau pour traiter le modèle suivant. Mais si vous spécifiez CleanupBehavior, l'appDomain est supprimé et le modèle suivant est traité dans un nouvel appDomain.

Cela ralentit le traitement du texte. Toutefois, cela peut s'avérer utile pour garantir la suppression des ressources.

Cette directive fonctionne uniquement dans l'hôte Visual Studio.