---
title: "Erreur du compilateur CS0412 | Microsoft Docs"
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
  - "CS0412"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0412"
ms.assetid: eeb2afbc-9416-4bcf-b116-d6adc5cfd4ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0412
'generic' : un paramètre ou une variable locale ne peut pas avoir le même nom qu’un paramètre de type de méthode  
  
 Il existe un conflit de nom entre le paramètre de type d’une méthode générique et une variable locale, au niveau de la méthode ou de l’un des paramètres de la méthode. Pour éviter cette erreur, renommez les paramètres ou les variables locales incompatibles.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0412 :  
  
```  
// CS0412.cs using System; class C { // Parameter name is the same as method type parameter name public void G<T>(int T)  // CS0412 { } public void F<T>() { // Method local variable name is the same as method type // parameter name double T = 0.0;  // CS0412 Console.WriteLine(T); } public static void Main() { } }  
```