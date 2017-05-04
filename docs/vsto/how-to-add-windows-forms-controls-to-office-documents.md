---
title: "Comment&#160;: ajouter des contr&#244;les Windows Forms &#224; des documents Office | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents Office (développement Office dans Visual Studio), contrôles Windows Forms"
  - "contrôles Windows Forms (développement Office dans Visual Studio), ajouter"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Comment&#160;: ajouter des contr&#244;les Windows Forms &#224; des documents Office
  Vous pouvez ajouter des contrôles Windows Forms à des documents Microsoft Office Excel et Microsoft Office Word au moment du design dans les projets au niveau du document.  Au moment de l'exécution, vous pouvez ajouter des contrôles dans les personnalisations au niveau du document et les compléments VSTO.  Par exemple, vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> à votre feuille de calcul pour que les utilisateurs puissent sélectionner une option dans une liste.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles au moment du design](#designtime)  
  
-   [Ajout de contrôles au moment de l'exécution dans des projets au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles au moment de l'exécution dans des compléments VSTO](#runtimeaddin)  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner la démonstration vidéo associée, consultez les informations indiquant [comment ajouter des contrôles à la surface d'un document au moment de l'exécution](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Ajout de contrôles au moment du design  
 Il existe plusieurs façons d'ajouter des contrôles Windows Forms au document dans un projet au niveau du document au moment du design.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Pour faire glisser un contrôle Windows Forms vers le document  
  
1.  Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, cliquez sur le contrôle à ajouter, puis faites\-le glisser vers le document.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
#### Pour dessiner un contrôle Windows Forms sur le document  
  
1.  Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, cliquez sur le contrôle à ajouter.  
  
3.  Dans le document, cliquez à l'endroit où l'angle supérieur gauche du contrôle doit se trouver, puis faites glisser le curseur vers l'endroit où l'angle inférieur droit du contrôle doit se trouver.  
  
     Le contrôle est ajouté au document avec l'emplacement et la taille spécifiés.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
#### Pour ajouter un contrôle Windows Forms au document en cliquant une fois sur le contrôle  
  
1.  Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, cliquez sur le contrôle à ajouter  
  
3.  Dans le document, cliquez à l'emplacement où vous souhaitez ajouter le contrôle.  
  
     Le contrôle est ajouté au document avec la taille par défaut.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
#### Pour ajouter un contrôle Windows Forms au document en double\-cliquant sur le contrôle  
  
1.  Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, double\-cliquez sur le contrôle à ajouter.  
  
     Le contrôle est ajouté au document, au centre de ce dernier ou du volet actif.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
#### Pour ajouter un contrôle Windows Forms au document en appuyant sur la touche Entrée  
  
1.  Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, cliquez sur le contrôle à ajouter, puis appuyez sur la touche Entrée.  
  
     Le contrôle est ajouté au document, au centre de ce dernier ou du volet actif.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
##  <a name="runtimedoclevel"></a> Ajout de contrôles au moment de l'exécution dans des projets au niveau du document  
 Vous pouvez ajouter par programmation des contrôles Windows Forms à un document au moment de l'exécution.  Dans Word, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> de la classe `ThisDocument`.  Dans Excel, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> d'une classe `Sheet`*n*.  Chaque méthode a plusieurs surcharges qui vous permettent de spécifier l'emplacement du contrôle de différentes façons.  
  
 Quand vous ajoutez un contrôle Windows Forms à un document au moment de l'exécution, le contrôle n'est pas conservé dans le document après la fermeture de ce dernier.  Vous pouvez recréer le contrôle à la prochaine ouverture du document.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Pour ajouter un contrôle Windows Forms au moment de l'exécution  
  
1.  Utilisez une méthode portant le nom Add\<*classe du contrôle*\> \(où *classe du contrôle* est le nom de la classe du contrôle Windows Forms que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
     L'exemple de code suivant montre comment ajouter <xref:Microsoft.Office.Tools.Excel.Controls.Button> à la cellule **C5** de `Sheet1` dans un projet au niveau du document pour Excel.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> Ajout de contrôles au moment de l'exécution dans des compléments VSTO  
 Vous pouvez ajouter des contrôles Windows Forms par programmation à un document ouvert au moment de l'exécution.  Tout d'abord, générez un élément hôte basé sur un document ouvert ou une feuille de calcul ouverte.  Dans Word, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> du nouvel élément hôte.  Dans Excel, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> du nouvel élément hôte.  Chaque méthode a plusieurs surcharges qui vous permettent de spécifier l'emplacement du contrôle de différentes façons.  
  
 Quand vous ajoutez un contrôle Windows Forms à un document au moment de l'exécution, le contrôle n'est pas conservé dans le document après la fermeture de ce dernier.  Vous pouvez recréer le contrôle à la prochaine ouverture du document.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Pour plus d'informations sur la génération d'éléments hôtes dans les projets de complément VSTO, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Pour ajouter un contrôle Windows Forms au moment de l'exécution  
  
1.  Utilisez une méthode portant le nom Add\<*classe du contrôle*\> \(où *classe du contrôle* est le nom de la classe du contrôle Windows Forms que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
    > [!NOTE]  
    >  Dans les projets de complément VSTO qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez ajouter une référence à l'assembly Microsoft.Office.Tools.Excel.v4.0.Utilities.dll ou Microsoft.Office.Tools.Word.v4.0.Utilities.dll pour pouvoir accéder aux méthodes Add\<*classe du contrôle*\>.  
  
     L'exemple de code suivant montre comment ajouter <xref:Microsoft.Office.Tools.Word.Controls.Button> au premier paragraphe du document actif en utilisant un complément Word VSTO.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## Voir aussi  
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  