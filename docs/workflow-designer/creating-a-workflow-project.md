---
title: Créer un projet de Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15c02312d5c257f13b9c0394790bc8a2611d7972
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949797"
---
# <a name="workflow-project-templates"></a>Modèles de projet de flux de travail

Vous pouvez créer des flux de travail, les services de workflow Windows Communication Foundation (WCF), les activités personnalisées et les concepteurs d’activités personnalisées à l’aide de modèles de projet Visual Studio. Cet article décrit comment créer des bibliothèques et des applications avec les modèles de projet disponibles dans Visual Studio.

## <a name="create-a-workflow-project"></a>Créer un projet de workflow

Visual Studio fournit quatre modèles de projet de flux de travail différents :

- Application de console de workflow

- Application de service de workflow WCF

- Bibliothèque d’activités

- Bibliothèque ActivityDesigner

Pour accéder à ces modèles, installez d’abord le **Windows Workflow Foundation** composant de Visual Studio. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Une fois que vous avez installé le **Windows Workflow Foundation** composant, sélectionnez **fichier** > **New** > **deprojet**.

1. Recherchez et sélectionnez un modèle de projet de flux de travail, par exemple, le **Application Console de Workflow** modèle.

1. Suivez les instructions créer le projet.

   > [!NOTE]
   > Si vous souhaitez ajouter un nouveau projet à une solution existante, ouvrez cette solution dans Visual Studio, avec le bouton droit de la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter** > **nouveau Projet**.

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