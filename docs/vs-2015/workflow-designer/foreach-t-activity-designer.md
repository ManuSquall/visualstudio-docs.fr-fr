---
title: "&lt;Concepteur d' &gt; activités foreach T | Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656649"
---
# <a name="foreachlttgt-activity-designer"></a>&lt;Concepteur d' &gt; activités foreach T
L'activité <xref:System.Activities.Statements.ForEach%601> exécute l'activité contenue dans sa propriété <xref:System.Activities.Statements.ForEach%601.Body%2A> pour chaque élément d'une collection <xref:System.Activities.Statements.ForEach%601.Values%2A> spécifiée.

## <a name="foreacht-properties-in-the-workflow-designer"></a>\<T>Propriétés foreach dans le concepteur de flux de travail
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ForEach%601> et décrit comment les utiliser dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.ForEach%601>. La valeur par défaut est ForEach \<Int32> . Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Vrai|Collection d’éléments à itérer. Pour définir le <xref:System.Activities.Statements.ForEach%601.Values%2A> , tapez une [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expression dans la zone **valeurs** du concepteur d’activités ** \<T> foreach** ou dans la grille des propriétés.|
|*TypeArgument*|Vrai|Type des éléments dans la <xref:System.Activities.Statements.ForEach%601.Values%2A> collection spécifiée par le paramètre générique *T*. Par défaut, *TypeArgument* a la valeur **Int32**. Pour modifier le type, modifiez la valeur de la zone de liste déroulante *TypeArgument* dans la grille des propriétés.|

 Par défaut, l’itérateur de boucle est nommé **Item**. Vous pouvez modifier le nom de la variable d'itérateur dans le concepteur d'activités <xref:System.Activities.Statements.ForEach%601>. L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Voir aussi
 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [Workflow de contrôle](../workflow-designer/control-flow-activity-designers.md)