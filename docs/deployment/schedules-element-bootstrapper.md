---
title: '&lt;Schedules &gt; , élément (programme d’amorçage) | Microsoft Docs'
description: L’élément Schedules contient des éléments Schedule, qui définissent des heures spécifiques d’exécution des commandes définies par l’élément Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f84727647f198c25175139412d3e8509e73fe1c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349358"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Schedules &gt; , élément (programme d’amorçage)
L' `Schedules` élément contient des `Schedule` éléments qui définissent des heures spécifiques à laquelle les commandes définies par l' `Command` élément doivent être exécutées.

## <a name="syntax"></a>Syntaxe

```xml
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
 L' `Schedules` élément est un enfant de l' `Product` élément. Chaque `Product` élément peut avoir au plus un `Schedules` élément. L’élément `Schedules` ne comporte pas d’attributs.

## <a name="schedule"></a>Planifier
 L' `Schedule` élément est un enfant de l' `Schedules` élément. Un `Schedules` élément doit avoir au moins un `Schedule` élément.

 `Schedule` a l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`Name`|Obligatoire. Nom de l’élément de planification. Cela correspond à la `ScheduleName` propriété de l' `Command` élément. Lorsqu’un `Command` référence la planification nommée, il est exécuté uniquement à l’heure indiquée par cet `Schedule` élément. Les planifications peuvent également être associées `FailIf` aux `BypassIf` éléments et, qui limitent l’exécution de ces tests conditionnels à la planification spécifiée. Pour plus d’informations, consultez [ \<Commands> élément](../deployment/commands-element-bootstrapper.md).|

 Un `Schedule` élément donné peut avoir un seul des enfants suivants.

## <a name="buildlist"></a>BuildList
 L' `BuildList` élément indique au programme d’installation d’exécuter une commande immédiatement après le démarrage de l’application d’amorçage.

## <a name="beforepackage"></a>BeforePackage
 L' `BeforePackage` élément indique au programme d’installation d’exécuter une commande avant l’installation du package spécifié.

## <a name="afterpackage"></a>AfterPackage
 L' `AfterPackage` élément indique au programme d’installation d’exécuter une commande après l’installation du package spécifié.

## <a name="see-also"></a>Voir aussi
- [\<Product> appartient](../deployment/product-element-bootstrapper.md)
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)