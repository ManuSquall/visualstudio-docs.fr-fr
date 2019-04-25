---
title: Bonnes pratiques pour MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043419"
---
# <a name="msbuild-best-practices"></a>Meilleures pratiques pour MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :  
  
- Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande. Par exemple, utilisez  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Évitez les caractères génériques quand vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. Les erreurs susceptibles de se produire quand vous ajoutez ou supprimez des fichiers sont ainsi plus faciles à localiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
