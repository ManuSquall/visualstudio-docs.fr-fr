---
title: "Erreur du compilateur CS1643 | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1643
Tous les chemins de code ne retournent pas nécessairement une valeur de la méthode de type 'type\!'  
  
 Cette erreur se produit si un corps de délégué ne contient pas d’instruction return ou si elle en contient une mais que le compilateur ne peut pas vérifier si elle sera atteinte. Dans l’exemple ci\-dessous, le compilateur ne tente pas de prédire le résultat de la condition de création de branche afin de vérifier que le bloc de méthode anonyme retourne toujours une valeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1643 :  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```