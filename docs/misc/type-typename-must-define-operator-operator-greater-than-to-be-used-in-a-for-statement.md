---
title: "Le type &#39;&lt;nom_type&gt;&#39; doit d&#233;finir l’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; &#224; utiliser dans une instruction &#39;For&#39; | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; doit d&#233;finir l’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; &#224; utiliser dans une instruction &#39;For&#39;
Une boucle `For` spécifie une variable de compteur d’un type qui ne prend pas en charge un opérateur obligatoire.  
  
 La variable de compteur dans une boucle `For` peut être de n’importe quel type de données qui prend en charge tous les opérateurs suivants :  
  
-   Supérieur ou égal à \(`>=`\)  
  
-   Inférieur ou égal à \(`<=`\)  
  
-   Addition \(`+`\)  
  
-   Soustraction \(`-`\)  
  
 Si vous utilisez un type de données numérique pour la variable de compteur, tous les opérateurs précédents sont pris en charge. Si vous utilisez une classe ou une structure définie par l’utilisateur, vous devez définir tous les opérateurs précédents sur cette classe ou structure.  
  
 Notez également que les types de données des expressions `start`, `end` et `step` dans l’instruction `For` doivent s’étendre au type de données de la variable de compteur. Si la variable de compteur est une classe ou une structure définie par l’utilisateur et que l’expression `start`, `end` ou `step` est d’un type différent, vous devez définir l’opérateur de conversion `CType` pour effectuer la conversion nécessaire.  
  
 **ID d’erreur :** BC33038  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l’orthographe du type de données de variable de compteur est correcte.  
  
2.  Si vous utilisez une structure ou une classe définie par l’utilisateur pour la variable de compteur, définissez tous les opérateurs requis sur cette classe ou structure.  
  
3.  En fonction des types de données des expressions `start`, `end` et `step`, vous devrez peut\-être définir un ou plusieurs opérateurs de conversion `CType` pour les convertir vers le type de données de la variable de compteur.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [CType, fonction](/dotnet/visual-basic/language-reference/functions/ctype-function)