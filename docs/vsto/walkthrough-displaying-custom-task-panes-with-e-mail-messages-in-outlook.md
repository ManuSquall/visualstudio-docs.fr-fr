---
title: 'Procédure pas à pas : Afficher les volets de tâches personnalisés avec des messages électroniques dans Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 322cb9b2136adab37a4506b8332d7d6477ab75ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926580"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Procédure pas à pas : Afficher les volets de tâches personnalisés avec des messages électroniques dans Outlook
  Cette procédure pas à pas montre comment afficher une instance unique d’un volet de tâches personnalisé avec chaque message électronique créé ou ouvert. Les utilisateurs peuvent afficher ou masquer le volet des tâches personnalisé à l’aide d’un bouton situé sur le ruban de chaque message électronique.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Pour afficher un volet des tâches personnalisé avec plusieurs fenêtres d’explorateur ou d’inspecteur, vous devez créer une instance du volet des tâches personnalisé pour chaque fenêtre ouverte. Pour plus d’informations sur le comportement des volets de tâches personnalisés dans les fenêtres Outlook, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  Cette procédure pas à pas présente le code du complément VSTO en petites sections afin de simplifier la présentation de la logique que suit le code.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception de l’interface utilisateur du volet des tâches personnalisé.  
  
-   Création d’une interface utilisateur du ruban personnalisée.  
  
-   Affichage de l’interface ruban personnalisée avec les messages électroniques.  
  
-   Création d’une classe pour gérer les fenêtres d’inspecteur et les volets des tâches personnalisés.  
  
-   Initialisation et nettoyage des ressources utilisées par le complément VSTO.  
  
