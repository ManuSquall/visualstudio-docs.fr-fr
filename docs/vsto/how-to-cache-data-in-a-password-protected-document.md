---
title: 'Comment : mettre en cache des données dans un document protégé par un mot de passe'
description: En outre, si vous ajoutez des données au cache de données dans un document ou un classeur protégé par un mot de passe, vous pouvez enregistrer les modifications apportées aux données mises en cache en remplaçant deux méthodes dans votre projet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd7efe4aa2aa14cb94a68f0729bc7fe3535888ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954031"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Comment : mettre en cache des données dans un document protégé par un mot de passe
  Si vous ajoutez des données au cache de données dans un document ou un classeur protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées automatiquement. Vous pouvez enregistrer les modifications apportées aux données mises en cache en remplaçant deux méthodes dans votre projet.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Mise en cache dans les documents Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Pour mettre en cache des données dans un document Word protégé par un mot de passe

1. Dans la `ThisDocument` classe, marquez un champ public ou une propriété à mettre en cache. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

2. Substituez la <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> méthode dans la `ThisDocument` classe et supprimez la protection du document.

     Lorsque le document est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre d’ôter la protection du document. Cela permet d’enregistrer les modifications apportées aux données mises en cache.

3. Substituez la <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> méthode dans la `ThisDocument` classe et réappliquez la protection au document.

     Une fois le document enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre de réappliquer la protection au document.

### <a name="example"></a>Exemple
 L’exemple de code suivant montre comment mettre en cache des données dans un document Word protégé par un mot de passe. Avant que le code ne supprime la protection dans la <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> méthode, il enregistre la <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valeur actuelle, afin que le même type de protection puisse être réappliqué dans la <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> méthode.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Compiler le code
 Ajoutez ce code à la `ThisDocument` classe de votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Cache dans les classeurs Excel
 Dans les projets Excel, cette procédure est nécessaire uniquement lorsque vous protégez le classeur entier avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> méthode. Cette procédure n’est pas nécessaire si vous protégez uniquement une feuille de calcul spécifique avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> méthode.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Pour mettre en cache des données dans un classeur Excel protégé par un mot de passe

1. Dans la `ThisWorkbook` classe ou l’une des `Sheet` *n* classes, marquez un champ public ou une propriété à mettre en cache. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

2. Substituez la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> méthode dans la `ThisWorkbook` classe et supprimez la protection du classeur.

     Lorsque le classeur est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre d’ôter la protection du classeur. Cela permet d’enregistrer les modifications apportées aux données mises en cache.

3. Substituez la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> méthode dans la `ThisWorkbook` classe et réappliquez la protection au document.

     Une fois le classeur enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous permettre de réappliquer la protection au classeur.

### <a name="example"></a>Exemple
 L’exemple de code suivant montre comment mettre en cache des données dans un classeur Excel protégé par un mot de passe. Avant que le code ne supprime la protection dans la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> méthode, il enregistre les <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> valeurs actuelles et <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> , afin que le même type de protection puisse être réappliqué dans la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> méthode.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Compiler le code
 Ajoutez ce code à la `ThisWorkbook` classe de votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword` .

## <a name="see-also"></a>Voir aussi
- [Données de cache](../vsto/caching-data.md)
- [Procédure : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
