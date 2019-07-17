---
title: '&lt;Planifications&gt; élément (programme d’amorçage) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85ffab2272a55bfe77c5f2a73c6e25967a203c85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68206094"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Planifications&gt; élément (programme d’amorçage)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Le `Schedules` élément est un enfant de le `Product` élément. Chaque `Product` élément peut avoir au maximum un `Schedules` élément. L’élément `Schedules` ne comporte pas d’attributs.  
  
## <a name="schedule"></a>Planification  
 Le `Schedule` élément est un enfant de le `Schedules` élément. Un `Schedules` élément doit avoir au moins un `Schedule` élément.  
  
 `Schedule` a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Requis. Le nom de l’élément de planification. Cela correspond à la `ScheduleName` propriété de la `Command` élément. Quand un `Command` fait référence à la planification nommée, elle est exécutée uniquement à l’heure indiquée par cette `Schedule` élément. Les planifications peuvent également être associées la `FailIf` et `BypassIf` éléments, qui limitent ces tests conditionnels visant l’exécution à la planification spécifiée. Pour plus d’informations, consultez [ \<commandes > élément](../deployment/commands-element-bootstrapper.md).|  
  
 A compte tenu de `Schedule` élément peut-être posséder exactement un des enfants suivants.  
  
## <a name="buildlist"></a>BuildList  
 Le `BuildList` élément indique le programme d’installation pour exécuter une commande immédiatement après le démarrage de l’application d’amorçage.  
  
## <a name="beforepackage"></a>BeforePackage  
 Le `BeforePackage` élément indique le programme d’installation pour exécuter une commande avant l’installation du package spécifié.  
  
## <a name="afterpackage"></a>AfterPackage  
 Le `AfterPackage` élément indique le programme d’installation pour exécuter une commande après avoir installé le package spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [\<Produit > élément](../deployment/product-element-bootstrapper.md)   
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
