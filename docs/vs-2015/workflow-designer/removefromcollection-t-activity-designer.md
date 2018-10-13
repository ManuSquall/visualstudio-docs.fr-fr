---
title: RemoveFromCollection&lt;T&gt; Concepteur d’activités | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341ed640666cc4501ac8917b568bf3f41b89b823
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170923"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt; Concepteur d’activités
Le **RemoveFromCollection\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.RemoveFromCollection%601> activité.  
  
## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection\<T > activité  
 L’activité <xref:System.Activities.Statements.RemoveFromCollection%601> supprime un élément spécifié d’une collection particulière.  
  
### <a name="using-the-removefromcollectiont-activity-designer"></a>À l’aide de RemoveFromCollection\<T > Concepteur d’activités  
 Le **RemoveFromCollection\<T >** Concepteur d’activités peut être trouvé dans le **Collection** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **Boîte à outils** onglet [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **RemoveFromCollection\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, tel que à l’intérieur d’un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.RemoveFromCollection%601> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection\<Int32 >. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **RemoveFromCollection\<T >** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection\<T > Propriétés  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.RemoveFromCollection%601> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.RemoveFromCollection%601>. La valeur par défaut est RemoveFromCollection\<Int32 >.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|L’élément à ajouter à la **Collection\<T >**. Cet élément est de type *T*, qui est de type *TypeArgument*. Pour spécifier l'élément, tapez une expression Visual Basic dans la grille des propriétés.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Collection à laquelle l’élément doit être ajouté. Cette collection est de type **ICollection\<TypeArgument >.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|  
|*TypeArgument*|True|Type T des éléments contenus dans la collection <xref:System.Collections.Generic.ICollection%601>. Par défaut, cela *TypeArgument* type est défini sur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* dans la zone de liste déroulante dans la grille des propriétés.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Valeur qui indique si l'élément spécifié a été supprimé de la collection. Pour spécifier une variable à lier au résultat, entrez une variable dans la grille des propriétés|  
  
## <a name="see-also"></a>Voir aussi  
 [collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)