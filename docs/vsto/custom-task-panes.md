---
title: Volets de tâches personnalisés
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dff9c5f8602f1e11ef020400a11d7d165b23b04
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
---
# <a name="custom-task-panes"></a>Volets de tâches personnalisés
  Les volets de tâches sont des panneaux d’interface utilisateur généralement ancrés à l’un des côtés d’une fenêtre dans une application Microsoft Office. Les volets de tâches personnalisés vous permettent de créer votre propre volet de tâches et de fournir aux utilisateurs une interface familière pour accéder aux fonctionnalités de votre solution. Par exemple, l'interface peut comporter des contrôles exécutant du code pour modifier des documents ou afficher des données à partir d'une source de données.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Un volet de tâches personnalisé diffère du volet Actions. Le volet Actions fait partie des personnalisations au niveau du document pour Microsoft Office Word et Microsoft Office Excel. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Avantages des volets de tâches personnalisés  
 Les volets de tâches personnalisés vous permettent d’intégrer vos propres fonctionnalités dans une interface utilisateur familière. Vous pouvez créer rapidement un volet de tâches personnalisé à l’aide des outils Visual Studio.  
  
### <a name="familiar-user-interface"></a>Interface utilisateur familière  
 Les utilisateurs d’applications dans Microsoft Office system sont déjà habitués à utiliser les volets de tâches telles que la **Styles et mise en forme** volet de tâches dans Word. Les volets de tâches personnalisés se comportent comme les autres volets de tâches de Microsoft Office System. Les utilisateurs peuvent ancrer les volets de tâches personnalisés aux différents côtés de la fenêtre d'application ou les faire glisser n'importe où dans la fenêtre. Vous pouvez créer un complément VSTO qui affiche plusieurs volets de tâches personnalisés simultanément, et les utilisateurs peuvent contrôler individuellement chaque volet de tâches.  
  
### <a name="windows-forms-support"></a>Prise en charge de Windows forms  
 L’interface utilisateur d’un volet de tâches personnalisé que vous créez à l’aide des outils de développement Office dans Visual Studio est basée sur les contrôles Windows Forms. Le concepteur Windows Forms familier vous permet de concevoir l'interface utilisateur pour un volet de tâches personnalisé. Vous pouvez également utiliser la prise en charge des liaisons de données dans Windows Forms pour lier une source de données à des contrôles dans le volet de tâches.  
  
## <a name="create-a-custom-task-pane"></a>Créer un volet Office personnalisé  
 Vous pouvez créer un volet de tâches personnalisé de base en deux étapes :  
  
1.  Créez une interface utilisateur pour votre volet de tâches personnalisé en ajoutant des contrôles Windows Forms à un objet <xref:System.Windows.Forms.UserControl>.  
  
