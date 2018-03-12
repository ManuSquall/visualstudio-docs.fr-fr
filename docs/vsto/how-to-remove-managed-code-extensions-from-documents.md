---
title: "Comment : supprimer des Extensions de Code managé à partir de Documents | Documents Microsoft"
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
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c83f9794cdce71db9f51a6adca69fbeabc8c7a8e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Comment : supprimer des extensions de code managé de documents
  Vous pouvez supprimer par programmation l’assembly de personnalisation à partir d’un document ou classeur qui fait partie d’une personnalisation au niveau du document pour Microsoft Office Word ou Microsoft Office Excel. Les utilisateurs peuvent ensuite ouvrir les documents et afficher le contenu, mais toute interface utilisateur personnalisée (UI) que vous ajoutez aux documents n’apparaîtra pas et votre code ne fonctionnera pas.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez supprimer l’assembly de personnalisation à l’aide d’une des méthodes RemoveCustomization fournies par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Méthode à utiliser varie selon que vous souhaitez supprimer la personnalisation au moment de l’exécution (autrement dit, en exécutant le code dans la personnalisation pendant que le mot document ou classeur Excel est ouvert), ou si vous souhaitez supprimer la personnalisation d’un document fermé ou d’un document que i s sur un serveur qui n’a pas de Microsoft Office est installé.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : n’attacher ou détacher un Assembly VSTO à partir d’un Document Word ?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Pour supprimer l’assembly de personnalisation au moment de l’exécution  
  
1.  Dans votre code de personnalisation, appelez le <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (méthode) (pour Word) ou <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (méthode) (pour Excel). Cette méthode doit être appelée uniquement après que la personnalisation n’est plus nécessaire.  
  
     Lorsque vous appelez cette méthode dans votre code dépend de l’utilisation de votre personnalisation. Par exemple, si les clients utilisent les fonctionnalités de votre personnalisation jusqu'à ce qu’ils sont prêts à envoyer le document à d’autres clients qui doivent uniquement le document lui-même (et pas sa personnalisation), vous pouvez fournir une interface utilisateur qui appelle RemoveCustomization lorsque l’utilisateur clique dessus. Si votre personnalisation remplit le document de données lorsqu’il est tout d’abord ouvert, mais ne fournit pas d’autres fonctionnalités qui sont accessibles directement par les clients, puis vous pouvez également appeler RemoveCustomization dès que votre personnalisation termine l’initialisation du document.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Pour supprimer l’assembly de personnalisation à partir d’un document fermé ou d’un document sur un serveur  
  
1.  Dans un projet qui ne requiert pas de Microsoft Office, telle qu’une application console ou un projet Windows Forms, ajoutez une référence à l’assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Ajoutez le code suivant **importations** ou **à l’aide de** en haut du fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Appelez la méthode statique <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> méthode de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe et spécifiez le chemin d’accès du document de solution pour le paramètre.  
  
     L’exemple de code suivant suppose que vous supprimez la personnalisation d’un document nommé **Documentword1.docx** qui se trouve sur le bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Générez le projet et exécuter l’application sur l’ordinateur sur lequel vous souhaitez supprimer la personnalisation. L’ordinateur doit disposer de Visual Studio 2010 Tools pour Office Runtime.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de Documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Guide pratique pour attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  