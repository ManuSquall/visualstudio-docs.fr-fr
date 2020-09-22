---
title: 'Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML'
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
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839381"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML
  Cette procédure pas à pas montre comment créer un onglet de ruban personnalisé à l’aide de l’élément **Ruban (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout de boutons à l’onglet **compléments** . L’onglet **compléments** est l’onglet par défaut qui est défini dans le fichier XML du ruban.

- L’automatisation de Microsoft Office Word à l’aide des boutons de l’onglet **compléments** .

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de complément VSTO Word. Vous allez personnaliser ultérieurement l’onglet **compléments** de ce document.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet **de complément Word** portant le nom **MyRibbonAddIn**.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn. vb** et ajoute le projet **MyRibbonAddIn** à **Explorateur de solutions**.

## <a name="create-the-vsto-add-ins-tab"></a>Créer l’onglet Compléments VSTO
 Pour créer l’onglet **compléments** , ajoutez un élément **Ruban (XML)** à votre projet. À une étape ultérieure de cette procédure pas à pas, vous ajouterez des boutons à cet onglet.

### <a name="to-create-the-add-ins-tab"></a>Pour créer l’onglet Compléments

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (XML)**.

3. Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.

     Le fichier **MyRibbon.cs** ou **MyRibbon. vb** s’ouvre dans le concepteur. Un fichier XML nommé **MyRibbon.xml** est également ajouté à votre projet.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **ThisAddIn.cs** ou sur **ThisAddIn. vb**, puis cliquez sur **afficher le code**.

5. Ajoutez le code suivant à la classe **ThisAddin** . Ce code substitue la méthode `CreateRibbonExtensibilityObject` et retourne la classe Ribbon XML à l'application Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **MyRibbonAddIn** , puis cliquez sur **générer**. Vérifiez que le projet se génère sans erreur.

## <a name="add-buttons-to-the-add-ins-tab"></a>Ajouter des boutons à l’onglet Compléments
 L'objectif de ce complément VSTO est de permettre aux utilisateurs d'ajouter du texte réutilisable et un tableau spécifique au document actif. Pour fournir l’interface utilisateur, ajoutez deux boutons à l’onglet **compléments** en modifiant le fichier XML du ruban. À une étape ultérieure de cette procédure pas à pas, vous définirez des méthodes de rappel pour les boutons. Pour plus d’informations sur le fichier XML du ruban, consultez [Ruban XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Pour ajouter des boutons à l’onglet Compléments

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MyRibbon.xml** , puis cliquez sur **ouvrir**.

2. Remplacez le contenu de l’élément **Tab** par le code XML suivant. Ce code XML remplace l’étiquette du groupe de contrôles par défaut par du **contenu**et ajoute deux nouveaux boutons avec les étiquettes **Insérer du texte** et insérer un **tableau**.

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

## <a name="automate-the-document-by-using-the-buttons"></a>Automatiser le document à l’aide des boutons
 Vous devez ajouter `onAction` des méthodes de rappel pour les boutons **Insérer du texte** et **Insérer un tableau** pour effectuer des actions lorsque l’utilisateur clique dessus. Pour plus d’informations sur les méthodes de rappel pour les contrôles du ruban, consultez [Ruban XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Pour ajouter des méthodes de rappel pour les boutons

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MyRibbon.cs** ou sur **MyRibbon. vb**, puis cliquez sur **ouvrir**.

2. Ajoutez le code suivant en haut du fichier **MyRibbon.cs** ou **MyRibbon. vb** . Ce code crée un alias pour l'espace de noms <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Ajoutez la méthode suivante à la classe `MyRibbon`. Il s’agit d’une méthode de rappel pour le bouton **Insérer un texte** qui ajoute une chaîne au document actif à l’emplacement actuel du curseur.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Ajoutez la méthode suivante à la classe `MyRibbon`. Il s’agit d’une méthode de rappel pour le bouton **Insérer une table** qui ajoute une table au document actif à l’emplacement actuel du curseur.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Test du complément VSTO
 Quand vous exécutez le projet, Word s’ouvre et l’onglet **compléments** s’affiche sur le ruban. Cliquez sur les boutons **Insérer du texte** et **Insérer un tableau** sous l’onglet **compléments** pour tester le code.

### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO

1. Appuyez sur **F5** pour exécuter votre projet.

2. Vérifiez que l’onglet **compléments** est visible sur le ruban.

3. Cliquez sur l'onglet **Compléments** .

4. Confirmez que le groupe de **contenu** est visible sur le ruban.

5. Cliquez sur le bouton **Insérer un texte** dans le groupe de **contenu** .

     Une chaîne est ajoutée au document à l'emplacement actuel du curseur.

6. Cliquez sur le bouton **Insérer une table** dans le groupe de **contenu** .

     Un tableau est ajouté au document à l'emplacement actuel du curseur.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :

- Personnaliser le ruban d’une autre application Office. Pour plus d’informations sur les applications qui prennent en charge la personnalisation du ruban, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

- Personnaliser le ruban d’une application Office à l’aide du concepteur de ruban. Pour plus d'informations, consultez [Ribbon Designer](../vsto/ribbon-designer.md).

- Créer un volet Actions personnalisé. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

- Personnaliser l'interface utilisateur de Microsoft Office Outlook à l'aide de zones de formulaire Outlook. Pour plus d’informations, consultez [procédure pas à pas : concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
