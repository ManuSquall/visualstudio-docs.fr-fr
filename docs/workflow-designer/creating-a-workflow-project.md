---
title: Créer un projet de Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 577bb58101556dc17c62453bfe18e9618c879405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999949"
---
# <a name="workflow-project-templates"></a>Modèles de projet de flux de travail

Vous pouvez créer des flux de travail, les services de workflow Windows Communication Foundation (WCF), les activités personnalisées et les concepteurs d’activités personnalisées à l’aide de modèles de projet Visual Studio. Cet article décrit comment créer des bibliothèques et des applications avec les modèles de projet disponibles dans Visual Studio.

## <a name="create-a-workflow-project"></a>Créer un projet de workflow

Visual Studio fournit quatre modèles de projet de flux de travail différents :

- Application de console de workflow

- Application de service de workflow WCF

- Bibliothèque d’activités

- Bibliothèque ActivityDesigner

Pour accéder à ces modèles, installez d’abord le **Windows Workflow Foundation** composant de Visual Studio 2017. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Une fois que vous avez installé le **Windows Workflow Foundation** composant, ouvrez le **nouveau projet** boîte de dialogue en sélectionnant **fichier** > **New**  >  **Projet**.

1. Dans le volet gauche, sélectionnez le **Visual C#** > **Workflow** catégorie (ou **Visual Basic** > **Workflow**si vous préférez Visual Basic).

1. Dans le volet central, sélectionnez un modèle de projet, tel que **Application Console de Workflow**.

1. Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.

1. Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou sélectionnez **Parcourir** pour naviguer jusqu'à lui.

1. Dans le **Solution** , entrez le nom de la nouvelle solution. Sélectionnez **OK** pour créer l’application.

   > [!NOTE]
   > Si vous souhaitez ajouter un nouveau projet à une solution existante, ouvrez cette solution dans Visual Studio, avec le bouton droit de la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter** > **nouveau Projet** pour ouvrir le **nouveau projet** boîte de dialogue.

## <a name="workflow-console-app"></a>Application de console de workflow

Si vous choisissez la **Application Console de Workflow** modèle, Visual Studio crée une définition de workflow dans XAML. Le Concepteur de flux de travail s’ouvre et affiche la zone de dessin du flux de travail que vous avez créé. Pour composer un workflow, faites glisser les activités ou autres éléments de flux de travail à partir de **boîte à outils** à l’aire de conception.

## <a name="wcf-workflow-service-app"></a>Application de service de workflow WCF

Si vous choisissez la **Application de Service de Workflow WCF** modèle, Visual Studio crée une définition de service comme XAML. Le Concepteur de flux de travail s’ouvre à la vue de conception avec un <xref:System.Activities.Statements.Sequence> activité qui contient un ensemble de <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> activités.

## <a name="activity-library"></a>Bibliothèque d’activités

Si vous choisissez la **bibliothèque d’activités** modèle, Visual Studio crée une définition d’activité dans XAML. Concepteur de flux de travail s’ouvre et affiche la zone de dessin pour votre activité personnalisée. Faites glisser une activité de **boîte à outils** vers l’aire de conception pour l’inclure dans votre activité personnalisée.

> [!NOTE]
> Vous êtes autorisé uniquement une activité enfant dans le corps de votre activité personnalisée. Toutefois, cette activité enfant peut être une activité composite, comme un <xref:System.Activities.Statements.Sequence> activité ou <xref:System.Activities.Statements.Flowchart> activité.

## <a name="activity-designer-library"></a>Bibliothèque ActivityDesigner

Si vous choisissez la **Bibliothèque ActivityDesigner** modèle, Visual Studio crée une définition de concepteur d’activités dans XAML et un fichier d’implémentation code-behind. Le Concepteur de flux de travail s’ouvre et affiche la zone de dessin pour votre concepteur d’activités. Faites glisser Windows Presentation Foundation (WPF) des contrôles de **boîte à outils** vers l’aire de conception pour les utiliser dans votre concepteur d’activités personnalisées.

Pour obtenir un exemple montrant comment implémenter un concepteur d’activités personnalisées, consultez [Comment : Créer un concepteur d’activités personnalisées](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Concepteurs d’activités personnalisées peuvent être utilisés pour les activités personnalisées et pour les activités de .NET Framework par défaut.

## <a name="see-also"></a>Voir aussi

- [Utiliser le Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
- [Concevez des workflows (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)