---
title: "Erreur du compilateur CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0844
Impossible d’utiliser la variable locale 'name' avant de la déclarer La déclaration de la variable locale masque le champ 'name'.  
  
 Un identificateur ne peut avoir qu’une seule signification dans un bloc donné. Les variables locales qui portent le même nom en tant que champs de classe peuvent masquer le champ en introduisant une deuxième signification pour l’identificateur. Ainsi, le compilateur génère une erreur quand vous faites référence à un champ de classe dans une méthode, puis déclarez une variable locale par le même nom.  
  
### Pour corriger cette erreur  
  
-   Utilisez `this.num` pour faire référence au champ de classe.  
  
-   Donnez à la variable locale un autre nom que celui du champ de classe.  
  
## Exemple  
 Le code suivant génère l’erreur CS0844 :  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```