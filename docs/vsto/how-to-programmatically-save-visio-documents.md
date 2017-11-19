---
title: "Comment : enregistrer des Documents Visio par programmation | Documents Microsoft"
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
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a100a573f26a774c58083cb82b07c50792908f45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-visio-documents"></a>Comment : enregistrer des documents Visio par programmation
  Il existe plusieurs façons d’enregistrer des documents Microsoft Office Visio :  
  
-   Enregistrer les modifications dans un document existant.  
  
-   Enregistrer un nouveau document ou enregistrer un document existant sous un nouveau nom.  
  
-   Enregistrer un document avec des arguments spécifiés.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour les méthodes [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) et [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="saving-an-existing-document"></a>Enregistrement d’un document existant  
  
#### <a name="to-save-a-document"></a>Pour enregistrer un document  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.Save de la classe Microsoft.Office.Tools.Visio.Document d’un document qui a déjà été enregistré.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  La méthode Microsoft.Office.Interop.Visio.Document.Save lève une exception si un nouveau document Visio n’a pas encore été enregistré.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Enregistrement d’un document sous un nouveau nom  
 Utilisez la méthode Microsoft.Office.Interop.Visio.Document.SaveAs pour enregistrer un nouveau document ou un document portant un nouveau nom. Cette méthode requiert que vous spécifiiez le nouveau nom de fichier.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Pour enregistrer le document Visio actif sous un nouveau nom  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.SaveAs de la Microsoft.Office.Tools.Visio.Document que vous souhaitez enregistrer, en utilisant un chemin d’accès qualifié complet, y compris un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Enregistrement d’un document sous un nouveau nom et avec des arguments spécifiés  
 Utilisez la méthode Microsoft.Office.Interop.Visio.Document.SaveAsEx pour enregistrer un document avec un nouveau nom et spécifier tous les arguments à appliquer au document.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Pour enregistrer un document sous un nouveau nom avec des arguments spécifiés  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.SaveAsEx de la Microsoft.Office.Tools.Visio.Document que vous souhaitez enregistrer, en utilisant un chemin d’accès qualifié complet, y compris un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, une exception est levée.  
  
     L’exemple de code suivant enregistre le document actif sous un nouveau nom, marque le document en lecture seule et affiche le document dans la liste des derniers fichiers utilisés. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Pour enregistrer un document portant un nouveau nom, un répertoire nommé `Test` doit se trouver dans le dossier Mes documents (Windows XP ou version antérieure) ou Documents (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des Documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des Documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des Documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Guide pratique pour imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  