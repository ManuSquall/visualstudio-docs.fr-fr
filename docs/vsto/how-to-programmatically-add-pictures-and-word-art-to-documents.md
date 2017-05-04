---
title: "Comment&#160;: ajouter des images et des effets WordArt aux documents par programmation | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), ajouter des images"
  - "graphiques, ajouter à des documents Word"
  - "documents Word, ajouter des images"
  - "documents Word, ajouter un objet Word Art"
  - "WordArt, ajouter à des documents"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: ajouter des images et des effets WordArt aux documents par programmation
  Vous pouvez ajouter des images et des objets de dessin à vos documents au moment du design ou de l'exécution.  WordArt vous permet d'ajouter du texte décoratif aux documents Microsoft Office Word.  Ces effets de texte spéciaux sont des objets de dessin que vous pouvez personnaliser et insérer dans votre document.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Ajout d'une image au moment du design  
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter une image au document au moment du design.  
  
#### Pour ajouter une image à un document Word au moment du design  
  
1.  Placez votre curseur à l'emplacement où vous souhaitez insérer l'image dans le document.  
  
2.  Dans le ruban, cliquez sur l'onglet **Insertion**.  
  
3.  Dans le groupe **Illustrations**, cliquez sur **Image**.  
  
4.  Dans la boîte de dialogue **Insérer une image**, accédez à l'image à insérer et cliquez sur **Insérer**.  
  
     L'image est ajoutée à votre document à l'emplacement du curseur.  
  
## Ajout d'une image au moment de l'exécution  
 Vous pouvez insérer une image dans un document à l'emplacement du curseur.  
  
#### Pour ajouter une image à l'emplacement du curseur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> de la collection <xref:Microsoft.Office.Interop.Word.InlineShapes> et passez\-lui le nom du fichier.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## Ajout d'un objet WordArt au moment du design  
 Si vous développez une personnalisation au niveau du document, vous pouvez ajouter un objet WordArt au document au moment du design.  
  
#### Pour ajouter un objet WordArt à un document Word au moment du design  
  
1.  Placez votre curseur à l'emplacement où vous souhaitez insérer l'objet WordArt dans le document.  
  
2.  Dans le ruban, cliquez sur l'onglet **Insertion**.  
  
3.  Dans le groupe **Texte**, cliquez sur **WordArt**, puis sélectionnez un style WordArt.  
  
4.  Ajoutez le texte à afficher dans le document dans la boîte de dialogue **Modification du texte WordArt** et cliquez sur **OK**.  
  
     Le texte est ajouté à votre document et le style WordArt sélectionné lui est appliqué.  
  
## Ajout d'un objet WordArt au moment de l'exécution  
 Vous pouvez insérer un objet WordArt dans un document à l'emplacement du curseur.  La procédure est différente pour les personnalisations de niveau document et les compléments VSTO.  
  
#### Pour ajouter un objet WordArt à l'emplacement du curseur dans une personnalisation au niveau du document  
  
1.  Obtenez la position gauche et supérieure de l'emplacement du curseur.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> dans le document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### Pour ajouter un objet WordArt à l'emplacement du curseur dans un complément VSTO  
  
1.  Obtenez la position gauche et supérieure de l'emplacement du curseur.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Shapes> du document actif \(ou d'un autre document que vous spécifiez\).  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## Compilation du code  
  
-   Une image nommée **SamplePicture.jpg** doit exister sur le lecteur C.  
  
## Voir aussi  
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Comment : insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Comment : enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  