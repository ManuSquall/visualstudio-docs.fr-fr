---
title: "Comment : ajouter un nouvel élément à un projet de flux de travail | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e2031f084b11f9879fd94f5d2e454e0966ed3787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Comment : ajouter un nouvel élément à un projet de workflow
Après avoir créé un projet de workflow, vous pouvez ajouter à votre projet des activités de workflow, des concepteurs et d'autres éléments [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous utilisez habituellement.  
  
 Le tableau suivant répertorie les éléments [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que vous pouvez ajouter à un projet de workflow.  
  
|Nom|Description|  
|----------|-----------------|  
|Activité|Activité à composer d'autres activités. Sélection de cet élément ajoute le même fichier XAML au projet que ceux obtenus lors de la sélection du **bibliothèque d’activités** modèle pour un nouveau projet. [!INCLUDE[crabout](../test/includes/crabout_md.md)]dans cette procédure, consultez [Comment : créer une bibliothèque d’activités](../workflow-designer/how-to-create-an-activity-library.md).|  
|Concepteur d'activités|Concepteur pour personnaliser l’expérience au moment du design d’une activité. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Bibliothèque ActivityDesigner** modèle pour un nouveau projet. [!INCLUDE[crabout](../test/includes/crabout_md.md)]dans cette procédure, consultez [Comment : créer une bibliothèque ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Activité de code|Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement.|  
|Service de workflow WCF|Service [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] construit à l'aide d'activités de workflow. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Application de Service de Workflow WCF** modèle pour un nouveau projet. [!INCLUDE[crabout](../test/includes/crabout_md.md)]dans cette procédure, consultez [Comment : créer une Application de Service de Workflow WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow  
  
1.  Sur le **projet** menu, cliquez sur **ajouter un nouvel élément...** .  
  
     Le **ajouter un nouvel élément** boîte de dialogue s’ouvre.  
  
2.  Dans le **modèles installés** volet, sélectionnez **Workflow** groupe.  
  
3.  Sélectionnez l'un des quatre éléments. Le tableau précédent répertorie les sélections disponibles.  
  
4.  Tapez un nom approprié pour l’élément dans le **nom** zone située au bas de la boîte de dialogue.  
  
5.  Cliquez sur **ajouter** pour ajouter un élément au projet de flux de travail en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)