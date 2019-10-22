---
title: Concepteur d’activités ClearCollection &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657020"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Concepteur d’activités ClearCollection &lt;T &gt;
Le concepteur d’activités **ClearCollection \<T >** permet de créer et de configurer une activité <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Activité ClearCollection \<T >
 L’activité <xref:System.Activities.Statements.ClearCollection%601> efface tous les éléments d’une collection spécifiée.

### <a name="using-the-clearcollectiont-activity-designer"></a>Utilisation du concepteur d’activités ClearCollection \<T >
 Le concepteur d’activités **ClearCollection \<T >** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la Menu **affichage** ou CTRL + ALT + X.)

 Le concepteur d’activités **ClearCollection \<T >** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.ClearCollection%601> avec une <xref:System.Activities.Activity.DisplayName%2A> par défaut de ClearCollection \<Int32 >. (Par défaut, le *TypeArgument* est **Int32**. Cela peut être modifié dans la grille des propriétés.) La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **ClearCollection \<T >** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-clearcollectiont-properties"></a>Propriétés du > \<T ClearCollection
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ClearCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.ClearCollection%601>. La valeur par défaut est ClearCollection \<Int32 >. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Spécifie la collection dont les éléments doivent être effacés. Cette collection est de type **ICollection \<TypeArgument >.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Spécifie le type T des éléments contenus dans l'objet <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|

## <a name="see-also"></a>Voir aussi
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)