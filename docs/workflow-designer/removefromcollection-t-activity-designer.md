---
title: Concepteur de flux de travail - RemoveFromCollection&lt;T&gt; Concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53fc58e231e5ef1cbbc6106e279b4925d145dd9f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755935"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > Concepteur d’activités

Le **RemoveFromCollection\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.RemoveFromCollection%601> activité.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > activité

L'activité <xref:System.Activities.Statements.RemoveFromCollection%601> supprime un élément spécifié d'une collection particulière.

### <a name="using-the-removefromcollectiont-activity-designer"></a>À l’aide de RemoveFromCollection\<T > Concepteur d’activités

Accès le **RemoveFromCollection\<T >** Concepteur d’activités dans le **Collection** catégorie de la **boîte à outils**. Le **RemoveFromCollection\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées, tel que à l’intérieur d’un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.RemoveFromCollection%601> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection < Int32\>. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **RemoveFromCollection < T\>**  Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> propriétés

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.RemoveFromCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.RemoveFromCollection%601>. La valeur par défaut est RemoveFromCollection < Int32\>.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|L’élément à ajouter à la **Collection\<T >**. Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Collection à laquelle l’élément doit être ajouté. Cette collection est de type **ICollection < TypeArgument\>.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, cela *TypeArgument* type est défini sur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* dans la zone de liste déroulante dans la grille des propriétés.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié a été supprimé de la collection. Pour spécifier une variable à lier au résultat, entrez une variable dans la grille des propriétés|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)