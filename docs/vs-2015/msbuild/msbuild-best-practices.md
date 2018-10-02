---
title: Bonnes pratiques pour MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df388b4b5aeac30e5ee83e24dc08905507318f18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501822"
---
# <a name="msbuild-best-practices"></a>Meilleures pratiques pour MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [MSBuild meilleures pratiques](https://docs.microsoft.com/visualstudio/msbuild/msbuild-best-practices).  
  
  
Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :  
  
-   Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande. Par exemple, utilisez  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Évitez les caractères génériques quand vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. Les erreurs susceptibles de se produire quand vous ajoutez ou supprimez des fichiers sont ainsi plus faciles à localiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)



