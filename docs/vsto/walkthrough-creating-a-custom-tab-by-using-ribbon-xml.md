---
title: 'Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b92c3ff12ab284ac208b012f3e03975b4eddd7c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871986"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban
  Cette procédure pas à pas montre comment créer un onglet de ruban personnalisé à l’aide de la **ruban (XML)** élément.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de boutons à la **Add-Ins** onglet. Le **Add-Ins** onglet est l’onglet par défaut qui est défini dans le fichier XML du ruban.  
  
-   Automatisation de Microsoft Office Word en utilisant les boutons sur le **Add-Ins** onglet.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-the-project"></a>Créer le projet  
 La première étape consiste à créer un projet de complément VSTO Word. Vous personnaliserez ultérieurement le **Add-Ins** onglet de ce document.  
  
### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un **complément Word** projet portant le nom **MyRibbonAddIn**.  
  
     Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ouvre le **ThisAddIn.cs** ou **ThisAddIn.vb** fichier de code et ajoute le **MyRibbonAddIn** de projet à **l’Explorateur de solutions**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>Créer l’onglet Compléments VSTO  
 Pour créer le **Add-Ins** onglet, ajoutez un **ruban (XML)** élément à votre projet. À une étape ultérieure de cette procédure pas à pas, vous ajouterez des boutons à cet onglet.  
  
### <a name="to-create-the-add-ins-tab"></a>Pour créer l’onglet Compléments  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **ruban (XML)**.  
  
3.  Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.  
  
     Le **MyRibbon.cs** ou **MyRibbon.vb** fichier s’ouvre dans le concepteur. Un fichier XML nommé **MyRibbon.xml** est également ajouté à votre projet.  
  
4.  Dans **l’Explorateur de solutions**, avec le bouton droit **ThisAddin.cs** ou **ThisAddin.vb**, puis cliquez sur **afficher le Code**.  
  
5.  Ajoutez le code suivant à la classe **ThisAddin** . Ce code substitue la méthode `CreateRibbonExtensibilityObject` et retourne la classe Ribbon XML à l'application Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Dans **l’Explorateur de solutions**, avec le bouton droit le **MyRibbonAddIn** de projet, puis cliquez sur **Build**. Vérifiez que le projet se génère sans erreur.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Ajouter des boutons à l’onglet Compléments  
 L’objectif de ce complément VSTO est de permettre aux utilisateurs d’ajouter du texte réutilisable et un tableau spécifique au document actif. Pour fournir l’interface utilisateur, ajoutez deux boutons à la **Add-Ins** onglet en modifiant le fichier XML du ruban. À une étape ultérieure de cette procédure pas à pas, vous définirez des méthodes de rappel pour les boutons. Pour plus d’informations sur le fichier XML du ruban, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>Pour ajouter des boutons à l’onglet Compléments  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyRibbon.xml** puis cliquez sur **Open**.  
  
2.  Remplacez le contenu de la **onglet** élément avec le code XML suivant. Ce code XML remplace l’étiquette du groupe de contrôle par défaut à **contenu**, et ajoute deux nouveaux boutons avec les étiquettes **Insert Text** et **insérer un tableau**.  
  
    ```xml  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automate-the-document-by-using-the-buttons"></a>Automatiser le document en utilisant les boutons  
 Vous devez ajouter `onAction` méthodes de rappel pour le **Insert Text** et **insérer un tableau** boutons permettant d’effectuer des actions lorsque l’utilisateur clique dessus. Pour plus d’informations sur les méthodes de rappel pour les contrôles de ruban, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Pour ajouter des méthodes de rappel pour les boutons  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyRibbon.cs** ou **MyRibbon.vb**, puis cliquez sur **Open**.  
  
2.  Ajoutez le code suivant en haut de la **MyRibbon.cs** ou **MyRibbon.vb** fichier. Ce code crée un alias pour l'espace de noms <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Ajoutez la méthode suivante à la classe `MyRibbon` . Il s’agit d’une méthode de rappel pour le **Insert Text** bouton qui ajoute une chaîne au document actif à l’emplacement actuel du curseur.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Ajoutez la méthode suivante à la classe `MyRibbon` . Il s’agit d’une méthode de rappel pour le **insérer un tableau** bouton qui ajoute un tableau au document actif à l’emplacement actuel du curseur.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Test du complément VSTO  
 Lorsque vous exécutez le projet, Word s’ouvre et l’onglet nommé **Add-Ins** apparaît sur le ruban. Cliquez sur le **Insert Text** et **insérer un tableau** des boutons de la **Add-Ins** onglet pour tester le code.  
  
### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO  
  
1.  Appuyez sur **F5** pour exécuter votre projet.  
  
2.  Vérifiez que le **Add-Ins** onglet est visible sur le ruban.  
  
3.  Cliquez sur l'onglet **Compléments** .  
  
4.  Vérifiez que le **contenu** groupe est visible sur le ruban.  
  
5.  Cliquez sur le **Insert Text** situé dans le **contenu** groupe.  
  
     Une chaîne est ajoutée au document à l'emplacement actuel du curseur.  
  
6.  Cliquez sur le **insérer un tableau** situé dans le **contenu** groupe.  
  
     Un tableau est ajouté au document à l'emplacement actuel du curseur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :  
  
-   Personnaliser le ruban d’une autre application Office. Pour plus d’informations sur les applications qui prennent en charge la personnalisation du ruban, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
-   Personnaliser le ruban d’une application Office à l’aide du Concepteur de ruban. Pour plus d'informations, consultez [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Créer un volet Actions personnalisé. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
-   Personnaliser l'interface utilisateur de Microsoft Office Outlook à l'aide de zones de formulaire Outlook. Pour plus d’informations, consultez [Procédure pas à pas : Concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
