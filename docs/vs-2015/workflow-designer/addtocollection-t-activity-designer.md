---
title: "&lt;Concepteur d' &gt; activités AddToCollection T | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659203"
---
# <a name="addtocollectionlttgt-activity-designer"></a>&lt;Concepteur d' &gt; activités AddToCollection T
Le concepteur d’activités ** \<T> AddToCollection** permet de créer et de configurer une <xref:System.Activities.Statements.AddToCollection%601> activité.

## <a name="the-addtocollectiont-activity"></a>Activité AddToCollection \<T>
 L'activité <xref:System.Activities.Statements.AddToCollection%601> ajoute un élément à une collection.

### <a name="using-the-addtocollectiont-activity-designer"></a>Utilisation du \<T> Concepteur d’activités AddToCollection
 Le concepteur d’activités **AddToCollection \<T> ** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

 Le concepteur d’activités **AddToCollection \<T> ** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] , là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Une <xref:System.Activities.Statements.AddToCollection%601> activité est créée avec la valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> AddToCollection \<Int32> . (Par défaut, le *TypeArgument* est **Int32**. Cela peut être modifié dans la grille des propriétés.) La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **AddToCollection \<T> ** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-addtocollectiont-properties"></a>Propriétés AddToCollection \<T>
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.AddToCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.AddToCollection%601>. La valeur par défaut est AddToCollection \<Int32> . Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Élément à ajouter à la collection \<T> . Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Collection à laquelle l'élément doit être ajouté. Cette collection est de type **ICollection \<TypeArgument> **. Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|

## <a name="see-also"></a>Voir aussi
 [Collection](../workflow-designer/collection-activity-designers.md) [Concepteur d' \<T> activités AddToCollection](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)