---
title: "Erreur du compilateur CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0118
'construct1\_name' est un 'construct1' mais il est utilisé comme un 'construct2'  
  
 Le compilateur a détecté une situation dans laquelle une construction a été utilisée de manière erronée ou une opération non autorisée a été tentée sur une construction. Exemples courants :  
  
-   Une tentative d’instancier un espace de noms \(au lieu d’une classe\)  
  
-   Une tentative d’appeler un champ \(au lieu d’une méthode\)  
  
-   Une tentative d’utiliser un type en tant que variable  
  
-   Une tentative d’utiliser un alias externe en tant que type  
  
 Pour résoudre cette erreur, assurez\-vous que l’opération que vous exécutez est valide pour le type sur lequel vous exécutez l’opération.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0118.  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```