---
title: "Comment : créer par programme des Documents Visio | Documents Microsoft"
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa4a4d021ee0610d4fdd80a1966df6a8280c9523
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Comment : créer des documents Visio par programmation
  Lorsque vous créez un dessin Microsoft Office Visio, vous l’ajoutez à la collection Microsoft.Office.Interop.Visio.Documents de documents Visio ouverts. Par conséquent, la méthode Microsoft.Office.Interop.Visio.Documents.Add crée un dessin Visio. Pour plus d’informations, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="creating-new-blank-documents"></a>Création de documents vierges  
  
#### <a name="to-create-a-new-document"></a>Pour créer un document  
  
-   Utilisez la méthode Microsoft.Office.Interop.Visio.Documents.Add pour créer un nouveau document vierge qui n’est pas basé sur un modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Création de documents copiés à partir de documents existants  
 La méthode Microsoft.Office.Interop.Visio.Documents.Add peut créer un nouveau document qui est une copie d’un document Visio existant. Vous devez fournir le nom de fichier et le chemin complet du diagramme.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Pour créer un document copié à partir d’un document existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin d’accès du diagramme Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Création de gabarits copiés à partir de gabarits existants  
 La méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) peut créer un gabarit qui est une copie d’un gabarit Visio existant. Vous devez fournir le nom de fichier et le chemin complet du gabarit.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Pour créer un gabarit copié à partir d’un gabarit existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin du gabarit.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Création de documents basés sur des modèles existants  
 La méthode Microsoft.Office.Interop.Visio.Documents.Add peut créer un nouveau document (fichier .vsd) basé sur un modèle Visio existant (fichier .vst). Cette méthode copie les gabarits, styles et paramètres qui font partie de l’espace de travail du modèle. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Pour créer un document basé sur un modèle existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin d’accès du modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents (Windows XP ou version antérieure) ou du dossier Documents (Windows Vista).  
  
-   Un document Visio nommé `myStencil.vss` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents (Windows XP ou version antérieure) ou du dossier Documents (Windows Vista).  
  
-   Un document Visio nommé `myTemplate.vst` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents (Windows XP ou version antérieure) ou du dossier Documents (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : ouvrir des Documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des Documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des Documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Guide pratique pour imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  