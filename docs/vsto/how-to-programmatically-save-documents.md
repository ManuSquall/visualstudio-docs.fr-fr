---
title: "Comment&#160;: enregistrer des documents par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), enregistrer"
  - "Word (développement Office dans Visual Studio), enregistrer des documents"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: enregistrer des documents par programmation
  Il existe plusieurs méthodes d'enregistrement de documents Microsoft Office Word.  Ainsi, vous pouvez enregistrer un document sans modifier son nom ou sous un nouveau nom.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Enregistrement d'un document sans modifier le nom  
  
#### Pour enregistrer le document associé à une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>.  Pour utiliser cet exemple de code, exécutez\-le dans votre projet à partir de la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### Pour enregistrer le document actif  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.Save%2A> pour le document actif.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 Si vous n'êtes pas certain que le document que vous souhaitez enregistrer est le document actif, vous pouvez y faire référence par son nom.  
  
#### Pour enregistrer un document dont le nom est spécifié  
  
1.  Utilisez le nom du document comme argument pour la collection <xref:Microsoft.Office.Interop.Word.Documents> :  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## Enregistrement d'un document sous un nouveau nom  
 Utilisez la méthode SaveAs pour enregistrer un document sous un nouveau nom.  Vous pouvez utiliser cette méthode de l'élément hôte <xref:Microsoft.Office.Tools.Word.Document> dans un projet Word au niveau du document ou d'un objet <xref:Microsoft.Office.Interop.Word.Document> natif dans tout projet Word.  Vous devez spécifier le nouveau nom de fichier. Les autres arguments sont par contre facultatifs.  
  
> [!NOTE]  
>  Si vous affichez la boîte de dialogue **Enregistrer sous** dans le gestionnaire d'événements <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> de `ThisDocument` et que vous affectez au paramètre *Cancel* la valeur **false**, l'application peut prendre fin de manière inattendue.  Si vous affectez au paramètre *Cancel* la valeur **true**, un message d'erreur indique que l'enregistrement automatique a été désactivé.  
  
#### Pour enregistrer le document associé à une personnalisation au niveau du document sous un nouveau nom  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> de la classe `ThisDocument` dans votre projet, à l'aide d'un chemin et d'un nom de fichier qualifiés complets.  Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument`.  
  
    > [!NOTE]  
    >  La méthode <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> lève une exception si un répertoire cible n'existe pas ou si d'autres problèmes surgissent lors de l'enregistrement d'un fichier.  Il est toujours conseillé d'utiliser un bloc **try…catch** autour de la méthode <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> ou à l'intérieur d'une méthode appelante.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### Pour enregistrer un document natif sous un nouveau nom  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> du <xref:Microsoft.Office.Interop.Word.Document> que vous souhaitez enregistrer, prenant en paramètre un chemin qualifié complet incluant le nom du fichier.  Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     L'exemple de code suivant enregistre le document actif sous un nouveau nom.  Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
    > [!NOTE]  
    >  La méthode <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> lève une exception si un répertoire cible n'existe pas ou si d'autres problèmes surgissent lors de l'enregistrement d'un fichier.  Il est toujours conseillé d'utiliser un bloc **try…catch** autour de la méthode <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> ou à l'intérieur d'une méthode appelante.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Compilation du code  
 Cet exemple de code nécessite ce qui suit :  
  
-   Pour enregistrer un document par nom, un document nommé NouveauDocument.doc doit exister dans un répertoire Test sur le lecteur C.  
  
-   Pour enregistrer un document sous un nouveau nom, un répertoire Test doit exister sur le lecteur C.  
  
## Voir aussi  
 [Comment : fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Élément hôte de document](../vsto/document-host-item.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  