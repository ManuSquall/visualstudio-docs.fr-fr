---
title: "Avertissement du compilateur (niveau&#160;3) CS0414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0414"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0414"
ms.assetid: 6a0a80be-799b-4d9c-a7e0-6b91e9ce7be0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0414
Le champ privé 'field' est assigné, mais sa valeur n’est jamais utilisée  
  
 Cet avertissement peut se produire dans plusieurs scénarios dans lesquels le compilateur peut vérifier qu’une variable n’est jamais référencée :  
  
-   Une valeur de constante est assignée à un champ privé, mais ce dernier n’est jamais lu ensuite. Cette affectation inutile risque d’affecter les performances. Supprimez le champ.  
  
-   Une valeur de constante est assignée à un champ statique privé ou interne uniquement dans l’initialiseur. Transformez le champ en constante \(const\).  
  
-   Des valeurs de constante sont assignées à un champ privé ou interne qui n’est utilisé que dans des blocs exclus par des directives \#ifdef. Envisagez de placer le champ à l’intérieur du bloc \#ifdef.  
  
-   Des valeurs de constante sont assignées à un champ privé ou interne dans plusieurs emplacements, mais ce champ ne fait l’objet d’aucun autre accès. Si vous n’avez pas besoin de ce champ, envisagez de le supprimer. Sinon, utilisez\-le de manière appropriée.  
  
 Dans d’autres situations, ou lorsque la solution de contournement suggérée n’est pas acceptable, utilisez \#pragma 0414.  
  
 L’exemple suivant illustre un cas de génération d’une erreur CS0414 :  
  
```  
// CS0414 // compile with: /W3 class C { private int i = 1;  // CS0414 public static void Main() { } }  
```  
  
 **Remarque** Si la variable `i` est déclarée comme `protected or public`, aucune erreur n’est générée, car le compilateur ne peut pas savoir si une classe dérivée peut l’utiliser ou un autre code client peut instancier la classe et référencer la variable.  
  
## Voir aussi  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)   
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)