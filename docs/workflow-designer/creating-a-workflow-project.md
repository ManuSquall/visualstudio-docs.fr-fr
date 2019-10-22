---
title: Créer un projet Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650578"
---
# <a name="workflow-project-templates"></a>Modèles de projet de workflow

Vous pouvez créer des workflows, des services de flux de travail Windows Communication Foundation (WCF), des activités personnalisées et des concepteurs d’activités personnalisées à l’aide de modèles de projet Visual Studio. Cet article explique comment créer des bibliothèques et des applications avec les modèles de projet disponibles dans Visual Studio.

## <a name="create-a-workflow-project"></a>Créer un projet de workflow

Visual Studio fournit quatre modèles de projet de flux de travail différents :

- Application console de workflow

- Application de service de flux de travail WCF

- Bibliothèque d’activités

- Bibliothèque du concepteur d’activités

Pour accéder à ces modèles, installez d’abord le composant **Windows Workflow Foundation** de Visual Studio. Pour obtenir des instructions détaillées, consultez [installer Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Une fois que vous avez installé le composant **Windows Workflow Foundation** , sélectionnez **fichier**  > **nouveau**  > **projet**.

1. Recherchez et sélectionnez un modèle de projet de flux de travail, par exemple, le modèle **application console de workflow** .

1. Passez à la création du projet.

   > [!NOTE]
   > Si vous souhaitez ajouter un nouveau projet à une solution existante, ouvrez cette solution dans Visual Studio, cliquez avec le bouton droit sur la solution dans **Explorateur de solutions**, puis sélectionnez **Ajouter**  > **nouveau projet**.

## <a name="workflow-console-app"></a>Application console de workflow

Si vous choisissez le modèle **application console de flux de travail** , Visual Studio crée une définition de workflow en XAML. Le Concepteur de flux de travail s’ouvre et affiche le canevas du flux de travail que vous avez créé. Pour composer un workflow, faites glisser des activités ou d’autres éléments de workflow de la **boîte à outils** vers l’aire de conception.

## <a name="wcf-workflow-service-app"></a>Application de service de flux de travail WCF

Si vous choisissez le modèle **application de service de flux de travail WCF** , Visual Studio crée une définition de service en tant que code XAML. Le Concepteur de flux de travail s’ouvre en mode création avec une activité <xref:System.Activities.Statements.Sequence> qui contient un ensemble d’activités de <xref:System.ServiceModel.Activities.Receive> et de <xref:System.ServiceModel.Activities.SendReply>.

## <a name="activity-library"></a>Bibliothèque d’activités

Si vous choisissez le modèle **bibliothèque d’activités** , Visual Studio crée une définition d’activité en XAML. Concepteur de flux de travail s’ouvre et affiche la zone de dessin de votre activité personnalisée. Faites glisser une activité de la **boîte à outils** vers l’aire de conception pour l’inclure dans votre activité personnalisée.

> [!NOTE]
> Vous n’avez autorisé qu’une seule activité enfant dans le corps de votre activité personnalisée. Toutefois, cette activité enfant peut être une activité composite, telle qu’une activité <xref:System.Activities.Statements.Sequence> ou <xref:System.Activities.Statements.Flowchart> activité.

## <a name="activity-designer-library"></a>Bibliothèque du concepteur d’activités

Si vous choisissez le modèle **bibliothèque du concepteur d’activités** , Visual Studio crée une définition de concepteur d’activités en XAML et un fichier d’implémentation code-behind. La Concepteur de flux de travail s’ouvre et affiche la zone de dessin de votre concepteur d’activités. Faites glisser les contrôles Windows Presentation Foundation (WPF) de la **boîte à outils** vers l’aire de conception afin de les utiliser dans votre concepteur d’activités personnalisées.

Pour obtenir un exemple d’implémentation d’un concepteur d’activités personnalisé, consultez [Comment : créer un concepteur d’activités personnalisées](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Les concepteurs d’activités personnalisées peuvent être utilisés pour les activités personnalisées et pour les activités .NET par défaut.

## <a name="see-also"></a>Voir aussi

- [Utilisez la Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
- [Concevoir des flux de travail (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)