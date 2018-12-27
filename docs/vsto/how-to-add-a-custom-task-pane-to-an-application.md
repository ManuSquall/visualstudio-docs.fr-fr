---
title: 'Procédure : Ajouter un volet Office personnalisé à une application'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6436176c7af4206319d9d2f8408baccb0572da5b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646995"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Procédure : Ajouter un volet Office personnalisé à une application
  Vous pouvez ajouter un volet des tâches personnalisé aux applications répertoriées ci-dessus à l’aide du complément VSTO. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Ajouter un volet Office personnalisé à une application  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Pour ajouter un volet des tâches personnalisé à une application  
  
1.  Ouvrez ou créez un projet de complément VSTO pour l’une des applications répertoriées ci-dessus. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, changez le nom du nouveau contrôle utilisateur à **MyUserControl**, puis cliquez sur **ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
4.  Ajouter un ou plusieurs contrôles Windows Forms à partir de la **boîte à outils** au contrôle utilisateur.  
  
5.  Ouvrez le **ThisAddIn.cs** ou **ThisAddIn.vb** fichier de code.  
  
6.  Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn` .  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Ajoutez le code ci-après au gestionnaire d'événements `ThisAddIn_Startup`. Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes`. Le code affiche également le volet des tâches.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Ce code associe votre volet des tâches personnalisé à la fenêtre active de l’application. Pour certaines applications, vous pouvez modifier ce code afin de vous assurer que le volet des tâches s’affiche avec les autres documents ou éléments de l’application. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Volets Office personnalisés](../vsto/custom-task-panes.md)   
 [Procédure pas à pas : Automatiser une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  