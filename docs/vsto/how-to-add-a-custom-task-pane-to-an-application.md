---
title: 'Comment : ajouter un volet de tâches personnalisé à une application'
description: Découvrez comment vous pouvez ajouter un volet des tâches personnalisé aux applications à l’aide du complément Visual Studio Tools pour Office (VSTO).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e8056eddef6329aeb10ed5545c4146f0af0f167
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845048"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Comment : ajouter un volet de tâches personnalisé à une application
  Vous pouvez ajouter un volet des tâches personnalisé aux applications répertoriées ci-dessus à l’aide du complément VSTO. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Ajouter un volet de tâches personnalisé à une application

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Pour ajouter un volet des tâches personnalisé à une application

1. Ouvrez ou créez un projet de complément VSTO pour l'une des applications répertoriées ci-dessus. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom du nouveau contrôle utilisateur par **MyUserControl**, puis cliquez sur **Ajouter**.

     Le contrôle utilisateur s'ouvre dans le concepteur.

4. Ajoutez un ou plusieurs contrôles Windows Forms de la **boîte à outils** au contrôle utilisateur.

5. Ouvrez le fichier de code **ThisAddIn.cs** ou **ThisAddIn. vb** .

6. Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn` .

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Ajoutez le code ci-après au gestionnaire d'événements `ThisAddIn_Startup`. Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes` . Le code affiche également le volet des tâches.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Ce code associe votre volet des tâches personnalisé à la fenêtre active de l'application. Pour certaines applications, vous pouvez modifier ce code afin de vous assurer que le volet des tâches s'affiche avec les autres documents ou éléments de l'application. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Volets des tâches personnalisés](../vsto/custom-task-panes.md)
- [Procédure pas à pas : automatiser une application à partir d’un volet de tâches personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
