---
title: 'Comment : créer des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 171ad93caf6b5c13d000073a0d7f7e82282b9b4a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541529"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Comment : créer des documents Visio par programmation
  Quand vous créez un dessin Microsoft Office Visio, vous l’ajoutez à la collection `Microsoft.Office.Interop.Visio.Documents` de documents Visio ouverts. Ainsi, la méthode `Microsoft.Office.Interop.Visio.Documents.Add` crée un dessin Visio. Pour plus d’informations, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Créer des documents vides

### <a name="to-create-a-new-document"></a>Pour créer un document

- Utilisez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` pour créer un document vierge qui n’est pas basé sur un modèle.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Créer des documents copiés à partir de documents existants
 La méthode `Microsoft.Office.Interop.Visio.Documents.Add` peut créer un document qui est une copie d’un document Visio existant. Vous devez fournir le nom de fichier et le chemin complet du diagramme.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Pour créer un document copié à partir d’un document existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du diagramme Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Créer des stencils copiés à partir de gabarits existants
 La méthode [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) peut créer un gabarit qui est une copie d’un gabarit Visio existant. Vous devez fournir le nom de fichier et le chemin complet du gabarit.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Pour créer un gabarit copié à partir d’un gabarit existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du gabarit.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Créer des documents basés sur des modèles existants
 La `Microsoft.Office.Interop.Visio.Documents.Add` méthode peut créer un document (fichier *. VSD* ) basé sur un modèle Visio existant (fichier *. VST* ). Cette méthode copie les gabarits, styles et paramètres qui font partie de l’espace de travail du modèle. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Pour créer un document basé sur un modèle existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du modèle.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple de code doit respecter la condition suivante :

- Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` dans le dossier *Mes documents* (pour Windows XP et versions antérieures) ou dans le dossier *documents* (pour Windows Vista).

- Un document Visio nommé `myStencil.vss` doit se trouver dans un répertoire nommé `Test` dans le dossier *Mes documents* (pour Windows XP et versions antérieures) ou dans le dossier *documents* (pour Windows Vista).

- Un document Visio nommé `myTemplate.vst` doit se trouver dans un répertoire nommé `Test` dans le dossier *Mes documents* (pour Windows XP et versions antérieures) ou dans le dossier *documents* (pour Windows Vista).

## <a name="see-also"></a>Voir aussi
- [Solutions Visio](../vsto/visio-solutions.md)
- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)
- [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)
- [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)
- [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)
- [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)
