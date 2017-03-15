---
title: "Les instructions &#39;Line&#39; ne sont plus prises en charge (erreur du compilateur Smart Device/Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Line&#39; ne sont plus prises en charge (erreur du compilateur Smart Device/Visual Basic)
L’instruction `Line` n’est plus prise en charge. La fonctionnalité d’E\/S de fichier est normalement disponible sous la forme <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName>, mais la version ciblée de .NET Compact Framework ne la prend pas en charge.  
  
 **ID d’erreur :** BC30768  
  
### Pour corriger cette erreur  
  
-   Pour un accès aux fichiers, utilisez les fonctions définies dans l’espace de noms <xref:System.IO>.  
  
-   Pour des graphiques, utilisez <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)