---
title: 'Comment : créer par programme des documents Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256742"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Comment : créer par programme des documents Visio
  Lorsque vous créez un dessin Microsoft Office Visio, ajoutez-le à la `Microsoft.Office.Interop.Visio.Documents` collection de documents Visio ouverts. Par conséquent, le `Microsoft.Office.Interop.Visio.Documents.Add` méthode crée un nouveau document de dessin Visio. Pour plus d’informations, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="create-new-blank-documents"></a>Créer des documents vierges  
  
### <a name="to-create-a-new-document"></a>Pour créer un document  
  
-   Utilisez le `Microsoft.Office.Interop.Visio.Documents.Add` méthode pour créer un nouveau document vierge qui n’est pas basé sur un modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Créer des documents copiés à partir de documents existants  
 Le `Microsoft.Office.Interop.Visio.Documents.Add` méthode peut créer un nouveau document qui est une copie d’un document Visio existant. Vous devez fournir le nom de fichier et le chemin complet du diagramme.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Pour créer un document copié à partir d’un document existant  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Documents.Add` (méthode) et spécifiez le chemin d’accès du diagramme Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Création de gabarits copiés à partir de gabarits existants  
 La méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) peut créer un gabarit qui est une copie d’un gabarit Visio existant. Vous devez fournir le nom de fichier et le chemin complet du gabarit.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Pour créer un gabarit copié à partir d’un gabarit existant  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Documents.Add` (méthode) et spécifiez le chemin du gabarit.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Créer des documents basés sur des modèles existants  
 Le `Microsoft.Office.Interop.Visio.Documents.Add` méthode peut créer un nouveau document (un *.vsd* fichier) qui est basé sur un modèle Visio existant (un *.vst* fichier). Cette méthode copie les gabarits, styles et paramètres qui font partie de l’espace de travail du modèle. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Pour créer un document basé sur un modèle existant  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Documents.Add` (méthode) et spécifiez le chemin d’accès du modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
-   Un document Visio nommé `myStencil.vss` doit se trouver dans un répertoire nommé `Test` dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
-   Un document Visio nommé `myTemplate.vst` doit se trouver dans un répertoire nommé `Test` dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  