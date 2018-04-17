---
title: '&lt;Planifications&gt; élément (programme d’amorçage) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2b3cba1fcb5ac2d38b08383c8906adb2037e9651
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Planifications&gt; élément (programme d’amorçage)
Le `Schedules` élément contient `Schedule` éléments qui définissent des heures spécifiques commandes définies par le `Command` élément doit être exécuté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `Schedules` élément est un enfant de le `Product` élément. Chaque `Product` élément peut avoir au plus un `Schedules` élément. Le `Schedules` élément ne possède pas d’attributs.  
  
## <a name="schedule"></a>Planification  
 Le `Schedule` élément est un enfant de le `Schedules` élément. A `Schedules` l’élément doit avoir au moins un `Schedule` élément.  
  
 `Schedule` a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Le nom de l’élément de planification. Cela correspond à la `ScheduleName` propriété de la `Command` élément. Lorsqu’un `Command` fait référence à la planification nommée, il sera exécuté uniquement à l’heure indiquée par cette `Schedule` élément. Les planifications peuvent également être associées le `FailIf` et `BypassIf` éléments qui limitent ces tests conditionnels à l’exécution de la planification spécifiée. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
  
 Une fonction `Schedule` élément peut avoir un seul des enfants suivants.  
  
## <a name="buildlist"></a>BuildList  
 Le `BuildList` élément fait en sorte que le programme d’installation pour exécuter une commande immédiatement après le démarrage de l’application d’amorçage.  
  
## <a name="beforepackage"></a>BeforePackage  
 Le `BeforePackage` élément fait en sorte que le programme d’installation pour exécuter une commande avant l’installation du package spécifié.  
  
## <a name="afterpackage"></a>AfterPackage  
 Le `AfterPackage` élément fait en sorte que le programme d’installation pour exécuter une commande après avoir installé le package spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [\<Produit > élément](../deployment/product-element-bootstrapper.md)   
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)