2.  Instanciez le volet de tâches personnalisé en passant le contrôle utilisateur à l'objet <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> dans votre complément VSTO. Cette collection retourne un nouvel objet <xref:Microsoft.Office.Tools.CustomTaskPane> pouvant servir à modifier l'apparence du volet de tâches et à répondre aux événements utilisateur.  
  
 Pour plus d’informations, consultez [Comment : ajouter un volet Office personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="create-the-user-interface"></a>Créer l’interface utilisateur  
 Tous les volets de tâches personnalisés créés à l'aide des outils de développement Office dans Visual Studio contiennent un objet <xref:System.Windows.Forms.UserControl>. Ce contrôle utilisateur fournit l’interface utilisateur de votre volet de tâches personnalisé. Vous pouvez créer le contrôle utilisateur au moment du design ou au moment de l’exécution. Si vous le créez au moment du design, vous pouvez utiliser le concepteur Windows Forms pour construire l’interface utilisateur de votre volet de tâches.  
  
### <a name="instantiate-the-custom-task-pane"></a>Instanciez le volet de tâches personnalisé  
 Après avoir créé un contrôle utilisateur contenant l'interface utilisateur du volet de tâches personnalisé, vous devez instancier un objet <xref:Microsoft.Office.Tools.CustomTaskPane>. Pour cela, passez le contrôle utilisateur à l'objet <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> de votre complément VSTO en appelant l'une des méthodes <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>. Cette collection est exposée en tant que champ `CustomTaskPanes` de la classe `ThisAddIn`. L'exemple de code suivant est destiné à être exécuté à partir de la classe `ThisAddIn`.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 Les méthodes <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> retournent un nouvel objet <xref:Microsoft.Office.Tools.CustomTaskPane>. Vous pouvez utiliser cet objet pour modifier l’apparence du volet de tâches et répondre aux événements utilisateur.  
  
### <a name="control-the-task-pane-in-multiple-windows"></a>Le volet de tâches dans plusieurs fenêtres de contrôle  
 Les volets de tâches personnalisés sont associés à une fenêtre frame de document, qui présente une vue d’un document ou d’un élément à l’utilisateur. Le volet de tâches est visible uniquement quand la fenêtre associée est visible.  
  
 Pour déterminer la fenêtre qui affiche le volet de tâches personnalisé, utilisez la surcharge de méthode <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> appropriée quand vous créez le volet de tâches :  
  
-   Pour associer le volet de tâches à la fenêtre active, utilisez la méthode <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
-   Pour associer le volet de tâches à un document hébergé par une fenêtre spécifiée, utilisez la méthode <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
 Certaines applications Office nécessitent des instructions explicites pour savoir quand créer ou afficher votre volet de tâches, quand plusieurs fenêtres sont ouvertes. Il est donc important de se demander où instancier le volet de tâches personnalisé dans votre code pour vous assurer que ce volet s’affiche avec les documents et éléments appropriés dans l’application. Pour plus d’informations, consultez [gérer les volets de tâches personnalisés dans les fenêtres d’application](#Managing).  
  
## <a name="access-the-application-from-the-task-pane"></a>Accéder à l’application à partir du volet de tâches  
 Pour automatiser l'application à partir du contrôle utilisateur, vous pouvez directement accéder au modèle objet en utilisant `Globals.ThisAddIn.Application` dans votre code. La classe `Globals` statique permet d'accéder à l'objet `ThisAddIn`. Le champ `Application` de cet objet est le point d'entrée dans le modèle objet de l'application.  
  
 Pour plus d’informations sur la `Application` champ le `ThisAddIn` d’objets, consultez [des Compléments VSTO de programme](../vsto/programming-vsto-add-ins.md). Pour une procédure pas à pas qui montre comment automatiser une application à partir d’un volet Office personnalisé, consultez [procédure pas à pas : automatique, une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Pour plus d’informations sur la `Globals` de classe, consultez [d’accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="manage-the-user-interface-of-the-task-pane"></a>Gérer l’interface utilisateur du volet de tâches  
 Après avoir créé le volet de tâches, vous pouvez utiliser les propriétés et événements de l'objet <xref:Microsoft.Office.Tools.CustomTaskPane> pour contrôler l'interface utilisateur du volet de tâches et répondre quand l'utilisateur modifie ce volet.  
  
### <a name="make-the-custom-task-pane-visible"></a>Rendre visible le volet de tâches personnalisé  
 Par défaut, le volet de tâches n’est pas visible. Pour afficher le volet des tâches, vous devez définir le <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> propriété **true**.  
  
 Les utilisateurs peuvent fermer un volet de tâches à tout moment en cliquant sur le **fermer** bouton (X) dans le coin du volet des tâches. Toutefois, il n’existe pas de méthode par défaut permettant de rouvrir le volet de tâches personnalisé. Si un utilisateur ferme un volet de tâches personnalisé, il ne peut pas l'afficher de nouveau à moins que vous lui fournissiez un moyen de le faire.  
  
 Si vous créez un volet de tâches personnalisé dans votre complément VSTO, vous devez également créer un élément d'interface utilisateur, tel qu'un bouton, sur lequel les utilisateurs peuvent cliquer pour afficher ou masquer le volet de tâches personnalisé. Si vous créez un volet de tâches personnalisé dans une application Microsoft Office qui prend en charge la personnalisation du ruban, vous pouvez ajouter un groupe de contrôles au ruban avec un bouton permettant d’afficher ou de masquer le volet de tâches personnalisé. Pour une procédure pas à pas qui montre comment effectuer cette opération, consultez [procédure pas à pas : synchronisation d’un volet Office personnalisé avec un bouton de ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Si vous créez un volet de tâches personnalisé dans une application Microsoft Office qui ne prend en charge la personnalisation du ruban, vous pouvez ajouter un objet <xref:Microsoft.Office.Core.CommandBarButton> permettant d'afficher ou de masquer le volet de tâches personnalisé.  
  
### <a name="modify-the-appearance-of-the-task-pane"></a>Modifier l’apparence du volet de tâches  
 Vous pouvez contrôler la taille et l'emplacement d'un volet de tâches personnalisé à l'aide des propriétés de l'objet <xref:Microsoft.Office.Tools.CustomTaskPane>. Vous pouvez apporter de nombreuses autres modifications à l'apparence d'un volet de tâches personnalisé à l'aide des propriétés de l'objet <xref:System.Windows.Forms.UserControl> figurant dans le volet de tâches personnalisé. Par exemple, vous pouvez spécifier une image d'arrière-plan pour un volet de tâches personnalisé à l'aide de la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle utilisateur.  
  
 Le tableau suivant répertorie les modifications que vous pouvez apporter à un volet de tâches personnalisé à l'aide des propriétés <xref:Microsoft.Office.Tools.CustomTaskPane>.  
  
|Tâche|Propriété|  
|----------|--------------|  
|Modifier la taille du volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Modifier l’emplacement du volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Masquer et rendre visible le volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Empêcher l’utilisateur de modifier l’emplacement du volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="program-custom-task-pane-events"></a>Événements de volet de tâches personnalisé de programme  
 Vous souhaitez peut-être que votre complément VSTO réponde quand l’utilisateur modifie le volet de tâches personnalisé. Par exemple, si l'utilisateur remplace l'orientation verticale du volet par l'orientation horizontale, vous pouvez repositionner les contrôles.  
  
 Le tableau suivant répertorie les événements que vous pouvez gérer pour répondre aux modifications susceptibles d'être apportées par l'utilisateur dans le volet de tâches personnalisé.  
  
|Tâche|événement|  
|----------|-----------|  
|Répondre quand l’utilisateur modifie l’emplacement du volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Répondre quand l’utilisateur masque ou rend visible le volet de tâches|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="clean-up-resources-used-by-the-task-pane"></a>Nettoyer les ressources utilisées par le volet de tâches  
 Une fois que vous avez créé un volet de tâches personnalisé, l'objet <xref:Microsoft.Office.Tools.CustomTaskPane> reste en mémoire tant que votre complément VSTO est en cours d'exécution. L’objet reste en mémoire même quand l’utilisateur clique sur le **fermer** bouton (X) dans le coin du volet des tâches.  
  
 Pour nettoyer les ressources utilisées par le volet de tâches alors que le complément VSTO est encore en cours d'exécution, utilisez les méthodes <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> ou <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A>. Ces méthodes suppriment l'objet <xref:Microsoft.Office.Tools.CustomTaskPane> spécifié de la collection `CustomTaskPanes`, et elles appellent la méthode <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> de l'objet.  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nettoie automatiquement les ressources utilisées par le volet de tâches personnalisé quand le complément VSTO est déchargé. N’appelez pas la <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> ou <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> méthodes dans le `ThisAddIn_Shutdown` Gestionnaire d’événements dans votre projet. Ces méthodes lèvent une exception <xref:System.ObjectDisposedException> car [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nettoie les ressources utilisées par l'objet <xref:Microsoft.Office.Tools.CustomTaskPane> avant l'appel de `ThisAddIn_Shutdown`. Pour plus d’informations sur `ThisAddIn_Shutdown`, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Gérer les volets de tâches personnalisés dans plusieurs fenêtres d’application  
 Quand vous créez un volet de tâches personnalisé dans une application qui utilise plusieurs fenêtres pour afficher des documents et d’autres éléments, vous devez prendre des mesures supplémentaires pour garantir l’affichage du volet de tâches quand l’utilisateur s’attend à le voir.  
  
 Dans toutes les applications, les volets de tâches personnalisés sont associés à une fenêtre frame de document, qui présente une vue d'un document ou d'un élément à l'utilisateur. Le volet de tâches est visible uniquement quand la fenêtre associée est visible. Toutefois, toutes les applications n'utilisent pas les fenêtres frame de document de la même façon.  
  
 Les groupes d’applications suivants ont des exigences différentes en termes de développement :  
  
-   [Outlook](#Outlook)  
  
-   [Word, InfoPath et PowerPoint](#WordAndInfoPath)  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : gérer les volets de tâches dans les Compléments VSTO Word ?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Outlook  
 Quand vous créez un volet de tâches personnalisé pour Outlook, le volet est associé à une fenêtre d’explorateur ou d’inspecteur spécifique. Les explorateurs sont des fenêtres qui affichent le contenu d’un dossier, et les inspecteurs sont des fenêtres qui affichent un élément tel qu’un message électronique ou une tâche.  
  
 Pour afficher un volet de tâches personnalisé avec plusieurs fenêtres d’explorateur ou d’inspecteur, vous devez créer une nouvelle instance du volet de tâches personnalisé quand une fenêtre d’explorateur ou d’inspecteur s’ouvre. Pour cela, gérez un événement qui se déclenche quand une fenêtre d'explorateur ou d'inspecteur est créée, puis créez le volet de tâches dans le gestionnaire d'événements. Vous pouvez également gérer les événements d’explorateur et d’inspecteur pour masquer ou afficher les volets de tâches en fonction de la fenêtre visible.  
  
 Pour associer le volet de tâches à un Explorateur ou Inspecteur spécifique, utilisez la <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> méthode pour créer le volet des tâches, puis passez la <xref:Microsoft.Office.Interop.Outlook.Explorer> ou <xref:Microsoft.Office.Interop.Outlook.Inspector> de l’objet à la *fenêtre* paramètre. Pour plus d’informations sur la création de volets de tâches personnalisés, consultez [vue d’ensemble des volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 Pour surveiller l'état des fenêtres d'inspecteur, vous pouvez gérer les événements d'inspecteur suivants :  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Empêcher plusieurs instances d’un volet de tâches personnalisé dans Outlook  
 Pour empêcher les fenêtres Outlook d'afficher plusieurs instances d'un volet de tâches personnalisé, supprimez explicitement le volet de tâches personnalisé de la collection `CustomTaskPanes` de la classe `ThisAddIn` quand chaque fenêtre est fermée. Appelez la méthode <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> dans un événement qui est déclenché quand une fenêtre est fermée, tel que <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> ou <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Si vous ne supprimez pas explicitement le volet de tâches personnalisé, les fenêtres Outlook peuvent afficher plusieurs instances du volet de tâches personnalisé. Outlook recycle parfois des fenêtres. Ces fenêtres recyclées conservent les références aux éventuels volets de tâches personnalisés qui leur ont été attachés.  
  
##  <a name="WordAndInfoPath"></a> Word, InfoPath et PowerPoint  
 Word, InfoPath et PowerPoint affichent chaque document dans une fenêtre frame de document différente. Quand vous créez un volet de tâches personnalisé pour ces applications, le volet est associé uniquement à un document spécifique. Si l'utilisateur ouvre un autre document, le volet de tâches personnalisé est masqué jusqu'à ce que le document précédent soit de nouveau visible.  
  
 Pour afficher un volet de tâches personnalisé avec plusieurs documents, créez une nouvelle instance du volet de tâches personnalisé quand l'utilisateur crée un nouveau document ou ouvre un document existant. Pour cela, gérez les événements qui se déclenchent quand un document est créé ou ouvert, puis créez le volet de tâches dans les gestionnaires d'événements. Vous pouvez également gérer les événements de document pour masquer ou afficher les volets de tâches en fonction du document visible.  
  
 Pour associer le volet de tâches à une fenêtre de document spécifique, utilisez la <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> méthode pour créer le volet des tâches, puis passez un <xref:Microsoft.Office.Interop.Word.Window> (pour Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (pour InfoPath) ou <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (pour PowerPoint) à la *fenêtre*paramètre.  
  
### <a name="word-events"></a>Événements Word  
 Pour surveiller l'état des fenêtres de document dans Word, vous pouvez gérer les événements suivants :  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Événements InfoPath  
 Pour surveiller l'état des fenêtres de document dans InfoPath, vous pouvez gérer les événements suivants :  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Événements PowerPoint  
 Pour surveiller l'état des fenêtres de document dans PowerPoint, vous pouvez gérer les événements suivants :  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter un volet Office personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procédure pas à pas : Automatisation d’une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Procédure pas à pas : Synchronisation d’un volet Office personnalisé avec un bouton de ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Procédure : Afficher des volets de tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
