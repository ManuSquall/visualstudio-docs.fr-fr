---
title: "Comment : mettre en Cache les données dans un Document protégé par mot de passe | Documents Microsoft"
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
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ecc4913d9d508d95347945b8f4aaa816bc3d510c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Comment : mettre en cache des données dans un document protégé par un mot de passe
  Si vous ajoutez des données dans le cache de données dans un document ou le classeur est protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées automatiquement. Vous pouvez enregistrer les modifications aux données mises en cache en substituant deux méthodes dans votre projet.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>La mise en cache dans les Documents Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>En cache des données dans un document Word protégé par un mot de passe  
  
1.  Dans la `ThisDocument` de classe, marquez un champ public ou une propriété doit être mis en cache. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).  
  
2.  Remplacer la <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> méthode dans le `ThisDocument` de classe et de supprimer la protection du document.  
  
     Lorsque le document est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité pour la protection du document. Ainsi, les modifications apportées à l’enregistrement des données mises en cache.  
  
3.  Remplacer la <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> méthode dans le `ThisDocument` de classe et de réappliquer la protection du document.  
  
     Une fois que le document est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de réappliquer la protection du document.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment mettre en cache des données dans un document Word protégé par un mot de passe. Avant que le code supprime la protection dans le <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> (méthode), il enregistre le <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valeur, afin que le même type de protection puisse être rétabli dans la <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> (méthode).  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Ajoutez ce code à la `ThisDocument` classe dans votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>La mise en cache dans les classeurs Excel  
 Dans les projets Excel, cette procédure est nécessaire uniquement lorsque vous protégez le classeur entier avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> (méthode). Cette procédure n’est pas nécessaire si vous protégez uniquement une feuille de calcul spécifique avec un mot de passe à l’aide de la <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> (méthode).  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Pour le cache des données dans un classeur Excel qui est protégé par un mot de passe  
  
1.  Dans le `ThisWorkbook` classe ou une de le `Sheet`  *n*  classes, marquez un champ public ou une propriété doit être mis en cache. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).  
  
2.  Remplacer la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> méthode dans le `ThisWorkbook` de classe et de supprimer la protection du classeur.  
  
     Lorsque le classeur est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité pour la protection du classeur. Ainsi, les modifications apportées à l’enregistrement des données mises en cache.  
  
3.  Remplacer la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> méthode dans le `ThisWorkbook` de classe et de réappliquer la protection du document.  
  
     Une fois que le classeur est enregistré, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de réappliquer la protection du classeur.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment mettre en cache des données dans un classeur Excel qui est protégé par un mot de passe. Avant que le code supprime la protection dans le <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> (méthode), il enregistre le <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> et <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> des valeurs, afin que le même type de protection puisse être rétabli dans la <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> (méthode).  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Ajoutez ce code à la `ThisWorkbook` classe dans votre projet. Ce code suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache de données](../vsto/caching-data.md)   
 [Comment : mettre en Cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Guide pratique pour mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  