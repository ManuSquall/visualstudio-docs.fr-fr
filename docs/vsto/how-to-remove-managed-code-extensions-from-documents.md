---
title: 'Procédure : Supprimer des extensions de code managé de documents'
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
ms.openlocfilehash: 83bd57c8ffdcb268a560431c74806ddb6544d4e8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252166"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Procédure : Supprimer des extensions de code managé de documents
  Vous pouvez supprimer par programmation l’assembly de personnalisation d’un document ou d’un classeur qui fait partie d’une personnalisation au niveau du document pour Microsoft Office Word ou Microsoft Office Excel. Les utilisateurs peuvent ensuite ouvrir les documents et afficher le contenu, mais toute interface utilisateur personnalisée que vous ajoutez aux documents n’apparaît pas et votre code ne s’exécute pas.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous pouvez supprimer l’assembly de personnalisation à l’aide de `RemoveCustomization` l’une des méthodes [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]fournies par le. La méthode que vous utilisez varie selon que vous souhaitez supprimer la personnalisation au moment de l’exécution (autrement dit, en exécutant le code dans la personnalisation alors que le document Word ou le classeur Excel est ouvert), ou si vous souhaitez supprimer la personnalisation d’un document fermé ou d’un document que j’ai sur un serveur sur lequel Microsoft Office n’est pas installé.

 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, [consultez Comment faire : Attacher ou détacher un assembly VSTO d’un document Word ? ](http://go.microsoft.com/fwlink/?LinkId=136782).

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Pour supprimer l’assembly de personnalisation au moment de l’exécution

1. Dans votre code de personnalisation, appelez la <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> méthode (pour Word) ou la <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> méthode (pour Excel). Cette méthode doit être appelée uniquement une fois que la personnalisation n’est plus nécessaire.

     L’emplacement où vous appelez cette méthode dans votre code dépend de la manière dont votre personnalisation est utilisée. Par exemple, si les clients utilisent les fonctionnalités de votre personnalisation jusqu’à ce qu’ils soient prêts à envoyer le document à d’autres clients qui n’ont besoin que du document lui-même (et non de la personnalisation `RemoveCustomization` ), vous pouvez fournir une interface utilisateur qui appelle lorsque le client clique dessus. En guise d’alternative, si votre personnalisation remplit le document avec des données lorsqu’il est ouvert pour la première fois, mais que la personnalisation ne fournit pas d’autres fonctionnalités directement accessibles par les clients, vous pouvez appeler RemoveCustomization dès que votre personnalisation termine l’initialisation du document.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Pour supprimer l’assembly de personnalisation d’un document ou d’un document fermé sur un serveur

1. Dans un projet qui ne requiert pas de Microsoft Office, comme une application console ou un projet Windows Forms, ajoutez une référence à l’assembly *Microsoft. VisualStudio. Tools. applications. ServerDocument. dll* .

2. Ajoutez l’instruction **Imports** ou **using** suivante au début de votre fichier de code.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Appelez la méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> statique de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe et spécifiez le chemin d’accès du document de la solution pour le paramètre.

     L’exemple de code suivant suppose que vous supprimez la personnalisation d’un document nommé *DocumentWord1. docx* qui se trouve sur le bureau.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Générez le projet et exécutez l’application sur l’ordinateur sur lequel vous souhaitez supprimer la personnalisation. Visual Studio 2010 Tools pour Office Runtime doit être installé sur l’ordinateur.

## <a name="see-also"></a>Voir aussi
- [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Guide pratique pour Attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
