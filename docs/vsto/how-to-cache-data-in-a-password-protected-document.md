---
title: 'Procédure : Cache des données dans un document protégé par un mot de passe'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f6e9bea3d45249d847f2dccfe522f832d6a07b5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644521"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procédure : Cache des données dans un document protégé par un mot de passe
  Si vous ajoutez des données dans le cache de données dans un document ou classeur est protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées automatiquement. Vous pouvez enregistrer des modifications aux données mises en cache en remplaçant les deux méthodes dans votre projet.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>La mise en cache dans des documents Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>En cache des données dans un document Word qui est protégé par un mot de passe

1.  Dans le `ThisDocument` class, marquer un champ public ou une propriété doit être mis en cache. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).

2.  Remplacer le <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> méthode dans la `ThisDocument` classe et de supprimer la protection du document.

     Lorsque le document est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité pour ôter la protection du document. Ainsi, les modifications apportées à l’enregistrement des données mises en cache.

3.  Remplacer le <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> méthode dans la `ThisDocument` classe et de réappliquer la protection au document.

     Une fois que le document est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre de réappliquer la protection au document.

### <a name="example"></a>Exemple
 L’exemple de code suivant montre comment mettre en cache des données dans un document Word qui est protégé par un mot de passe. Avant que le code supprime la protection dans le <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> (méthode), il enregistre le <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valeur, afin que le même type de protection puisse être rétabli dans la <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> (méthode).

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Compiler le code
 Ajoutez ce code à la `ThisDocument` classe dans votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.

## <a name="cache-in-excel-workbooks"></a>Mettre en cache dans les classeurs Excel
 Dans les projets Excel, cette procédure est nécessaire uniquement lorsque vous protégez le classeur entier avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> (méthode). Cette procédure n’est pas nécessaire si vous protégez uniquement une feuille de calcul spécifique avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> (méthode).

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>En cache des données dans un classeur Excel qui est protégé par un mot de passe

1.  Dans le `ThisWorkbook` classe ou une de le `Sheet` *n* classes, marquer un champ public ou une propriété doit être mis en cache. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).

2.  Remplacer le <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> méthode dans la `ThisWorkbook` classe et de supprimer la protection du classeur.

     Lorsque le classeur est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité pour ôter la protection du classeur. Ainsi, les modifications apportées à l’enregistrement des données mises en cache.

3.  Remplacer le <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> méthode dans la `ThisWorkbook` classe et de réappliquer la protection au document.

     Une fois que le classeur est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre de réappliquer la protection du classeur.

### <a name="example"></a>Exemple
 L’exemple de code suivant montre comment mettre en cache des données dans un classeur Excel qui est protégé par un mot de passe. Avant que le code supprime la protection dans le <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> (méthode), il enregistre le <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> et <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> valeurs, afin que le même type de protection puisse être rétabli dans la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> (méthode).

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Compiler le code
 Ajoutez ce code à la `ThisWorkbook` classe dans votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.

## <a name="see-also"></a>Voir aussi
- [Données du cache](../vsto/caching-data.md)
- [Guide pratique pour Mettre en cache les données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Guide pratique pour Mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
