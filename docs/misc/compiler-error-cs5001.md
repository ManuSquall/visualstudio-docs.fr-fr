---
title: "Erreur du compilateur CS5001 | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS5001
Le programme 'programme' ne contient pas de méthode 'Main' statique adaptée à un point d’entrée  
  
 Cette erreur se produit quand aucune méthode [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) statique avec une signature appropriée n’a été trouvée dans le code qui génère un fichier exécutable. Cette erreur se produit également si la fonction du point d’entrée `Main` est définie avec une casse incorrecte, par exemple en minuscules \(`main`\).  
  
-   `Main` doit être déclaré comme statique et doit retourner [void](/dotnet/csharp/language-reference/keywords/void) ou [int](/dotnet/csharp/language-reference/keywords/int). De plus, il ne doit avoir aucun paramètre ou bien un paramètre de type `string[]`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS5001 :  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## Voir aussi  
 [Main\(\) et arguments de ligne de commande](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)