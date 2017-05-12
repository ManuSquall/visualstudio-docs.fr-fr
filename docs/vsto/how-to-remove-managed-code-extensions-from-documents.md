---
title: "Comment&#160;: supprimer des extensions de code manag&#233; de documents"
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
  - "documents (développement Office dans Visual Studio), extensions de code managé"
  - "extensions de code managé (développement Office dans Visual Studio), supprimer"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: supprimer des extensions de code manag&#233; de documents
  Vous pouvez supprimer par programmation l'assembly de personnalisation d'un document ou d'un classeur faisant partie d'une personnalisation au niveau du document pour Microsoft Office Word ou Microsoft Office Excel.  Les utilisateurs peuvent alors ouvrir les documents et afficher le contenu, mais les interfaces utilisateur personnalisées que vous ajoutez aux documents n'apparaissent pas et votre code ne s'exécute pas.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez supprimer l'assembly de personnalisation à l'aide de l'une des méthodes RemoveCustomization fournies par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  La méthode à utiliser dépend de si vous souhaitez supprimer la personnalisation au moment de l'exécution \(autrement dit, en exécutant le code dans la personnalisation pendant que le document Word ou le classeur Excel est ouvert\) ou si vous souhaitez supprimer la personnalisation d'un document fermé ou d'un document se trouvant sur un serveur sur lequel Microsoft Office n'est pas installé.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782) \(page éventuellement en anglais\).  
  
### Pour supprimer l'assembly de personnalisation au moment de l'exécution  
  
1.  Dans votre code de personnalisation, appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> \(pour Word\) ou la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> \(pour Excel\).  Cette méthode doit être appelée uniquement une fois que la personnalisation n'est plus nécessaire.  
  
     L'endroit de l'appel de la méthode dépend de la personnalisation utilisée.  Par exemple, si les utilisateurs utilisent les fonctionnalités de votre personnalisation jusqu'à ce qu'ils soient prêts à envoyer le document à d'autres utilisateurs qui nécessitent uniquement ce document \(et pas sa personnalisation\), vous pouvez fournir une interface utilisateur qui appelle RemoveCustomization lorsque l'utilisateur clique dessus.  Si votre personnalisation remplit le document de données lorsqu'il est ouvert pour la première fois, mais ne fournit pas toutes les autres fonctionnalités accessibles directement par les utilisateurs, vous pouvez appeler RemoveCustomization dès que votre personnalisation a terminé l'initialisation du document.  
  
### Pour supprimer l'assembly de personnalisation à partir d'un document fermé ou d'un document sur un serveur  
  
1.  Dans un projet qui ne requiert pas Microsoft Office, tel qu'une application console ou un projet Windows Forms, ajoutez une référence à l'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Ajoutez l'instruction **Imports** ou **using** suivante en haut de votre fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  Appelez la méthode statique <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> et spécifiez le chemin d'accès du document de solution pour le paramètre.  
  
     L'exemple de code suivant suppose que vous supprimez la personnalisation d'un document intitulé **WordDocument1.docx** qui se trouve sur le bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  Générez le projet et exécutez l'application sur l'ordinateur où vous souhaitez supprimer la personnalisation.  L'ordinateur doit avoir que Visual Studio 2010 tools pour Office Runtime installé.  
  
## Voir aussi  
 [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  