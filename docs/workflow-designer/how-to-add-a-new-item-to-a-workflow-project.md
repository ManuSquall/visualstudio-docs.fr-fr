---
title: 'Concepteur de flux de travail - Comment : Ajouter un nouvel élément à un projet de workflow'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d68b83f9364885ea33af2184f2a911bf916325
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222332"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procédure : Ajouter un nouvel élément à un projet de flux de travail

Une fois que vous avez créé un projet de flux de travail, vous pouvez ajouter des activités de flux de travail, les concepteurs et les autres éléments Visual Studio familiers à votre projet.

Le tableau suivant répertorie les éléments Windows Workflow Foundation (WF) que vous pouvez ajouter à un projet de flux de travail :


| Name | Description |
|-| - |
| Activité | Activité à composer d'autres activités. Sélection de cet élément ajoute le même fichier XAML au projet que ceux obtenus lors de la sélection du **bibliothèque d’activités** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [créer un projet de flux de travail](creating-a-workflow-project.md). |
| Concepteur d'activités | Concepteur pour personnaliser l’expérience au moment du design d’une activité. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Bibliothèque ActivityDesigner** modèle pour un nouveau projet. |
| Activité de code | Activité avec logique d'exécution écrite dans le code. Un fichier de code source avec substitution de la méthode <xref:System.Activities.CodeActivity.Execute%2A> est déjà généré automatiquement. |
| Service de workflow WCF | Service [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] construit à l'aide d'activités de workflow. Sélection de cet élément ajoute les mêmes fichiers au projet que ceux obtenus lors de la sélection du **Application de Service de Workflow WCF** modèle pour un nouveau projet. Pour plus d’informations sur cette procédure, consultez [Comment : Créer une Application de Service de Workflow WCF](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Dans le volet gauche, sélectionnez le **Workflow** catégorie et sélectionnez un modèle d’élément de flux de travail.

   > [!NOTE]
   > Si vous ne voyez pas le **Workflow** catégorie, la première installation du **Windows Workflow Foundation** composant de Visual Studio. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Entrez un nom pour l’élément dans le **nom** zone située au bas de la boîte de dialogue.

1. Sélectionnez **ajouter** pour ajouter l’élément au projet.

## <a name="see-also"></a>Voir aussi

- [Créer un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)