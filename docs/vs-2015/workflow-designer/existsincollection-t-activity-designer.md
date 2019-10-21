---
title: Concepteur d’activités ExistsInCollection &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656732"
---
# <a name="existsincollectionlttgt-activity-designer"></a>Concepteur d’activités ExistsInCollection &lt;T &gt;
Le concepteur d’activités **ExistsInCollection \<T >** permet de créer et de configurer une activité <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Activité ExistsInCollection \<T >
 L’activité <xref:System.Activities.Statements.ExistsInCollection%601> détermine si un élément spécifié existe dans une collection particulière.

### <a name="using-the-existsincollectiont-activity-designer"></a>Utilisation du concepteur d’activités ExistsInCollection \<T >
 Le concepteur d’activités **ExistsInCollection \<T >** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la Menu **affichage** ou CTRL + ALT + X.)

 Le concepteur d’activités **ExistsInCollection \<T >** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.ExistsInCollection%601> avec une <xref:System.Activities.Activity.DisplayName%2A> par défaut de ExistsInCollection \<Int32 >. (Par défaut, le *TypeArgument* est **Int32**. Elle peut être modifiée dans la grille des propriétés.)  La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **ExistsInCollection \<T >** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-existsincollectiont-properties"></a>Propriétés du > \<T ExistsInCollection
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ExistsInCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ExistsInCollection%601>. La valeur par défaut est ExistsInCollection \<Int32 >. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Élément à ajouter à la collection \<T >. Cet élément est de type *T* est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Collection à laquelle l'élément doit être ajouté. Cette collection est de type **ICollection \<TypeArgument >.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié existe dans la collection. Pour spécifier une variable à lier au résultat, tapez une variable Visual Basic dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)