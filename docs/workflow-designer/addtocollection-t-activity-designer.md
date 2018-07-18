---
title: Concepteur de flux de travail - AddToCollection<T> Concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976700"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > Concepteur d’activités

Le **AddToCollection\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.AddToCollection%601> activité.

## <a name="the-addtocollectiont-activity"></a>La AddToCollection\<T > activité

L'activité <xref:System.Activities.Statements.AddToCollection%601> ajoute un élément à une collection.

### <a name="using-the-addtocollectiont-activity-designer"></a>À l’aide de la AddToCollection\<T > Concepteur d’activités

Le **AddToCollection\<T >** Concepteur d’activités peut être trouvé dans le **Collection** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le  **Boîte à outils** onglet du Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

Le **AddToCollection\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont placées, par comme à l’intérieur d’un <xref:System.Activities.Statements.Sequence>. Suppression de la **AddToCollection\<T >** Concepteur d’activités crée un <xref:System.Activities.Statements.AddToCollection%601> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection < Int32\>. (Par défaut, le *TypeArgument* est **Int32**. TypeArgument peut être modifiée dans la grille des propriétés.) Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **AddToCollection < T\>**  Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-addtocollectiont-properties"></a>La AddToCollection\<T > Propriétés

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.AddToCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.AddToCollection%601>. La valeur par défaut est AddToCollection < Int32\>. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|L’élément à ajouter à la Collection\<T >. Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Collection à laquelle l’élément doit être ajouté. Cette collection est de type **ICollection < TypeArgument\>**. Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, cela *TypeArgument* type est défini sur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* dans la zone de liste déroulante dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > Concepteur d’activités](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)