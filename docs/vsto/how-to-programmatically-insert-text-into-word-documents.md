---
title: "Comment&#160;: ins&#233;rer du texte dans les documents Word par programmation"
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
  - "plages, insérer du texte dans des documents"
  - "texte (développement Office dans Visual Studio), insérer dans des documents"
  - "plages, remplacer du texte dans des documents"
  - "documents (développement Office dans Visual Studio), insérer du texte"
  - "texte (développement Office dans Visual Studio), remplacer"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Comment&#160;: ins&#233;rer du texte dans les documents Word par programmation
  Il existe trois principaux moyens pour insérer du texte dans des documents Microsoft Office Word :  
  
-   insérer du texte dans une plage ;  
  
-   remplacer du texte dans une plage par un nouveau texte ;  
  
-   utiliser la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Selection> pour insérer du texte au niveau du curseur ou de la sélection.  
  
> [!NOTE]  
>  Vous pouvez également insérer du texte dans les contrôles de contenu et les signets. Pour plus d’informations, consultez [Contrôles de contenu](../vsto/content-controls.md) et [Bookmark, contrôle](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Insertion de texte dans une plage  
 Utilisez la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> pour insérer du texte dans un document.  
  
#### Pour insérer du texte dans une plage  
  
1.  Spécifiez une plage au début d’un document et insérer le texte **New Text**.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  Sélectionnez l'objet <xref:Microsoft.Office.Interop.Word.Range>, qui s'est développé à partir d'un caractère jusqu'à la longueur correspondant au texte inséré.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## Remplacement de texte dans une plage  
 Si la plage spécifiée contient du texte, tout le texte de la plage est remplacé par le texte inséré.  
  
#### Pour remplacer du texte dans une plage  
  
1.  Créez un objet <xref:Microsoft.Office.Interop.Word.Range> comprenant les 12 premiers caractères du document.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO. Ce code utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  Remplacez ces caractères par la chaîne **New Text**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  Sélectionnez la plage.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## Insertion de texte à l'aide de TypeText  
 La méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> insère du texte au niveau de la sélection.<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporte différemment selon les options définies sur l'ordinateur de l'utilisateur. Le code de la procédure suivante déclare une variable objet <xref:Microsoft.Office.Interop.Word.Selection>, puis désactive l'option **Overtype**, si elle est activée. Si l'option **Overtype** est activée, le texte situé à proximité du curseur est remplacé.  
  
#### Pour insérer du texte à l'aide de la méthode TypeText  
  
1.  Déclarez une variable objet <xref:Microsoft.Office.Interop.Word.Selection>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  Désactivez l'option **Overtype**, si elle est activée.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  Vérifiez si la sélection actuelle est un point d'insertion.  
  
     Si tel est le cas, le code insère une phrase à l'aide de <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, puis une marque de paragraphe à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  Le code du bloc **ElseIf** vérifie si la sélection est une sélection normale. Si tel est le cas, un autre bloc **If** vérifie si l'option **ReplaceSelection** est activée. Si tel est le cas, le code utilise la méthode <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la sélection pour réduire cette dernière à un point d'insertion au début du bloc de texte sélectionné. Insérez le texte et une marque de paragraphe.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  Si la sélection n'est pas un point d'insertion ou un bloc de texte sélectionné, le code du bloc **Else** ne fait rien.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 Vous pouvez également utiliser la méthode <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Selection>, qui reproduit la fonctionnalité de la touche Retour arrière de votre clavier. Toutefois, quand il s'agit d'insérer et de manipuler du texte, l'objet <xref:Microsoft.Office.Interop.Word.Range> vous offre davantage de contrôle.  
  
 L'exemple suivant montre le code complet. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` ou `ThisAddIn` dans votre projet.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## Voir aussi  
 [Comment : mettre en forme du texte dans des documents par programmation](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  