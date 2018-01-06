---
title: "Si Concepteur d’activités | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 950bff10372c9c40e047f891049e7cc387c8efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="if-activity-designer"></a>Concepteur d'activités If
L'activité <xref:System.Activities.Statements.If> évalue une condition et exécute une activité en fonction des résultats de cette évaluation. Cette activité est très utile lors de l'utilisation d'un style de modélisation des procédures de la programmation. Une activité <xref:System.Activities.Statements.If> peut être imbriquée dans une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Parallel>, par exemple. Si vous utilisez une activité <xref:System.Activities.Statements.Flowchart>, il est conseillé d'utiliser plutôt une activité <xref:System.Activities.Statements.FlowDecision>.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Propriétés d'If dans Workflow Designer  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.If> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Condition qui détermine l'activité enfant à exécuter. Pour définir le <xref:System.Activities.Statements.If.Condition%2A>, tapez un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expression dans le **Condition** zone sur le **si** activité concepteur ou dans la grille des propriétés.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|L’activité à exécuter si la <xref:System.Activities.Statements.If.Condition%2A> est **false**. Pour ajouter une activité qui est exécutée par le <xref:System.Activities.Statements.If.Else%2A> créer une branche, déposez une activité de la **boîte à outils** dans le **Else** zone sur le **si** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
|<xref:System.Activities.Statements.If.Then%2A>|False|L’activité à exécuter si la <xref:System.Activities.Statements.If.Condition%2A> est **true**. Pour ajouter une activité qui est exécutée par le <xref:System.Activities.Statements.If.Then%2A> créer une branche, déposez une activité de la **boîte à outils** dans le **puis** zone sur le **si** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Séquence](../workflow-designer/sequence-activity-designer.md)   
 [Parallèle](../workflow-designer/parallel-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)