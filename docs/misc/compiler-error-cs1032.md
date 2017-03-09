---
title: "Erreur du compilateur CS1032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1032
Impossible de définir\/annuler la définition des symboles de préprocesseur à la suite du premier jeton du fichier  
  
 Les [directives de préprocesseur](/dotnet/csharp/language-reference/preprocessor-directives/index)`#define` et `#undef` doivent être utilisées au début d’un programme, avant les autres mots clés, notamment ceux utilisés dans la déclaration d’espace de noms.  
  
 L’exemple suivant génère l’erreur CS1032 :  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```