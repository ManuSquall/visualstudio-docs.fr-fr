---
title: "Comment : attacher des Extensions de Code managé à des Documents | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3f5703b54a1deb96e9d6719c2726164e1002a18f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Comment : attacher des extensions de code managé à des documents
  Vous pouvez attacher un assembly de personnalisation à un document Microsoft Office Word existant ou d’un classeur Microsoft Office Excel. Le document ou le classeur peut être dans n’importe quel format de fichier pris en charge par les projets Microsoft Office et les outils de développement dans Visual Studio. Pour plus d’informations, consultez [Architecture des personnalisations de niveau Document](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour attacher une personnalisation à un document Word ou Excel, utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthode de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Étant donné que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe est conçu pour être exécuté sur un ordinateur qui ne dispose pas de Microsoft Office est installé, vous pouvez utiliser cette méthode dans les solutions qui ne sont pas directement liées au développement de Microsoft Office (par exemple, une application console ou Windows Forms).  
  
> [!NOTE]  
>  La personnalisation échoue si le code attend des contrôles que le document spécifié n’a pas de charge.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : n’attacher ou détacher un Assembly VSTO à partir d’un Document Word ?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Pour attacher des extensions de code managé à un document  
  
1.  Dans un projet qui ne requiert pas de Microsoft Office, telle qu’une application console ou un projet Windows Forms, ajoutez une référence au Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll et Microsoft.VisualStudio.Tools.Applications.Runtime.dll assemblys.  
  
2.  Ajoutez le code suivant **importations** ou **à l’aide de** instructions au début du fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Appelez la méthode statique <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> (méthode).  
  
     Le code suivant exemple utilise le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> de surcharge. Cette surcharge prend le chemin d’accès complet du document et une <xref:System.Uri> qui spécifie l’emplacement du manifeste de déploiement pour la personnalisation que vous voulez attacher au document. Cet exemple suppose qu’un document Word nommé **Documentword1.docx** sur le bureau, et que le manifeste de déploiement se trouve dans un dossier nommé **publier** qui se trouve également sur le bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Générez le projet et exécuter l’application sur l’ordinateur où vous souhaitez attacher la personnalisation. L’ordinateur doit disposer de Visual Studio 2010 Tools pour Office Runtime.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de Documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Comment : supprimer des Extensions de Code managé de Documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  