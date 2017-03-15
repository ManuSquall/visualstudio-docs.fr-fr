---
title: "Avertissement du compilateur (niveau&#160;3) CS1717 | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS1717
Assignation effectuée à la même variable ; souhaitiez\-vous assigner un autre élément ?  
  
 Cet avertissement se produit quand vous assignez une variable à elle\-même \(par exemple `a = a`.  
  
 Plusieurs erreurs courantes peuvent générer cet avertissement :  
  
-   Écriture de `a = a` comme condition d’une instruction **if**, par exemple `if (a = a)`. Vous souhaitiez probablement indiquer `if (a == a)`, qui est toujours vrai ; vous pouvez donc mentionner de façon plus concise `if (true)`.  
  
-   Erreur de frappe. Vous souhaitiez probablement indiquer `a = b`.  
  
-   Dans un constructeur dans lequel le paramètre porte le même nom que le champ, sans utilisation du mot clé **this** : vous souhaitiez probablement indiquer `this.a = a`.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1717.  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```