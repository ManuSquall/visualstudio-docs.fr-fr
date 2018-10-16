---
title: Concepteur d’activités de séquence | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d676c4270d636d0869d5b2f95f7a265bf0a085ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282774"
---
# <a name="sequence-activity-designer"></a>Concepteur d'activités Sequence
L’activité <xref:System.Activities.Statements.Sequence> contient une collection ordonnée d’activités enfants qu’elle exécute dans l’ordre.  
  
 Une autre façon d'exécuter un ensemble d'activités dans l'ordre consiste à utiliser une activité <xref:System.Activities.Statements.Flowchart>. Envisagez d’utiliser le [organigramme](../workflow-designer/flowchart-activity-designer.md) lorsque vous avez un branchement ou en boucle les flux de programme que vous souhaitez modéliser schématiquement.  
  
## <a name="using-the-sequence-activity-designer"></a>Utilisation du concepteur d'activités Sequence  
 Pour ajouter un <xref:System.Activities.Statements.Sequence> activité, faites glisser le **séquence** Concepteur d’activités à partir de la **boîte à outils** et déposez-le sur le [!INCLUDE[wfd1](../includes/wfd1-md.md)] surface. Pour ajouter une activité enfant à cette <xref:System.Activities.Statements.Sequence> activité, faites glisser une autre activité de la **boîte à outils** et déposez-le sur le triangle dans la zone avec le texte d’indication « Déposer l’activité ici ».  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Sequence dans le concepteur de workflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Sequence> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Sequence> dans l'en-tête. Sequence est la valeur par défaut. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagramme de flux](../workflow-designer/flowchart-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)