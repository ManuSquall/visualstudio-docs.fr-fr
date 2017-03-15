---
title: "Erreur du compilateur CS0313 | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0313
Impossible d’utiliser le type 'type1' comme paramètre de type 'parameter name' dans le type ou la méthode générique 'type2'. Le type Nullable 'type1' ne satisfait pas la contrainte de 'type2'. Les types Nullable ne peuvent satisfaire aucune des contraintes d’interface.  
  
 Un type Nullable n’est pas équivalent à son pendant non Nullable. Dans l’exemple qui suit, `ImplStruct` satisfait la contrainte `BaseInterface`, mais `ImplStruct?` ne la satisfait pas, car `Nullable<ImplStruct>` n’implémente pas `BaseInterface`.  
  
### Pour corriger cette erreur  
  
1.  Par exemple, à l’aide du code suivant, vous pourriez spécifier un `ImplStruct` simple en tant que premier argument de type dans l’appel à `TestMethod`. Ensuite, vous pourriez modifier `TestMethod` pour créer une version Nullable de `Implstruct` dans son instruction return :  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## Exemple  
 Le code suivant génère l’erreur CS0313 :  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## Voir aussi  
 [Types Nullable](/dotnet/csharp/programming-guide/nullable-types/index)