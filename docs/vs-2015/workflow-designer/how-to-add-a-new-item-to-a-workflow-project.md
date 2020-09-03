---
title: 'Comment : ajouter un nouvel élément à un projet de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656630"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Comment : ajouter un nouvel élément à un projet de workflow
Après avoir créé un projet de workflow, vous pouvez ajouter à votre projet des activités de workflow, des concepteurs et d'autres éléments [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous utilisez habituellement.

 Le tableau suivant répertorie les éléments [!INCLUDE[wf](../includes/wf-md.md)] que vous pouvez ajouter à un projet de workflow.

|Nom|Description|
|----------|-----------------|
|Activité|Activité à composer d'autres activités. La sélection de cet élément ajoute le même fichier XAML au projet que celui obtenu lors de la sélection du modèle **bibliothèque d’activités** pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : créer une bibliothèque d’activités](../workflow-designer/how-to-create-an-activity-library.md).|
|Concepteur d'activités|Concepteur pour personnaliser l’expérience au moment du design d’une activité. La sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du modèle **bibliothèque du concepteur d’activités** pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : créer une bibliothèque de concepteur d’activités](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Activité de code|Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement.|
|Service de workflow WCF|Service [!INCLUDE[indigo2](../includes/indigo2-md.md)] construit à l'aide d'activités de workflow. La sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du modèle d' **application de service de workflow WCF** pour un nouveau projet. [!INCLUDE[crabout](../includes/crabout-md.md)] sur cette procédure, consultez [Comment : créer une application de service de flux de travail WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1. Dans le menu **projet** , cliquez sur **Ajouter un nouvel élément...**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Dans le volet **modèles installés** , sélectionnez Groupe de **flux de travail** .

3. Sélectionnez l'un des quatre éléments. Le tableau précédent répertorie les sélections disponibles.

4. Tapez un nom approprié pour l’élément dans la zone **nom** en bas de la boîte de dialogue.

5. Cliquez sur **Ajouter** pour ajouter l’élément au projet de workflow actuel.

## <a name="see-also"></a>Voir aussi
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)