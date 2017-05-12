---
title: "Comment&#160;: mettre en cache des donn&#233;es dans un document prot&#233;g&#233; par un mot de passe"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "données (développement Office dans Visual Studio), mettre en cache"
  - "mise en cache de données (développement Office dans Visual Studio), documents protégés"
  - "groupes de données (développement Office dans Visual Studio), mettre en cache"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: mettre en cache des donn&#233;es dans un document prot&#233;g&#233; par un mot de passe
  Si vous ajoutez des données au cache de données dans un document ou un classeur protégés par un mot de passe, les modifications apportées aux données en mémoire cache ne seront pas enregistrées automatiquement.  Vous pouvez enregistrer des modifications de données en mémoire cache en substituant deux méthodes dans votre projet.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Mise en cache dans les documents Word  
  
#### Pour mettre en cache des données dans un document Word protégé par un mot de passe  
  
1.  Dans la classe `ThisDocument`, marquez un champ public ou une propriété à mettre en cache.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
2.  Substituez la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> dans la classe `ThisDocument` et supprimez la protection du document.  
  
     Lorsque le document est enregistré, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de déprotéger le document.  Cela permet l'enregistrement des modifications apportées aux données mises en cache.  
  
3.  Substituez la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> dans la classe `ThisDocument` et rétablissez la protection du document.  
  
     Une fois le document enregistré, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de réappliquer la protection du document.  
  
### Exemple  
 L'exemple de code suivant montre comment mettre en cache des données dans un document Word protégé par un mot de passe.  Avant que le code ne retire la protection dans la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>, il enregistre la valeur <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> actuelle afin que le même type de protection puisse être rétabli dans la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### Compilation du code  
 Ajoutez ce code à la classe `ThisDocument` de votre projet.  Il suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.  
  
## Mise en cache dans les classeurs Excel  
 Dans les projets Excel, cette procédure est nécessaire uniquement lorsque vous protégez le classeur entier avec un mot de passe en utilisant la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>.  Elle n'est pas nécessaire si vous protégez uniquement une feuille de calcul spécifique avec un mot de passe en utilisant la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>.  
  
#### Pour mettre en cache des données dans un classeur Excel protégé par un mot de passe  
  
1.  Dans la classe `ThisWorkbook` ou une des classes `Sheet`*n*, marquez un champ public ou une propriété à mettre en cache.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
2.  Substituez la méthode <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> dans la classe `ThisWorkbook` et supprimez la protection du classeur.  
  
     Lorsque le classeur est enregistré, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de déprotéger le classeur.  Cela permet l'enregistrement des modifications apportées aux données mises en cache.  
  
3.  Substituez la méthode <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> dans la classe `ThisWorkbook` et rétablissez la protection du document.  
  
     Une fois le classeur enregistré, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle cette méthode pour vous donner la possibilité de réappliquer la protection du classeur.  
  
### Exemple  
 L'exemple de code suivant montre comment mettre en cache des données dans un classeur Excel protégé par un mot de passe.  Avant que le code ne supprime la protection dans la méthode <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>, il enregistre les valeurs <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> et <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> actuelles, afin que le même type de protection puisse être rétabli dans la méthode <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### Compilation du code  
 Ajoutez ce code à la classe `ThisWorkbook` de votre projet.  Il suppose que le mot de passe est stocké dans un champ nommé `securelyStoredPassword`.  
  
## Voir aussi  
 [Mise en cache des données](../vsto/caching-data.md)   
 [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  