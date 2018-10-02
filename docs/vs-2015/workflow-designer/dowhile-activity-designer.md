---
title: Concepteur d’activités DoWhile | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 911e6d6d94090ddcdd43fcd9511624e209f7c03c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501572"
---
# <a name="dowhile-activity-designer"></a>Concepteur d'activités DoWhile
Le <xref:System.Activities.Statements.DoWhile> activité s’exécute l’activité contenue dans son <xref:System.Activities.Statements.DoWhile.Body%2A> au moins une fois, jusqu'à ce qu’une condition spécifiée a la valeur **false**. Si vous devez exécuter zéro ou plusieurs fois l'activité contenue dans le corps d'une boucle, utilisez plutôt l'activité <xref:System.Activities.Statements.While>.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriétés de DoWhile dans Workflow Designer  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.DoWhile> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L’activité à exécuter pendant que la condition est **true**. Pour ajouter le <xref:System.Activities.Statements.DoWhile.Body%2A> activité, déposez une activité à partir de la boîte à outils dans le **corps** zone sur le **DoWhile** Concepteur d’activités avec le texte d’indication « Déposer l’activité ici ».|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condition à évaluer après chaque itération de la boucle. Pour définir le <xref:System.Activities.Statements.DoWhile.Condition%2A>, tapez un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expression dans le **Condition** zone sur le **DoWhile** activité concepteur ou dans la grille des propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [lors de la](../workflow-designer/while-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)