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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d85edb9773783abe6282918c432fc1a4eff83944
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826718"
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

5. Ouvrez le fichier de code **ThisAddIn. cs** ou **ThisAddIn. vb** .

6. Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Ajoutez le code ci-après au gestionnaire d'événements `ThisAddIn_Startup`. Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes` . Le code affiche également le volet des tâches.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Ce code associe votre volet des tâches personnalisé à la fenêtre active de l'application. Pour certaines applications, vous pouvez modifier ce code afin de vous assurer que le volet des tâches s'affiche avec les autres documents ou éléments de l'application. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Volets des tâches personnalisés](../vsto/custom-task-panes.md)
- [Procédure pas à pas : automatiser une application à partir d’un volet de tâches personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
