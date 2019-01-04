---
title: 'Procédure : Enregistrer des documents par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99a50ec83d69217d123d11aa83ff02600b82108c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821592"
---
# <a name="how-to-programmatically-save-documents"></a>Procédure : Enregistrer des documents par programmation
  Il existe plusieurs façons d’enregistrer des documents Microsoft Office Word. Vous pouvez enregistrer un document sans modifier le nom du document, ou vous pouvez enregistrer un document avec un nouveau nom.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Enregistrer un document sans modifier le nom  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Pour enregistrer le document associé à une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document> . Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>Pour enregistrer le document actif  
  
1. Appelez le <xref:Microsoft.Office.Interop.Word._Document.Save%2A> méthode pour le document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   Si vous n’êtes pas sûr si le document que vous souhaitez enregistrer est le document actif, vous pouvez faire référence à ce dernier par son nom.  
  
### <a name="to-save-a-document-specified-by-name"></a>Pour enregistrer un document spécifié par nom  
  
1.  Utiliser le nom du document en tant qu’argument à la <xref:Microsoft.Office.Interop.Word.Documents> collection. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Enregistrer un document sous un nouveau nom  
 Utilisez la méthode SaveAs pour enregistrer un document avec un nouveau nom. Vous pouvez utiliser cette méthode de la <xref:Microsoft.Office.Tools.Word.Document> élément hôte dans un projet de Word au niveau du document ou de native <xref:Microsoft.Office.Interop.Word.Document> objet dans n’importe quel projet Word. Cette méthode requiert que vous spécifiez le nouveau nom de fichier, mais que les autres arguments sont facultatifs.  
  
> [!NOTE]  
>  Si vous affichez le **SaveAs** boîte de dialogue à l’intérieur de la <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> Gestionnaire d’événements de `ThisDocument` et définir le *Annuler* paramètre **false**, l’application peut fermer de façon inattendue. Si vous définissez la *Annuler* paramètre **true**, un message d’erreur s’affiche indiquant que l’enregistrement automatique a été désactivé.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Pour enregistrer le document associé à une personnalisation au niveau du document avec un nouveau nom  
  
1.  Appelez le <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> méthode de la `ThisDocument` classe dans votre projet, à l’aide d’un chemin d’accès et un nom qualifié complet. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` .  
  
    > [!NOTE]  
    >  Le <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> méthode lève une exception si un répertoire cible n’existe pas ou si d’autres problèmes de l’enregistrement d’un fichier. Il est conseillé d’utiliser un **try... catch** bloquer autour de la <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> méthode ou à l’intérieur d’une méthode d’appel.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Pour enregistrer un document natif avec un nouveau nom  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> méthode de la <xref:Microsoft.Office.Interop.Word.Document> que vous souhaitez enregistrer, à l’aide d’un chemin d’accès et un nom qualifié complet. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     L’exemple de code suivant enregistre le document actif sous un nouveau nom. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  Le <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> méthode lève une exception si un répertoire cible n’existe pas ou si d’autres problèmes de l’enregistrement d’un fichier. Il est conseillé d’utiliser un **try... catch** bloquer autour de la <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> méthode ou à l’intérieur d’une méthode d’appel.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Pour enregistrer un document par nom, un document nommé *NouveauDocument.doc* doit exister dans un répertoire nommé *Test* sur le lecteur C.  
  
-   Pour enregistrer un document avec un nouveau nom, un répertoire nommé *Test* doit exister sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md)   
 [Guide pratique pour Ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Élément hôte de document](../vsto/document-host-item.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
