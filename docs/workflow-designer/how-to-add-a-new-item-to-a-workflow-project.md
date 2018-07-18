---
title: 'Le Concepteur de flux de travail - Comment : ajouter un nouvel élément à un projet de flux de travail'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0aa2be7fd8ecccbd8de0aa54c2693dd6b02c7e10
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971640"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Comment : ajouter un nouvel élément à un projet de workflow

Une fois que vous avez créé un projet de flux de travail, vous pouvez ajouter des activités de flux de travail, les concepteurs et les autres éléments de Visual Studio familiers à votre projet.

Le tableau suivant répertorie les éléments de Windows Workflow Foundation (WF) que vous pouvez ajouter à un projet de flux de travail.

|Name|Description|
|----------|-----------------|
|Activité|Activité à composer d'autres activités. Sélection de cet élément ajoute le même fichier XAML au projet que ceux obtenus lors de la sélection du **bibliothèque d’activités** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une bibliothèque d’activités](../workflow-designer/how-to-create-an-activity-library.md).|
|Concepteur d'activités|Concepteur pour personnaliser l’expérience au moment du design d’une activité. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Bibliothèque ActivityDesigner** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une bibliothèque ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Activité de code|Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement.|
|Service de workflow WCF|Service [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] construit à l'aide d'activités de workflow. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Application de Service de Workflow WCF** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une Application de Service de Workflow WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1.  Sur le **projet** menu, cliquez sur **ajouter un nouvel élément...** .

     Le **ajouter un nouvel élément** boîte de dialogue s’ouvre.

2.  Dans le **modèles installés** volet, sélectionnez **Workflow** groupe.

3.  Sélectionnez l'un des quatre éléments. Le tableau précédent répertorie les sélections disponibles.

4.  Tapez un nom approprié pour l’élément dans le **nom** zone située au bas de la boîte de dialogue.

5.  Cliquez sur **ajouter** pour ajouter un élément au projet de flux de travail en cours.

## <a name="see-also"></a>Voir aussi

- [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)