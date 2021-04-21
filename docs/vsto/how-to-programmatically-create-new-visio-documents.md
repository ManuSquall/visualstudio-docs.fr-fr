---
title: 'Comment : créer des documents Visio par programmation'
description: Découvrez comment vous pouvez créer un nouveau document de dessin Microsoft Visio par programmation et l’ajouter à la collection documents de documents Visio ouverts.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825314"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Comment : créer des documents Visio par programmation
  Quand vous créez un dessin Microsoft Office Visio, vous l’ajoutez à la collection `Microsoft.Office.Interop.Visio.Documents` de documents Visio ouverts. Ainsi, la méthode `Microsoft.Office.Interop.Visio.Documents.Add` crée un dessin Visio. Pour plus d’informations, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Créer des documents vides

### <a name="to-create-a-new-document"></a>Pour créer un document

- Utilisez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` pour créer un document vierge qui n’est pas basé sur un modèle.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Créer des documents copiés à partir de documents existants
 La méthode `Microsoft.Office.Interop.Visio.Documents.Add` peut créer un document qui est une copie d’un document Visio existant. Vous devez fournir le nom de fichier et le chemin complet du diagramme.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Pour créer un document copié à partir d’un document existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du diagramme Visio.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Créer des stencils copiés à partir de gabarits existants
 La méthode [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) peut créer un gabarit qui est une copie d’un gabarit Visio existant. Vous devez fournir le nom de fichier et le chemin complet du gabarit.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Pour créer un gabarit copié à partir d’un gabarit existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du gabarit.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Créer des documents basés sur des modèles existants
 La `Microsoft.Office.Interop.Visio.Documents.Add` méthode peut créer un document (fichier *. VSD* ) basé sur un modèle Visio existant (fichier *. VST* ). Cette méthode copie les gabarits, styles et paramètres qui font partie de l’espace de travail du modèle. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Pour créer un document basé sur un modèle existant

- Appelez la méthode `Microsoft.Office.Interop.Visio.Documents.Add` et spécifiez le chemin du modèle.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

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