-   Synchronisation du bouton bascule du ruban avec le volet des tâches personnalisé.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] ou Microsoft Outlook 2010  
  
  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Utiliser des volets de tâches dans Outlook ? ](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="create-the-project"></a>Créer le projet  
 Les volets des tâches personnalisés sont implémentés dans les compléments VSTO. Commencez par créer un projet de complément VSTO pour Outlook.  
  
### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de **Complément Outlook** portant le nom **OutlookMailItemTaskPane**. Utilisez le modèle de projet **Complément Outlook** . Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code *ThisAddIn.cs* ou *ThisAddIn.vb* et ajoute le projet **OutlookMailItemTaskPane** à l’ **Explorateur de solutions**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Concevoir l’interface utilisateur du volet Office personnalisé  
 Il n’existe pas de concepteur visuel pour les volets des tâches personnalisés, mais vous pouvez concevoir un contrôle utilisateur avec l’interface utilisateur de votre choix. Le volet des tâches personnalisé de ce complément VSTO offre une interface utilisateur simple qui contient un contrôle <xref:System.Windows.Forms.TextBox> . À une étape ultérieure de cette procédure, vous ajouterez le contrôle utilisateur au volet des tâches personnalisé.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Pour concevoir l’interface utilisateur du volet des tâches personnalisé  
  
1.  Dans l’ **Explorateur de solutions**, cliquez sur le projet **OutlookMailItemTaskPane** .  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom du nouveau contrôle utilisateur par **TaskPaneControl**, puis cliquez sur **Ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
4.  Sous l’onglet **Contrôles communs** de la **boîte à outils**, faites glisser un contrôle **TextBox** vers le contrôle utilisateur.  
  
## <a name="design-the-user-interface-of-the-ribbon"></a>Concevoir l’interface utilisateur du ruban  
 Un des objectifs de ce complément, VSTO consiste à donner aux utilisateurs un moyen pour masquer ou afficher le volet Office personnalisé à partir du ruban de chaque message électronique. Pour fournir l’interface utilisateur, créez une interface utilisateur du ruban personnalisée qui affiche un bouton bascule sur lequel les utilisateurs peuvent cliquer pour afficher ou masquer le volet des tâches personnalisé.  
  
### <a name="to-create-a-custom-ribbon-ui"></a>Pour créer une interface utilisateur du ruban personnalisée  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)**.  
  
3.  Remplacez le nom du nouveau ruban par **ManageTaskPaneRibbon**, puis cliquez sur **Ajouter**.  
  
     Le fichier *ManageTaskPaneRibbon.cs* ou *ManageTaskPaneRibbon.vb* s’ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Dans le Concepteur de ruban, cliquez sur **group1**.  
  
5.  Dans la fenêtre **Propriétés** , définissez la propriété **Label** sur la valeur **Gestionnaire de volets des tâches**.  
  
6.  Sous l’onglet **Contrôles de ruban Office** de la **boîte à outils**, faites glisser un contrôle ToggleButton dans le groupe **Gestionnaire de volets des tâches** .  
  
7.  Cliquez sur **toggleButton1**.  
  
8.  Dans la fenêtre **Propriétés** , affectez à la propriété **Label** la valeur **Afficher le Volet Office**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Afficher l’interface utilisateur du ruban personnalisée avec les messages électroniques  
 Le volet des tâches personnalisé créé dans cette procédure pas à pas est conçu pour ne s’afficher qu’avec les fenêtres d’inspecteur qui contiennent des messages électroniques. Par conséquent, définissez les propriétés afin d’afficher votre interface utilisateur du ruban personnalisée uniquement avec ces fenêtres.  
  
### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Pour afficher l’interface ruban personnalisée avec les messages électroniques  
  
1.  Dans le Concepteur de ruban, cliquez sur le ruban **ManageTaskPaneRibbon** .  
  
2.  Dans la fenêtre **Propriétés** , cliquez sur la liste déroulante en regard de **RibbonType**, puis sélectionnez **Microsoft.Outlook.Mail.Compose** et **Microsoft.Outlook.Mail.Read**.  
  
## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Créer une classe pour gérer les fenêtres d’inspecteur et les volets de tâches personnalisés  
 Il existe plusieurs cas dans lequel le composant logiciel complément VSTO doit identifier volet des tâches personnalisé est associé à un message électronique spécifique. Il s’agit notamment des cas suivants :  
  
- Lorsque l’utilisateur ferme un message électronique. Dans ce cas, le complément VSTO doit supprimer le volet des tâches personnalisé correspondant afin de garantir que les ressources utilisées par le complément VSTO sont correctement nettoyées.  
  
- Lorsque l’utilisateur ferme le volet des tâches personnalisé. Dans ce cas, le composant logiciel complément VSTO doit mettre à jour l’état du bouton bascule sur le ruban du message électronique.  
  
- Lorsque l’utilisateur clique sur le bouton bascule du ruban. Dans ce cas, le complément VSTO doit masquer ou afficher le volet des tâches correspondant.  
  
  Pour activer le complément VSTO pour effectuer le suivi de volet de tâches personnalisé est associé à chaque message électronique ouvert, créez une classe personnalisée qui encapsule des paires de <xref:Microsoft.Office.Interop.Outlook.Inspector> et <xref:Microsoft.Office.Tools.CustomTaskPane> objets. Cette classe crée un nouvel objet de volet de tâches personnalisé pour chaque message électronique, et il supprime le volet Office personnalisé lorsque le message électronique correspondant est fermé.  
  
### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Pour créer une classe pour gérer les fenêtres d’inspecteur et les volets de tâches personnalisés  
  
1.  Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *ThisAddIn.cs* ou *ThisAddIn.vb* , puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez les instructions suivantes au début du fichier.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Ajoutez le code suivant au fichier *ThisAddIn.cs* ou *ThisAddIn.vb* , en dehors de la classe `ThisAddIn` (pour Visual C#, ajoutez ce code dans l’espace de noms `OutlookMailItemTaskPane` ). La classe `InspectorWrapper` gère une paire d’objets <xref:Microsoft.Office.Interop.Outlook.Inspector> et <xref:Microsoft.Office.Tools.CustomTaskPane> . Vous effectuez la définition de cette classe dans les étapes suivantes.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Ajoutez le constructeur suivant après le code ajouté à l’étape précédente. Ce constructeur crée et initialise un nouveau volet de tâches personnalisé associé à l’objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui est passé. En C#, le constructeur attache également des gestionnaires d’événements à l’événement <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> de l’objet <xref:Microsoft.Office.Interop.Outlook.Inspector> et à l’événement <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> de l’objet <xref:Microsoft.Office.Tools.CustomTaskPane> .  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Ajoutez la méthode suivante après le code ajouté à l’étape précédente. Il s’agit d’un gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> de l’objet <xref:Microsoft.Office.Tools.CustomTaskPane> contenu dans la classe `InspectorWrapper` . Ce code met à jour l’état du bouton bascule chaque fois que l’utilisateur ouvre ou ferme le volet des tâches personnalisé.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Ajoutez la méthode suivante après le code ajouté à l’étape précédente. Cette méthode est un gestionnaire d’événements pour le <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> événements de la <xref:Microsoft.Office.Interop.Outlook.Inspector> objet qui contient le message électronique actuel. Le Gestionnaire d’événements libère des ressources lorsque le message électronique est fermé. Il supprime également le volet des tâches personnalisé actuel de la collection `CustomTaskPanes` . Cela permet d’éviter que plusieurs instances du volet Office personnalisé lorsque le message électronique suivant est ouvert.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Ajoutez le code suivant après le code ajouté à l’étape précédente. À une étape ultérieure de cette procédure, vous appellerez cette propriété à partir d’une méthode dans l’interface utilisateur du ruban personnalisée pour afficher ou masquer le volet des tâches personnalisé.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Initialiser et nettoyer les ressources utilisées par le complément  
 Ajoutez du code à la classe `ThisAddIn` pour initialiser le complément VSTO lorsqu’il est chargé et pour nettoyer les ressources utilisées par le complément VSTO lorsqu’il est déchargé. Vous initialisez le module additionnel VSTO en définissant un gestionnaire d’événements pour le <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> événement et en passant de tous les messages électroniques existants à ce gestionnaire d’événements. Lorsque le complément VSTO est déchargé, détachez le gestionnaire d’événements et nettoyez les objets utilisés par le complément VSTO.  
  
### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Pour initialiser et nettoyer les ressources utilisées par le complément VSTO  
  
1. Dans le fichier *ThisAddIn.cs* ou *ThisAddIn.vb* , localisez la définition de la classe `ThisAddIn` .  
  
2. Ajoutez les déclarations suivantes à la classe `ThisAddIn` :  
  
   - Le champ `inspectorWrappersValue` contient tous les objets <xref:Microsoft.Office.Interop.Outlook.Inspector> et `InspectorWrapper` gérés par le complément VSTO.  
  
   - Le champ `inspectors` conserve une référence à la collection de fenêtres Inspecteur de l'instance Outlook actuelle. Cette référence empêche le garbage collector de libérer la mémoire qui contient le gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> , que vous allez déclarer à l’étape suivante.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3. Remplacez la méthode `ThisAddIn_Startup` par le code suivant. Ce code attache un gestionnaire d’événements à l’événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> et passe chaque objet <xref:Microsoft.Office.Interop.Outlook.Inspector> existant au gestionnaire d’événements. Si l’utilisateur charge le module additionnel VSTO après que Outlook est déjà en cours d’exécution, le composant logiciel complément VSTO utilise ces informations pour créer des volets de tâches personnalisés pour tous les messages électroniques qui sont déjà ouverts.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4. Remplacez la méthode `ThisAddIn_ShutDown` par le code suivant. Ce code détache le gestionnaire d’événements <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> et nettoie les objets utilisés par le complément VSTO.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5. Ajoutez le gestionnaire d’événements <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> suivant à la classe `ThisAddIn` . Si un nouveau <xref:Microsoft.Office.Interop.Outlook.Inspector> contient un message électronique, la méthode crée une instance d’un nouveau `InspectorWrapper` objet pour gérer la relation entre le message électronique et le volet des tâches correspondant.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6. Ajoutez la propriété suivante à la classe `ThisAddIn` . Cette propriété expose le champ `inspectorWrappersValue` privé au code en dehors de la classe `ThisAddIn` .  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 Générez votre projet pour vous assurer qu’il est compilé sans erreur.  
  
### <a name="to-build-your-project"></a>Pour générer votre projet  
  
1.  Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **OutlookMailItemTaskPane** , puis cliquez sur **Générer**. Vérifiez que le projet se compile sans erreur.  
  
## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchroniser le bouton bascule du ruban avec le volet Office personnalisé  
 Le bouton semble enfoncé lorsque le volet Office est visible, et il semble être désactivé lorsque le volet Office est masqué. Pour synchroniser l’état du bouton avec le volet des tâches personnalisé, modifiez le gestionnaire d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule.  
  
### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Pour synchroniser le volet des tâches personnalisé avec le bouton bascule  
  
1.  Dans le Concepteur de ruban, double-cliquez sur le bouton bascule **Afficher le Volet Office** .  
  
     Visual Studio génère automatiquement un gestionnaire d’événements nommé `toggleButton1_Click`, qui gère l’événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Visual Studio ouvre également le fichier *ManageTaskPaneRibbon.cs* ou *ManageTaskPaneRibbon.vb* dans l’éditeur de code  
  
2.  Ajoutez les instructions suivantes au début du fichier *ManageTaskPaneRibbon.cs* ou *ManageTaskPaneRibbon.vb* .  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Remplacez le gestionnaire d'événements `toggleButton1_Click` par le code suivant. Lorsque l’utilisateur clique sur le bouton bascule, cette méthode masque ou affiche le volet des tâches personnalisé associé à la fenêtre d’inspecteur actuelle.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="test-the-project"></a>Le projet de test  
 Lorsque vous commencez à déboguer le projet, Outlook s’ouvre et le complément VSTO est chargé. Le composant logiciel complément VSTO affiche une instance unique du volet des tâches personnalisé avec chaque message électronique qui est ouvert. Créer plusieurs nouveaux e-mails pour tester le code.  
  
### <a name="to-test-the-vsto-add-in"></a>Pour tester le complément VSTO  
  
1. Appuyez sur **F5**.  
  
2. Dans Outlook, cliquez sur **New** pour créer un nouveau message électronique.  
  
3. Dans le ruban du message électronique, cliquez sur le **Add-Ins** onglet, puis cliquez sur le **afficher le volet Office** bouton.  
  
    Vérifiez que le titre, un volet de tâches **Mon volet des tâches** s’affiche avec le message électronique.  
  
4. Dans le volet des tâches, tapez **Premier volet des tâches** dans la zone de texte.  
  
5. Fermez le volet des tâches.  
  
    Vérifiez que l’état du bouton **Afficher le volet Office** change de sorte qu’il ne soit plus enfoncé.  
  
6. Cliquez de nouveau sur le bouton **Afficher le volet Office** .  
  
    Assurez-vous que le volet des tâches s’ouvre et que la zone de texte contient encore la chaîne **Premier volet des tâches**.  
  
7. Dans Outlook, cliquez sur **New** pour créer un deuxième message électronique.  
  
8. Dans le ruban du message électronique, cliquez sur le **Add-Ins** onglet, puis cliquez sur le **afficher le volet Office** bouton.  
  
    Vérifiez qu’un volet de tâches avec le titre **Mon volet des tâches** s’affiche avec le message électronique, et la zone de texte dans ce volet de tâches est vide.  
  
9. Dans le volet des tâches, tapez **Second volet des tâches** dans la zone de texte.  
  
10. Placer le focus sur le premier message de courrier électronique.  
  
     Vérifiez que le volet des tâches qui est associé à ce message électronique affiche toujours **premier volet des tâches** dans la zone de texte.  
  
    Ce complément VSTO gère également des scénarios plus avancés que vous pouvez tester. Par exemple, vous pouvez tester le comportement lors de l’affichage des messages électroniques à l’aide de la **élément suivant** et **élément précédent** boutons. Vous pouvez également tester le comportement lorsque vous déchargez le complément, VSTO, ouvrez plusieurs messages électroniques et puis rechargez le VSTO Add-in.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur la création de volets Office personnalisés, consultez les rubriques suivantes :  
  
-   Créer un volet Office personnalisé dans un complément VSTO pour une autre application. Pour plus d’informations sur les applications qui prennent en charge des volets de tâches personnalisés, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Automatiser une application Microsoft Office à l’aide d’un volet des tâches personnalisé. Pour plus d’informations, consultez [Procédure pas à pas : Automatiser une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Créer un bouton du ruban dans Excel pour masquer ou afficher un volet des tâches personnalisé. Pour plus d’informations, consultez [Procédure pas à pas : Synchroniser un volet Office personnalisé avec un bouton de ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Volets Office personnalisés](../vsto/custom-task-panes.md)   
 [Guide pratique pour Ajouter un volet Office personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procédure pas à pas : Automatiser une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Procédure pas à pas : Synchroniser un volet Office personnalisé avec un bouton de ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)   
 [Accéder au ruban lors de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)  
