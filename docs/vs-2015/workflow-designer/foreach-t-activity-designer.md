---
title: Concepteur d’activités ForEach &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656649"
---
# <a name="foreachlttgt-activity-designer"></a>Concepteur d’activités &lt;T ForEach &gt;
L'activité <xref:System.Activities.Statements.ForEach%601> exécute l'activité contenue dans sa propriété <xref:System.Activities.Statements.ForEach%601.Body%2A> pour chaque élément d'une collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifiée.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Propriétés de > \<T ForEach dans le Concepteur de flux de travail
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ForEach%601> et décrit comment les utiliser dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.ForEach%601>. La valeur par défaut est ForEach \<Int32 >. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Collection d’éléments à itérer. Pour définir la <xref:System.Activities.Statements.ForEach%601.Values%2A>, tapez une expression de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dans la zone **valeurs** de la **\<T foreach >** concepteur d’activités ou dans la grille des propriétés.|
|*TypeArgument*|True|Type des éléments dans la collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifiée par le paramètre générique *t*. Par défaut, *TypeArgument* a la valeur **Int32**. Pour modifier le type, modifiez la valeur de la zone de liste déroulante *TypeArgument* dans la grille des propriétés.|

 Par défaut, l’itérateur de boucle est nommé **Item**. Vous pouvez modifier le nom de la variable d'itérateur dans le concepteur d'activités <xref:System.Activities.Statements.ForEach%601>. L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Voir aussi
 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [le contrôle du workflow](../workflow-designer/control-flow-activity-designers.md)