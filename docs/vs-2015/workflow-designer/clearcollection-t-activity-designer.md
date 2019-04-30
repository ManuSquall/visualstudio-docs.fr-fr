---
title: ClearCollection&lt;T&gt; Concepteur d’activités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 240e634115e7602c66d69f0dba9cfa52504dc89a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977169"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; Concepteur d’activités
Le **ClearCollection\<T >** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.ClearCollection%601> activité.  
  
## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > activité  
 L’activité <xref:System.Activities.Statements.ClearCollection%601> efface tous les éléments d’une collection spécifiée.  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>À l’aide de ClearCollection\<T > Concepteur d’activités  
 Le **ClearCollection\<T >** Concepteur d’activités peut être trouvé dans le **Collection** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le  **Boîte à outils** onglet de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **ClearCollection\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.ClearCollection%601> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection\<Int32 >. (Par défaut, le *TypeArgument* est **Int32**. Elle peut être modifiée dans la grille des propriétés.) Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **ClearCollection\<T >** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.  
  
### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > Propriétés  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ClearCollection%601> et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.ClearCollection%601>. La valeur par défaut est ClearCollection\<Int32 >. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Spécifie la collection dont les éléments doivent être effacés. Cette collection est de type **ICollection\<TypeArgument >.** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|  
|*TypeArgument*|True|Spécifie le type T des éléments contenus dans l'objet <xref:System.Collections.Generic.ICollection%601>. Par défaut, cela *TypeArgument* type est défini sur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* dans la zone de liste déroulante dans la grille des propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)