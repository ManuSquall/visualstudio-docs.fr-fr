---
title: Concepteur d’activités RemoveFromCollection &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672576"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>Concepteur d’activités RemoveFromCollection &lt;T &gt;
Le concepteur d’activités **RemoveFromCollection \<T >** permet de créer et de configurer une activité <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiont-activity"></a>Activité RemoveFromCollection \<T >
 L'activité <xref:System.Activities.Statements.RemoveFromCollection%601> supprime un élément spécifié d'une collection particulière.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Utilisation du concepteur d’activités RemoveFromCollection \<T >
 Le concepteur d’activités **RemoveFromCollection \<T >** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou CTRL + ALT + X.)

 Le concepteur d’activités **RemoveFromCollection \<T >** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.RemoveFromCollection%601> avec une <xref:System.Activities.Activity.DisplayName%2A> par défaut de RemoveFromCollection \<Int32 >. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **RemoveFromCollection \<T >** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-removefromcollectiont-properties"></a>Propriétés du > \<T RemoveFromCollection
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.RemoveFromCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.RemoveFromCollection%601>. La valeur par défaut est le > de \<Int32 RemoveFromCollection.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Élément à ajouter à la **Collection \<T >** . Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Collection à laquelle l'élément doit être ajouté. Cette collection est de type **ICollection \<TypeArgument >.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l’élément spécifié a été supprimé de la collection. Pour spécifier une variable à lier au résultat, entrez une variable dans la grille des propriétés|

## <a name="see-also"></a>Voir aussi
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)