---
title: "Comment&#160;: attacher des extensions de code manag&#233; &#224; des documents | Microsoft Docs"
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
  - "extensions de code managé (développement Office dans Visual Studio), attacher"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Comment&#160;: attacher des extensions de code manag&#233; &#224; des documents
  Vous pouvez attacher un assembly de personnalisation à un document Microsoft Office Word ou un classeur Microsoft Office Excel existant.  Le document ou le classeur peut avoir n'importe quel format de fichier pris en charge par les projets et les outils de développement Microsoft Office dans Visual Studio.  Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour attacher une personnalisation à un document Word ou Excel, utilisez la méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Étant donné que la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> est conçue pour s'exécuter sur un ordinateur sur lequel Microsoft Office n'est pas installé, il est possible d'utiliser cette méthode dans les solutions qui ne sont pas directement liées au développement Microsoft Office \(telles qu'une console ou une application Windows Forms\).  
  
> [!NOTE]  
>  Le chargement de la personnalisation échouera si le code attend des contrôles que le document spécifié ne possède pas.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782) \(page éventuellement en anglais\).  
  
### Pour joindre des extensions de code managé à un document  
  
1.  Dans un projet qui ne requiert pas Microsoft Office, tel qu'une application console ou un projet Windows Forms, ajoutez une référence aux assemblys Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll et Microsoft.VisualStudio.Tools.Applications.Runtime.dll de.  
  
2.  Ajoutez l'instruction **Imports** ou **using** suivante en haut de votre fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  Appelez la méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> statique.  
  
     L'exemple de code suivant utilise la surcharge <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  Cette surcharge utilise le chemin d'accès complet du document et un <xref:System.Uri> qui spécifie l'emplacement du manifeste de déploiement pour la personnalisation que vous voulez joindre au document.  Cet exemple part du principe qu'un document Word appelé **WordDocument1.docx** est affiché sur le Bureau et que le manifeste de déploiement se trouve dans le dossier **Publish**, également sur le Bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  Générez le projet et exécutez l'application sur l'ordinateur où vous souhaitez attacher la personnalisation.  L'ordinateur doit avoir que Visual Studio 2010 tools pour Office Runtime installé.  
  
## Voir aussi  
 [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifestes d'application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  