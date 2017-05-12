---
title: "Comment&#160;: d&#233;finir les options de recherche dans Word par programmation"
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
  - "documents (développement Office dans Visual Studio), options de recherche"
  - "rechercher, options Word"
  - "paramètres, options de recherche Word"
  - "Word, options de recherche"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: d&#233;finir les options de recherche dans Word par programmation
  Il existe deux méthodes de définition des options de recherche pour les sélections dans les documents Microsoft Office Word :  
  
-   Définir les propriétés individuelles d'un objet <xref:Microsoft.Office.Interop.Word.Find>.  
  
-   Utiliser des arguments de la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Find>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Utilisation des propriétés d'un objet de recherche  
 Le code suivant définit les propriétés d'un objet <xref:Microsoft.Office.Interop.Word.Find> pour rechercher du texte dans la sélection actuelle.  Notez que les critères de recherche, tels que la recherche en avant, le renvoi à la ligne et le texte à rechercher, sont des propriétés de l'objet <xref:Microsoft.Office.Interop.Word.Find>.  
  
 La définition de chacune des propriétés de l'objet <xref:Microsoft.Office.Interop.Word.Find> n'est pas utile lorsque vous rédigez du code C\#, car vous devez spécifier ces mêmes propriétés en tant que paramètres dans la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  Par conséquent, cet exemple contient uniquement du code Visual Basic.  
  
#### Pour définir des options de recherche à l'aide d'un objet Find  
  
1.  Définissez les propriétés d'un objet <xref:Microsoft.Office.Interop.Word.Find> de manière à rechercher vers l'avant le texte **find me** dans une sélection.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Utilisation des arguments de la méthode Execute  
 Le code suivant utilise la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Find> pour rechercher du texte dans la sélection actuelle.  Notez que les critères de recherche, tels que la recherche vers l'avant, le renvoi à la ligne et le texte à rechercher, sont passés comme paramètres de la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
#### Pour définir des options de recherche à l'aide des arguments de la méthode Execute  
  
1.  Passez les critères de recherche comme paramètres de la méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> pour rechercher vers l'avant le texte **find me** dans une sélection.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## Voir aussi  
 [Comment : rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Comment : parcourir les éléments trouvés dans les documents par programmation](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Comment : restaurer des sélections après des recherches par programmation](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  