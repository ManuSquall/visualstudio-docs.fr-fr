---
title: "Comment&#160;: prot&#233;ger des parties de documents &#224; l&#39;aide de contr&#244;les de contenu | Microsoft Docs"
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
  - "contrôles de contenu (développement Office dans Visual Studio), protéger les documents"
  - "protection des documents (développement Office dans Visual Studio)"
  - "GroupContentControl"
  - "protection partielle des documents (développement Office dans Visual Studio)"
  - "autorisations restreintes (développement Office dans Visual Studio)"
  - "Word (développement Office dans Visual Studio), protection partielle de documents"
  - "Word (développement Office dans Visual Studio), autorisations restreintes"
ms.assetid: 50d7286a-7746-446f-8eef-06ceeadc94d0
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Comment&#160;: prot&#233;ger des parties de documents &#224; l&#39;aide de contr&#244;les de contenu
  Quand vous protégez une partie d'un document, vous empêchez les utilisateurs de modifier ou de supprimer le contenu dans cette partie du document.  Il existe plusieurs manières de protéger des parties d'un document Microsoft Office Word à l'aide de contrôles de contenu :  
  
-   Vous pouvez protéger un contrôle de contenu.  
  
-   Vous pouvez protéger une partie d'un document qui ne se trouve pas dans un contrôle de contenu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Protection d'un contrôle de contenu  
 Vous pouvez empêcher les utilisateurs de modifier ou supprimer un contrôle de contenu en définissant les propriétés du contrôle dans un projet au niveau du document, au moment du design ou au moment de l'exécution.  
  
 Vous pouvez également protéger les contrôles de contenu que vous ajoutez à un document au moment de l'exécution à l'aide d'un projet de complément VSTO.  Pour plus d'informations, consultez [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
#### Pour protéger un contrôle de contenu au moment du design  
  
1.  Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez le contrôle de contenu à protéger.  
  
2.  Dans la fenêtre **Propriétés**, définissez l'une des propriétés suivantes, ou les deux :  
  
    -   Pour empêcher les utilisateurs de modifier le contrôle, affectez à **LockContents** la valeur **True**.  
  
    -   Pour empêcher les utilisateurs de supprimer le contrôle, affectez à **LockContentControl** la valeur **True**.  
  
3.  Cliquez sur **OK**.  
  
#### Pour protéger un contrôle de contenu au moment de l'exécution  
  
1.  Affectez à la propriété `LockContents` du contrôle de contenu la valeur **true** pour empêcher les utilisateurs de modifier le contrôle, et affectez à la propriété `LockContentControl` la valeur **true** pour empêcher les utilisateurs de supprimer le contrôle.  
  
     L'exemple de code suivant illustre l'utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet au niveau du document.  Pour exécuter ce code, ajoutez\-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#2)]  
  
     L'exemple de code suivant illustre l'utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet de complément VSTO.  Pour exécuter ce code, ajoutez\-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_WordAddInDynamicControls#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#14)]  
  
## Protection d'une partie d'un document qui ne se trouve pas dans un contrôle de contenu  
 Vous pouvez empêcher les utilisateurs de modifier une zone d'un document en la plaçant dans <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Cela s'avère utile dans les scénarios suivant :  
  
-   Vous souhaitez protéger une zone qui ne contient pas de contrôles de contenu.  
  
-   Vous souhaitez protéger une zone qui contient déjà des contrôles de contenu, mais le texte ou les autres éléments que vous souhaitez protéger ne se trouvent pas dans les contrôles de contenu.  
  
> [!NOTE]  
>  Si vous créez un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient des contrôles de contenu incorporés, ces contrôles ne sont pas protégés automatiquement.  Pour empêcher les utilisateurs de modifier un contrôle de contenu incorporé, utilisez la propriété **LockContents** du contrôle.  
  
#### Pour protéger une zone d'un document au moment du design  
  
1.  Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez la zone à protéger.  
  
2.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher.  Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Dans le groupe **Contrôles**, cliquez sur le bouton de liste déroulante **Groupe**, puis cliquez sur **Groupe**.  
  
     Un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient la zone protégée est généré automatiquement dans la classe `ThisDocument` de votre projet.  Une bordure qui représente le contrôle de groupe est visible au moment du design. Toutefois, aucune bordure n'est visible au moment de l'exécution.  
  
#### Pour protéger une zone d'un document au moment de l'exécution  
  
1.  Sélectionnez par programmation la zone à protéger, puis appelez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> pour créer <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     L'exemple de code suivant pour un projet au niveau du document ajoute du texte au premier paragraphe du document, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Pour exécuter ce code, ajoutez\-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#1)]  
  
     L'exemple de code suivant pour un projet de complément VSTO ajoute du texte au premier paragraphe du document actif, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Pour exécuter ce code, ajoutez\-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_WordAddInDynamicControls#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#15)]  
  
## Voir aussi  
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  