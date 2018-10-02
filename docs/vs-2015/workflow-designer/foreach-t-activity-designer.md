---
title: ForEach&lt;T&gt; Concepteur d’activités | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b118eb62f3055486e26f9d90a4e3abb74fe38660
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503515"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Concepteur d’activités
L'activité <xref:System.Activities.Statements.ForEach%601> exécute l'activité contenue dans sa propriété <xref:System.Activities.Statements.ForEach%601.Body%2A> pour chaque élément d'une collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifiée.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > Propriétés dans le Concepteur de flux de travail  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ForEach%601> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ForEach%601>. La valeur par défaut est ForEach\<Int32 >. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Collection d’éléments à itérer. Pour définir le <xref:System.Activities.Statements.ForEach%601.Values%2A>, tapez un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expression dans le **valeurs** zone sur le **ForEach\<T >** activité concepteur ou dans la grille des propriétés.|  
|*TypeArgument*|True|Le type des éléments dans le <xref:System.Activities.Statements.ForEach%601.Values%2A> collection spécifiée par le paramètre générique *T*. Par défaut, *TypeArgument* a la valeur **Int32**. Pour modifier le type, modifiez la valeur de la *TypeArgument* zone de liste déroulante dans la grille des propriétés.|  
  
 Par défaut, l’itérateur de boucle est nommé **élément**. Vous pouvez modifier le nom de la variable d'itérateur dans le concepteur d'activités <xref:System.Activities.Statements.ForEach%601>. L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>Voir aussi  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)