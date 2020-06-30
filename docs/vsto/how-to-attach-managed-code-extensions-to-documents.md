---
title: 'Comment : attacher des extensions de code managé à des documents'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f44b153ac7d55704ba649a7dc09860518a5e76b7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547522"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Comment : attacher des extensions de code managé à des documents
  Vous pouvez attacher un assembly de personnalisation à un document Word Microsoft Office existant ou à Microsoft Office classeur Excel. Le document ou le classeur peut être dans n’importe quel format de fichier pris en charge par le Microsoft Office projets et les outils de développement dans Visual Studio. Pour plus d’informations, consultez [architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Pour attacher une personnalisation à un document Word ou Excel, utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthode de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Étant donné que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe est conçue pour être exécutée sur un ordinateur sur lequel Microsoft Office n’est pas installé, vous pouvez utiliser cette méthode dans des solutions qui ne sont pas directement liées au développement Microsoft Office (par exemple, une console ou une application Windows Forms).

> [!NOTE]
> Le chargement de la personnalisation échoue si le code attend des contrôles que le document spécifié n’a pas.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Pour attacher des extensions de code managé à un document

1. Dans un projet qui ne requiert pas de Microsoft Office, comme une application console ou un projet Windows Forms, ajoutez une référence aux assemblys *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* et *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* .

2. Ajoutez les instructions **Imports** ou **using** suivantes en haut de votre fichier de code.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Appelez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthode statique.

     L’exemple de code suivant utilise la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> surcharge. Cette surcharge prend le chemin d’accès complet du document et un <xref:System.Uri> qui spécifie l’emplacement du manifeste de déploiement pour la personnalisation que vous souhaitez attacher au document. Cet exemple suppose qu’un document Word nommé **WordDocument1.docx** se trouve sur le bureau et que le manifeste de déploiement se trouve dans un dossier nommé **Publish** qui se trouve également sur le bureau.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Générez le projet et exécutez l’application sur l’ordinateur sur lequel vous souhaitez attacher la personnalisation. Visual Studio 2010 Tools pour Office Runtime doit être installé sur l’ordinateur.

## <a name="see-also"></a>Voir aussi
- [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
