---
title: 'Comment : attacher à des documents, les extensions de code managé'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6e39f27caf9d321bb83666d72114a9675091f03
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257038"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Comment : attacher à des documents, les extensions de code managé
  Vous pouvez attacher un assembly de personnalisation à un document Microsoft Office Word existant ou d’un classeur Microsoft Office Excel. Le document ou le classeur peut être dans n’importe quel format de fichier qui est pris en charge par les projets Microsoft Office et les outils de développement dans Visual Studio. Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour attacher une personnalisation à un document Word ou Excel, utilisez le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthode de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Étant donné que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe est conçue pour être exécuté sur un ordinateur qui n’a pas de Microsoft Office est installé, vous pouvez utiliser cette méthode dans les solutions qui ne sont pas directement liées au développement de Microsoft Office (par exemple, une application console ou Windows Forms).  
  
> [!NOTE]  
>  La personnalisation ne sera pas chargé si le code attend des contrôles au document spécifié n’a pas.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [comment faire : attacher ou détacher un assembly VSTO à partir d’un document Word ?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Pour attacher des extensions de code managé à un document  
  
1.  Dans un projet qui ne nécessite pas de Microsoft Office, par exemple une application console ou un projet Windows Forms, ajoutez une référence à la *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* et  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* assemblys.  
  
2.  Ajoutez le code suivant **importations** ou **à l’aide de** instructions au début du fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Appelez la méthode statique <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> (méthode).  
  
     Le code suivant exemple utilise le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> de surcharge. Cette surcharge prend le chemin d’accès complet du document et un <xref:System.Uri> qui spécifie l’emplacement du manifeste de déploiement pour la personnalisation que vous voulez attacher au document. Cet exemple suppose qu’un document Word nommé **Documentword1.docx** est sur le bureau, et que le manifeste de déploiement se trouve dans un dossier nommé **publier** qui se trouve également sur le bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Générez le projet et exécutez l’application sur l’ordinateur où vous souhaitez attacher la personnalisation. L’ordinateur doit disposer de Visual Studio 2010 Tools pour Office Runtime est installé.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Comment : supprimer des extensions de code managé à partir de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  