---
title: 'Le Concepteur de flux de travail - Comment : créer une Application de Service de Workflow WCF'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974667"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procédure : créer une application de service de workflow WCF

Applications de service de flux de travail de Windows Communication Foundation (WCF) sont des services de communications distribués qui passent des messages entre les clients et eux-mêmes au-delà des limites de processus. L’implémentation du contrat de service du côté service s’effectue de façon déclarative via des activités de flux de travail dans le .NET Framework 4 d’une manière analogue à des services de workflow hérité dans .NET Framework 3.5.

## <a name="to-create-a-wcf-workflow-service-application"></a>Pour créer une application de service de workflow WCF

1.  Démarrez Visual Studio 2010.

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Dans le **modèles installés** volet, sélectionnez **WCF** ou **Workflow** à partir la **Visual C#** ou **Visual Basic** regroupements selon le langage de choix.

4.  Dans le volet central, sélectionnez **Application de Service de Workflow WCF**.

5.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

7.  Dans le **Solution** , sélectionnez soit créer une nouvelle solution, puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans Visual Studio 2010, cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet** pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.

8.  Le modèle de projet crée une définition de service au format XAML. Le Concepteur de flux de travail Windows s’ouvre en mode design avec un <xref:System.Activities.Statements.Sequence> activité qui contient un ensemble de <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> activités.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer une activité](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)