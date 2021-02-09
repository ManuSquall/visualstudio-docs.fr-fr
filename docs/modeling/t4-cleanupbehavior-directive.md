---
title: Directive CleanUpBehavior T4
description: En savoir plus sur la directive CleanUpBehavior et sur la suppression de l’appDomain après le traitement d’un modèle de texte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49609dd13e2e322f88f265d27e55c49154f4c5c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899654"
---
# <a name="t4-cleanupbehavior-directive"></a>Directive CleanUpBehavior T4

Pour supprimer l'appDomain après avoir traité un modèle de texte, insérez la ligne suivante :

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Les modèles de texte sont traités dans un appDomain indépendant du processus hôte. Dans la plupart des cas, lorsqu'un modèle de texte a été traité, l'appdomain sert à nouveau pour traiter le modèle suivant. Mais si vous spécifiez CleanupBehavior, l'appDomain est supprimé et le modèle suivant est traité dans un nouvel appDomain.

Cela ralentit le traitement du texte. Toutefois, cela peut s'avérer utile pour garantir la suppression des ressources.

Cette directive fonctionne uniquement dans l'hôte Visual Studio.
