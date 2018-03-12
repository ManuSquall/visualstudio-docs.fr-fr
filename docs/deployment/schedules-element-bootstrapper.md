---
title: "&lt;Planifications&gt; élément (programme d’amorçage) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b7924515dbb661a4281397817be4b1b68487a6ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
 `Schedule`a l’attribut suivant.  
  
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