---
title: Concepteur de flux de travail - ExistsInCollection&lt;T&gt; Concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5625f42489752647da57fad9956cff8c64b8f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974398"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > Concepteur d’activités

Le **ExistsInCollection\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.ExistsInCollection%601> activité.

## <a name="the-existsincollectiont-activity"></a>La ExistsInCollection\<T > activité
 L'activité <xref:System.Activities.Statements.ExistsInCollection%601> détermine si un élément spécifié existe dans une collection particulière.

### <a name="using-the-existsincollectiont-activity-designer"></a>À l’aide de la ExistsInCollection\<T > Concepteur d’activités
 Le **ExistsInCollection\<T >** Concepteur d’activités peut être trouvé dans le **Collection** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le  **Boîte à outils** onglet du Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **ExistsInCollection\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.ExistsInCollection%601> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection < Int32\>. (Par défaut, le *TypeArgument* est **Int32**. Elle peut être modifiée dans la grille des propriétés.)  Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **ExistsInCollection < T\>**  Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-existsincollectiont-properties"></a>La ExistsInCollection\<T > Propriétés
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ExistsInCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ExistsInCollection%601>. La valeur par défaut est ExistsInCollection < Int32\>. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|L’élément à ajouter à la Collection\<T >. Cet élément est de type *T* est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Collection à laquelle l’élément doit être ajouté. Cette collection est de type **ICollection < TypeArgument\>.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, cela *TypeArgument* type est défini sur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* dans la zone de liste déroulante dans la grille des propriétés.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié existe dans la collection. Pour spécifier une variable à lier au résultat, tapez une variable Visual Basic dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)