---
title: "Le codage ne peut pas avoir la valeur Nothing | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le codage ne peut pas avoir la valeur Nothing
Une tentative de lecture ou d’écriture dans un fichier a échoué, car le paramètre `encoding` a la valeur `Nothing`, mais requiert une valeur valide.  
  
 <xref:System.Text.Encoding> est utilisé pour déterminer le codage à utiliser lors de l’écriture dans un fichier. La valeur par défaut est UTF\-8.  
  
### Pour corriger cette erreur  
  
-   Fournissez une valeur valide pour le paramètre `encoding`.  
  
## Voir aussi  
 [File Encodings](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-encodings)   
 [Reading from Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/reading-from-files)   
 [Writing to Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/writing-to-files)   
 [My.Computer.FileSystem.ReadAllText, méthode](http://msdn.microsoft.com/fr-fr/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText, méthode](http://msdn.microsoft.com/fr-fr/f507460c-87d9-4504-b74f-3ff825c7d5c4)