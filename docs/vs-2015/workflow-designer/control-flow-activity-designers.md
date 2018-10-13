---
title: Concepteurs d’activités de flux de contrôle | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e852bfa5b392c6ffa758678fa83dabd8a8c97f54
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303613"
---
# <a name="control-flow-activity-designers"></a>Concepteurs d'activités de flux de contrôle
[!INCLUDE[wfd1](../includes/wfd1-md.md)] inclut plusieurs activités fournies par le système que vous pouvez utiliser lors de la construction de vos workflows. Cette section contient les activités fournies par le système utilisées pour contrôler le flux dans un workflow. Les rubriques suivantes décrivent ces activités et fournissent des conseils sur la façon de les utiliser.  
  
## <a name="in-this-section"></a>Dans cette section  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 Exécute l’activité contenue dans son corps au moins une fois, jusqu'à ce qu’une condition spécifiée a la valeur **true**.  
  
 [ForEach\<T >](http://msdn.microsoft.com/en-us/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 Exécute l’activité contenue dans son corps pour chaque élément d’une collection spécifiée.  
  
 [If](../workflow-designer/if-activity-designer.md)  
 Évalue une condition et exécute une activité en fonction des résultats de cette évaluation.  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 Exécute simultanément une collection d’activités enfants.  
  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)  
 Énumère les éléments d’une collection et exécute en parallèle une instruction incorporée pour chaque élément de la collection.  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 Exécute l’une des diverses branches en réponse à un événement qui fournit le flux de contrôle basé sur les événements.  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 Fournit un chemin d’exécution potentiel dans une activité <xref:System.Activities.Statements.Pick>.  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 Contient une collection ordonnée d’activités enfants qui sont exécutées dans l’ordre.  
  
 [Commutateur\<T >](http://msdn.microsoft.com/en-us/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 Évalue une expression spécifiée et exécute l’activité à partir d’une collection d’activités dont la clé associée correspond à la valeur obtenue de l’évaluation.  
  
 [While](../workflow-designer/while-activity-designer.md)  
 Exécute l’activité contenue dans son corps lorsqu’une condition spécifiée a la valeur **true**.  
  
## <a name="reference"></a>Référence  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour les autres types de concepteurs d'activités, consultez les rubriques suivantes.  
  
 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)  
  
 [Organigramme](../workflow-designer/flowchart-activity-designers.md)  
  
 [Messagerie](../workflow-designer/messaging-activity-designers.md)  
  
 [Runtime](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [Transaction](../workflow-designer/transaction-activity-designers.md)  
  
 [Collection](../workflow-designer/collection-activity-designers.md)  
  
 [Gestion des erreurs](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Ressources externes  
 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)