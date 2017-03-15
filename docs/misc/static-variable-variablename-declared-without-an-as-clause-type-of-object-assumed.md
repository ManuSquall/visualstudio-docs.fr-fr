---
title: "Variable statique &#39;&lt;nom_variable&gt;&#39; d&#233;clar&#233;e sans clause &#39;As&#39;&#160;; type &#39;Object&#39; pris par d&#233;faut | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable statique &#39;&lt;nom_variable&gt;&#39; d&#233;clar&#233;e sans clause &#39;As&#39;&#160;; type &#39;Object&#39; pris par d&#233;faut
Le compilateur ne déduit pas le type de données des variables locales statiques. Dans l’exemple suivant, avec `Option Strict` défini sur `Off`, le type de `m` est `Object`, que `Option Infer` ait la valeur `On` ou `Off`. L’inférence de type local ne s’applique pas.  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42111  
  
### Pour traiter cet avertissement  
  
-   Spécifiez le type de données des variables locales statiques.  
  
     Par exemple, si vous voulez que `m` soit de type `Integer` dans l’exemple précédent, spécifiez le type dans la déclaration.  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD Comment : allonger la durée de vie d’une variable](http://msdn.microsoft.com/fr-fr/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)