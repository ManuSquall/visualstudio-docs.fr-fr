---
title: Bonnes pratiques pour MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 622d7b087e94d21f86691b88c3af4891aa533e9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013208"
---
# <a name="msbuild-best-practices"></a>Bonnes pratiques pour MSBuild
Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :  
  
-   Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande. Par exemple, utilisez  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   Évitez les caractères génériques quand vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. Les erreurs susceptibles de se produire quand vous ajoutez ou supprimez des fichiers sont ainsi plus faciles à localiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
