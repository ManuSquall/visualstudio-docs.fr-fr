---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un onglet personnalis&#233; &#224; l&#39;aide d&#39;un &#233;l&#233;ment XML Ribbon"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Personnalisé (onglet) (développement Office dans Visual Studio)"
  - "personnaliser le ruban, onglets de ruban personnalisés, onglets"
  - "ruban (développement Office dans Visual Studio), personnaliser"
  - "ruban (développement Office dans Visual Studio), onglets"
  - "ruban (développement Office dans Visual Studio), XML"
  - "XML (développement Office dans Visual Studio), ruban"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un onglet personnalis&#233; &#224; l&#39;aide d&#39;un &#233;l&#233;ment XML Ribbon
  Cette procédure pas à pas montre comment créer un onglet de ruban personnalisé à l'aide de l'élément **Ruban \(XML\)**.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de boutons à l'onglet **Compléments**.  L'onglet **Compléments** est l'onglet par défaut défini dans le fichier XML du ruban.  
  
-   Automatisation de Microsoft Office Word à l'aide des boutons de l'onglet **Compléments**.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Création du projet  
 La première étape consiste à créer un projet de complément VSTO Word.  Vous personnaliserez ultérieurement l'onglet **Compléments** de ce document.  
  
#### Pour créer un projet  
  
1.  Créer un projet **Complément Word** et nommez\-le MyRibbonAddIn.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb** et ajoute le projet **MyRibbonAddIn** à l'**Explorateur de solutions**.  
  
## Création de l'onglet Compléments VSTO  
 Pour créer l'onglet **Compléments**, ajoutez un élément **Ruban \(XML\)** à votre projet.  À une étape ultérieure de cette procédure pas à pas, vous ajouterez des boutons à cet onglet.  
  
#### Pour créer l'onglet Compléments  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Ruban \(XML\)**.  
  
3.  Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.  
  
     Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le concepteur.  Un fichier XML nommé **MyRibbon.xml**est également ajouté à votre projet.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisAddin.cs** ou sur **ThisAddin.vb**, puis cliquez sur **Afficher le code**.  
  
5.  Ajoutez le code suivant à la classe **ThisAddin**.  Ce code substitue la méthode CreateRibbonExtensibilityObject et retourne la classe Ribbon XML à l'application Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **MyRibbonAddIn**, puis cliquez sur **Générer**.  Vérifiez que le projet se génère sans erreur.  
  
## Ajout de boutons à l'onglet Compléments  
 L'objectif de ce complément VSTO est de permettre aux utilisateurs d'ajouter du texte réutilisable et un tableau spécifique au document actif.  Pour fournir l'interface utilisateur, ajoutez deux boutons à l'onglet **Compléments** en modifiant le fichier XML du ruban.  À une étape ultérieure de cette procédure pas à pas, vous définirez des méthodes de rappel pour les boutons.  Pour plus d'informations sur le fichier XML du ruban, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
#### Pour ajouter des boutons à l'onglet Compléments  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **MyRibbon.xml**, puis cliquez sur **Ouvrir**.  
  
2.  Remplacez le contenu de l'élément **tab** par le code XML suivant :  Ce code XML remplace l'étiquette du groupe de contrôles par défaut par **Content** et ajoute deux nouveaux boutons nommés **Insert Text** et **Insert Table**.  
  
    ```  
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
  
## Automatisation du document à l'aide des boutons  
 Vous devez ajouter des méthodes de rappel `onAction` pour que les boutons **Insert Text** et **Insert Table** exécutent des actions lorsque l'utilisateur clique dessus.  Pour plus d'informations sur les méthodes de rappel pour les contrôles du ruban, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
#### Pour ajouter des méthodes de rappel pour les boutons  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **MyRibbon.cs** ou sur **MyRibbon.vb**, puis cliquez sur **Ouvrir**.  
  
2.  Ajoutez le code suivant en haut du fichier **MyRibbon.cs** ou **MyRibbon.vb**.  Ce code crée un alias pour l'espace de noms <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  Ajoutez la méthode suivante à la classe `MyRibbon`.  Il s'agit d'une méthode de rappel pour le bouton **Insert Text** qui ajoute une chaîne au document actif à l'emplacement actuel du curseur.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  Ajoutez la méthode suivante à la classe `MyRibbon`.  Il s'agit d'une méthode de rappel pour le bouton **Insert Table** qui ajoute un tableau au document actif à l'emplacement actuel du curseur.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## Test du complément VSTO  
 Lorsque vous exécutez le projet, Word s'ouvre et l'onglet nommé **Compléments** apparaît sur le ruban.  Cliquez sur les boutons **Insert Text** et **Insert Table** de l'onglet **Compléments** pour tester le code.  
  
#### Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que l'onglet **Compléments** est visible sur le ruban.  
  
3.  Cliquez sur l'onglet **Compléments**.  
  
4.  Vérifiez que le groupe **Content** est visible sur le ruban.  
  
5.  Cliquez sur le bouton **Insert Text** situé dans le groupe **Content**.  
  
     Une chaîne est ajoutée au document à l'emplacement actuel du curseur.  
  
6.  Cliquez sur le bouton **Insert Table** situé dans le groupe **Content**.  
  
     Un tableau est ajouté au document à l'emplacement actuel du curseur.  
  
## Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :  
  
-   Personnaliser le ruban d'une autre application Office.  Pour plus d'informations sur les applications qui prennent en charge la personnalisation du ruban, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
-   Personnaliser le ruban d'une application Office à l'aide du Concepteur de ruban.  Pour plus d'informations, consultez [Concepteur de ruban](../vsto/ribbon-designer.md).  
  
-   Créer un volet Actions personnalisé.  Pour plus d'informations, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
-   Personnaliser l'interface utilisateur de Microsoft Office Outlook à l'aide de zones de formulaire Outlook.  Pour plus d'informations, consultez [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  