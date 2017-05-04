---
title: "Rendre des contr&#244;les dynamiques persistants dans des documents Office | Microsoft Docs"
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
  - "documents Office (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents Office (développement Office dans Visual Studio), contrôles hôtes"
  - "contrôles (développement Office dans Visual Studio), persistance dans le document"
  - "contrôles Windows Forms (développement Office dans Visual Studio), persistance dans le document"
  - "documents (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents (développement Office dans Visual Studio), contrôles hôtes"
  - "contrôles hôtes (développement Office dans Visual Studio), persistance dans le document"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Rendre des contr&#244;les dynamiques persistants dans des documents Office
  Les contrôles ajoutés au moment de l’exécution ne sont pas rendus persistants lorsque le document ou le classeur est enregistré et fermé. Le comportement exact est différent pour les contrôles hôtes et les contrôles Windows Forms. Dans les deux cas, vous pouvez ajouter du code à votre solution pour recréer les contrôles lorsque l’utilisateur ouvre de nouveau le document.  
  
 Les contrôles que vous ajoutez aux documents au moment de l’exécution sont appelés *contrôles dynamiques*. Pour plus d’informations sur les contrôles dynamiques, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Persistance des contrôles hôtes dans le document  
 Lorsqu’un document est enregistré puis fermé, tous les contrôles hôtes dynamiques sont supprimés du document. Seuls les objets Office natifs sous\-jacents restent en arrière\-plan. Par exemple, un contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject> devient un <xref:Microsoft.Office.Interop.Excel.ListObject>. Les objets Office natifs ne sont pas liés aux événements de contrôle hôte, et ils n’ont pas la fonctionnalité de liaison des données du contrôle hôte.  
  
 Le tableau suivant répertorie l’objet Office natif laissé en arrière\-plan dans un document pour chaque type de contrôle hôte.  
  
