---
title: Concepteur d’activités TerminateWorkflow | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 67681982c9c8d77df77242be5c07679f3b0d24ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225710"
---
# <a name="terminateworkflow-activity-designer"></a>Concepteur d'activités TerminateWorkflow
Le **TerminateWorkflow** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.TerminateWorkflow> activité.  
  
## <a name="the-terminateworkflow-activity"></a>Activité TerminateWorkflow  
 L'activité <xref:System.Activities.Statements.TerminateWorkflow> termine l'exécution d'un workflow.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Utilisation du concepteur d'activités TerminateWorkflow  
 Le **TerminateWorkflow** Concepteur d’activités peut être trouvé dans le **Runtime** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **TerminateWorkflow** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.TerminateWorkflow> activité avec une valeur par défaut **DisplayName** de TerminateWorkflow. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **TerminateWorkflow** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.  
  
### <a name="the-terminateworkflow-properties"></a>Propriétés de TerminateWorkflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TerminateWorkflow> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.TerminateWorkflow>. La valeur par défaut est TerminateWorkflow. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Exception à lever lorsque le workflow est terminé. Définissez cette propriété dans la grille des propriétés.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Raison qui explique pourquoi le workflow a été terminé. Définissez cette propriété dans la grille des propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)