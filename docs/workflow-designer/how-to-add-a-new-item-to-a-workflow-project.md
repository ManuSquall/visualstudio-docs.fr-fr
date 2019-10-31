---
title: 'Concepteur de flux de travail : ajouter un nouvel élément au projet de workflow'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cdea5b3cbf99ab8213c320acc82665816062dca
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189641"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Comment : ajouter un nouvel élément à un projet de workflow

Une fois que vous avez créé un projet de workflow, vous pouvez ajouter des activités de workflow, des concepteurs et d’autres éléments Visual Studio familiers à votre projet.

Le tableau suivant répertorie les éléments de Windows Workflow Foundation (WF) que vous pouvez ajouter à un projet de flux de travail :

| Name | Description |
|-| - |
| Activité | Activité à composer d'autres activités. La sélection de cet élément ajoute le même fichier XAML au projet que celui obtenu lors de la sélection du modèle **bibliothèque d’activités** pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [créer un projet de flux de travail](creating-a-workflow-project.md). |
| Concepteur d'activités | Concepteur pour personnaliser l’expérience au moment du design d’une activité. La sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du modèle **bibliothèque du concepteur d’activités** pour un nouveau projet. |
| Activité de code | Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement. |
| Service de workflow WCF | Service [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] construit à l'aide d'activités de workflow. La sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du modèle d' **application de service de workflow WCF** pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : créer une application de service de flux de travail WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Dans le volet gauche, sélectionnez la catégorie **flux de travail** , puis sélectionnez un modèle d’élément de Workflow.

   > [!NOTE]
   > Si vous ne voyez pas la catégorie de **flux de travail** , installez d’abord le composant **Windows Workflow Foundation** de Visual Studio. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Entrez un nom pour l’élément dans la zone **nom** en bas de la boîte de dialogue.

1. Sélectionnez **Ajouter** pour ajouter l’élément au projet.

## <a name="see-also"></a>Voir aussi

- [Créer un projet de workflow](../workflow-designer/creating-a-workflow-project.md)