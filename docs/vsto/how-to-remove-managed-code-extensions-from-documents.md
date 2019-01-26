---
title: 'Procédure : Supprimer des extensions de code managé à partir de documents'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f1acdec565a2d03b98a2423f500d527934235bd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874864"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procédure : Supprimer des extensions de code managé à partir de documents
  Vous pouvez supprimer par programmation l’assembly de personnalisation à partir d’un document ou classeur qui fait partie d’une personnalisation au niveau du document pour Microsoft Office Word ou Microsoft Office Excel. Les utilisateurs peuvent ensuite ouvrir les documents et afficher le contenu, mais n’importe quelle interface utilisateur personnalisée (IU) que vous ajoutez aux documents n’apparaît pas, et votre code s’exécutera pas.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez supprimer l’assembly de personnalisation à l’aide d’un de le `RemoveCustomization` méthodes fournies par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Méthode à utiliser varie selon que vous souhaitez supprimer la personnalisation au moment de l’exécution (autrement dit, en exécutant du code dans la personnalisation pendant que le mot document ou classeur Excel est ouvert), ou si vous souhaitez supprimer la personnalisation d’un document fermé ou d’un document que i s sur un serveur qui n’a pas de Microsoft Office est installé.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [procédure : Attacher ou détacher un Assembly VSTO à partir d’un Document Word ? ](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>Pour supprimer l’assembly de personnalisation lors de l’exécution  
  
1.  Dans votre code de personnalisation, appelez le <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (méthode) (pour Word) ou le <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (méthode) (pour Excel). Cette méthode doit être appelée uniquement après que la personnalisation n’est plus nécessaire.  
  
     Lorsque vous appelez cette méthode dans votre code dépend de l’utilisation de votre personnalisation. Par exemple, si les clients utilisent les fonctionnalités de votre personnalisation jusqu'à ce qu’ils sont prêts à envoyer le document à d’autres clients qui doivent uniquement le document proprement dit (pas la personnalisation), vous pouvez fournir une interface utilisateur qui appelle `RemoveCustomization` lorsque l’utilisateur clique dessus. Si votre personnalisation remplit le document de données lors de sa première ouverture, mais ne fournit pas d’autres fonctionnalités qui sont accessibles directement par les clients, puis vous pouvez également appeler RemoveCustomization dès que votre personnalisation termine l’initialisation du document.  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Pour supprimer l’assembly de personnalisation à partir d’un document fermé ou d’un document sur un serveur  
  
1.  Dans un projet qui ne nécessite pas de Microsoft Office, par exemple une application console ou un projet Windows Forms, ajoutez une référence à la *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* assembly.  
  
2.  Ajoutez le code suivant **importations** ou **à l’aide de** instruction au début du fichier de code.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Appelez la méthode statique <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> méthode de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, puis spécifiez le chemin d’accès du document solution pour le paramètre.  
  
     L’exemple de code suivant suppose que vous supprimez la personnalisation d’un document nommé *Documentword1.docx* qui se trouve sur le bureau.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Générez le projet et exécuter l’application sur l’ordinateur où vous souhaitez supprimer la personnalisation. L’ordinateur doit disposer de Visual Studio 2010 Tools pour Office runtime est installé.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Guide pratique pour Attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
