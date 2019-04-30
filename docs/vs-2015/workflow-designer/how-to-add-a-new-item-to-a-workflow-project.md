---
title: 'Procédure : Ajouter un nouvel élément à un projet de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ecc310896f7b938025d42e06ac5ef0ec8bac3d35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62932995"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procédure : Ajouter un nouvel élément à un projet de workflow
Après avoir créé un projet de workflow, vous pouvez ajouter à votre projet des activités de workflow, des concepteurs et d'autres éléments [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous utilisez habituellement.  
  
 Le tableau suivant répertorie les éléments [!INCLUDE[wf](../includes/wf-md.md)] que vous pouvez ajouter à un projet de workflow.  
  
|Nom|Description|  
|----------|-----------------|  
|Activité|Activité à composer d'autres activités. Sélection de cet élément ajoute le même fichier XAML au projet que ceux obtenus lors de la sélection du **bibliothèque d’activités** modèle pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : Créer une bibliothèque d’activités](../workflow-designer/how-to-create-an-activity-library.md).|  
|Concepteur d'activités|Concepteur pour personnaliser l’expérience au moment du design d’une activité. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Bibliothèque ActivityDesigner** modèle pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : Créer une bibliothèque ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Activité de code|Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement.|  
|Service de workflow WCF|Service [!INCLUDE[indigo2](../includes/indigo2-md.md)] construit à l'aide d'activités de workflow. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Application de Service de Workflow WCF** modèle pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : Créer une Application de Service de Workflow WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow  
  
1. Sur le **projet** menu, cliquez sur **ajouter un nouvel élément...** .  
  
     Le **ajouter un nouvel élément** boîte de dialogue s’ouvre.  
  
2. Dans le **modèles installés** volet, sélectionnez **Workflow** groupe.  
  
3. Sélectionnez l'un des quatre éléments. Le tableau précédent répertorie les sélections disponibles.  
  
4. Tapez un nom approprié pour l’élément dans le **nom** zone située au bas de la boîte de dialogue.  
  
5. Cliquez sur **ajouter** pour ajouter l’élément au projet de flux de travail en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)