|Type de contrôle hôte|Type d’objet Office natif|  
|---------------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### Recréation de contrôles hôtes dynamiques lors de l’ouverture de documents  
 Vous pouvez recréer des contrôles hôtes dynamiques à la place des contrôles natifs existants chaque fois qu’un utilisateur ouvre le document. Créer des contrôles hôtes de cette manière lors de l’ouverture d’un document simule l’expérience que les utilisateurs peuvent attendre.  
  
 Pour recréer un contrôle hôte pour Word, ou un contrôle hôte <xref:Microsoft.Office.Tools.Excel.NamedRange> ou <xref:Microsoft.Office.Tools.Excel.ListObject> pour Excel, utilisez une méthode `Add`\<*control class*\> d’un objet <xref:Microsoft.Office.Tools.Excel.ControlCollection> ou <xref:Microsoft.Office.Tools.Word.ControlCollection>. Utilisez une méthode qui a un paramètre pour l’objet Office natif.  
  
 Par exemple, si vous souhaitez créer un contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject> à partir d’un <xref:Microsoft.Office.Interop.Excel.ListObject> natif existant lors de l’ouverture du document, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> et transmettez le <xref:Microsoft.Office.Interop.Excel.ListObject> existant. L’exemple de code suivant montre cette opération dans un projet au niveau du document pour Excel. Le code recrée un <xref:Microsoft.Office.Tools.Excel.ListObject> dynamique qui est basé sur un <xref:Microsoft.Office.Interop.Excel.ListObject> existant nommé `MyListObject` dans la classe `Sheet1`.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### Recréation de graphiques  
 Pour recréer un contrôle hôte <xref:Microsoft.Office.Tools.Excel.Chart>, vous devez d’abord supprimer le <xref:Microsoft.Office.Interop.Excel.Chart> natif, puis recréez le <xref:Microsoft.Office.Tools.Excel.Chart> à l’aide de la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> ou <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>. Il n’existe aucune méthode `Add`\<*control class*\> vous permettant de créer un nouveau <xref:Microsoft.Office.Tools.Excel.Chart> basé sur un <xref:Microsoft.Office.Interop.Excel.Chart> existant.  
  
 Si vous ne commencez pas par supprimer le <xref:Microsoft.Office.Interop.Excel.Chart> natif, vous allez alors créer un second graphique dupliqué lorsque vous recréerez le <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## Persistance des contrôles Windows Forms dans les documents  
 Lorsqu’un document est enregistré puis fermé, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] supprime dans le document tous les contrôles Windows Forms créés dynamiquement. Toutefois, le comportement est différent pour les projets au niveau du document et de complément VSTO.  
  
 Dans les personnalisations au niveau du document, les contrôles et leurs wrappers ActiveX sous\-jacents \(qui sont utilisés pour héberger les contrôles dans le document\) sont supprimés à la prochaine ouverture du document. Rien n’indique la présence de ces contrôles.  
  
 Dans les compléments VSTO, les contrôles sont supprimés mais les wrappers ActiveX restent dans le document. Lors de la prochaine ouverture du document, les wrappers ActiveX seront visibles. Dans Excel, les wrappers ActiveX affichent des images des contrôles tels qu’ils apparaissent lors du dernier enregistrement du document. Dans Word, les wrappers ActiveX sont invisibles, sauf si l’utilisateur clique dessus, auquel cas ils affichent une ligne en pointillé qui représente la bordure des contrôles. Vous pouvez supprimer les wrappers ActiveX de plusieurs façons. Pour plus d’informations, consultez [Suppression de wrappers ActiveX dans un complément](#removingActiveX).  
  
### Recréation de contrôles Windows Forms hôtes dynamiques lors de l’ouverture de documents  
 Vous pouvez recréer des contrôles Windows Forms supprimés lorsque l’utilisateur ouvre de nouveau le document. Pour ce faire, votre solution doit effectuer les tâches suivantes :  
  
1.  Stocker des informations sur la taille, l’emplacement et l’état des contrôles lorsque le document est enregistré ou fermé. Dans une personnalisation au niveau du document, vous pouvez enregistrer ces données dans le cache de données du document. Dans un complément VSTO, vous pouvez enregistrer ces données dans une partie XML personnalisée du document.  
  
2.  Recréez les contrôles dans un événement qui est déclenché lors de l’ouverture du document. Dans les projets au niveau du document, vous pouvez le faire dans les gestionnaires d’évènements `Sheet`*n*`_Startup` ou `ThisDocument_Startup`. Dans les projets de complément VSTO, vous pouvez le faire dans les gestionnaires d’événements pour les événements <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> ou <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
###  <a name="removingActiveX"></a> Suppression de wrappers ActiveX dans un complément  
 Lorsque vous ajoutez des contrôles Windows Forms dynamiques à des documents à l’aide d’un complément VSTO, vous pouvez empêcher l’apparition des wrappers ActiveX des contrôles dans le document lors de sa prochaine ouverture, en utilisant l’une des méthodes suivantes.  
  
#### Suppression de wrappers ActiveX lorsque le document est ouvert  
 Pour supprimer tous les wrappers ActiveX, appelez la méthode GetVstoObject permettant de générer un élément hôte pour le <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Workbook> qui représente le document récemment ouvert. Par exemple, pour supprimer tous les wrappers ActiveX dans un document Word, vous pouvez appeler la méthode GetVstoObject permettant de générer un élément hôte pour l’objet <xref:Microsoft.Office.Interop.Word.Document> qui est transmis au gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
 Cette procédure est utile lorsque vous savez que le document sera ouvert uniquement sur des ordinateurs avec le complément VSTO installé. Si le document peut être transmis à d’autres utilisateurs qui n’ont pas le complément VSTO installé, envisagez de supprimer les contrôles avant de fermer le document.  
  
 L’exemple de code suivant montre comment appeler la méthode GetVstoObject lorsque le document est ouvert.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 Bien que la méthode GetVstoObject soit principalement utilisée pour générer un nouvel élément hôte au moment de l’exécution, elle efface également tous les wrappers ActiveX du document la première fois qu’elle est appelée pour un document spécifique. Pour plus d’informations sur l’utilisation de la méthode GetVstoObject, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Notez que si votre complément VSTO crée des contrôles dynamiques lorsque le document est ouvert, votre complément VSTO appellera déjà la méthode GetVstoObject dans le cadre du processus de création des contrôles. Vous n’avez pas besoin d’ajouter un appel séparé à la méthode GetVstoObject pour supprimer les wrappers ActiveX dans ce scénario.  
  
#### Suppression de contrôles dynamiques avant la fermeture du document  
 Votre complément VSTO peut supprimer, de manière explicite, chaque contrôle dynamique du document avant la fermeture de celui\-ci. Cette procédure est utile pour les documents qui peuvent être transmis à d’autres utilisateurs qui n’ont pas le complément VSTO installé.  
  
 L’exemple de code suivant montre comment supprimer tous les contrôles Windows Forms d’un document Word lorsque celui\-ci est fermé.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## Voir aussi  
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  