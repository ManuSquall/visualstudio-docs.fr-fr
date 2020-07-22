---
title: Concepteur d’activités Concepteur de flux de travail-ExistsInCollection &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b48bb11e2aac9d542a07551df62d710c41596d28
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875655"
---
# <a name="existsincollectiont-activity-designer"></a>Concepteur d’activités ExistsInCollection\<T>

Le concepteur d’activités ** \<T> ExistsInCollection** permet de créer et de configurer une <xref:System.Activities.Statements.ExistsInCollection%601> activité.

## <a name="the-existsincollectiont-activity"></a>Activité ExistsInCollection \<T>

L’activité <xref:System.Activities.Statements.ExistsInCollection%601> détermine si un élément spécifié existe dans une collection particulière.

### <a name="using-the-existsincollectiont-activity-designer"></a>Utilisation du \<T> Concepteur d’activités ExistsInCollection

Le concepteur d’activités **ExistsInCollection \<T> ** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **ExistsInCollection \<T> ** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Une <xref:System.Activities.Statements.ExistsInCollection%601> activité est créée avec la valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection<Int32 \> . (Par défaut, le *TypeArgument* est **Int32**. Elle peut être modifiée dans la grille des propriétés.)  La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **ExistsInCollection<T \> ** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-existsincollectiont-properties"></a>Propriétés ExistsInCollection \<T>

Le tableau suivant présente les <xref:System.Activities.Statements.ExistsInCollection%601> Propriétés et décrit comment elles sont utilisées dans le concepteur :

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ExistsInCollection%601>. La valeur par défaut est ExistsInCollection<Int32 \> . Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Élément à rechercher dans la collection \<T> . Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Collection dans laquelle vérifier si l’élément existe. Cette collection est de type **ICollection<TypeArgument \> .** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié existe dans la collection. Pour spécifier une variable à lier au résultat, tapez une variable Visual Basic dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)