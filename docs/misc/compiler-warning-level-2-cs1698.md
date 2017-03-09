---
title: "Avertissement du compilateur (niveau&#160;2) CS1698 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS1698
La référence d’assembly circulaire 'AssemblyName1' ne correspond pas au nom de l’assembly de sortie 'AssemblyName2'. Essayez d’ajouter une référence à 'AssemblyName1' ou de modifier le nom de l’assembly de sortie pour qu’ils correspondent.  
  
 L’avertissement CS1698 se produit quand une référence d’assembly est incorrecte, par exemple si un assembly référencé est recompilé. Pour résoudre ce problème, ne remplacez pas un assembly qui est lui\-même une dépendance d’un assembly que vous référencez.  
  
## Exemple  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## Exemple  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1698.  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```