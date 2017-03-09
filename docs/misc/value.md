---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value (mot clé)"
  - "types valeur, déclarer"
  - "mot clé __value, syntaxe"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [Classes and Structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Déclare une classe pour qu'elle soit de type \_\_value.  
  
## Syntaxe  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## Notes  
 Le type `__value` diffère des types `__gc` dans le sens où les variables de type `__value` contiennent directement leurs données, alors que les variables gérées pointent vers leurs données, qui sont stockées sur le tas Common Langage Runtime.  
  
 Les conditions suivantes s'appliquent aux types `__value` :  
  
-   Le mot clé `__value` ne peut pas être appliqué à une interface.  
  
-   Un type `__value` peut hériter d'un nombre illimité d'interfaces mais ne peut pas hériter d'autres types ou de types `__value`.  
  
-   Un type `__value` est sealed par définition. Pour plus d'informations, consultez [\_\_sealed](../misc/sealed.md).  
  
-   Il est possible d'utiliser un type `__value` partout où un type managé est autorisé.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser le mot clé `__value` avec le mot clé `__abstract`.  
  
 Un type `__value` peut être explicitement connecté à un pointeur **System::Object**. Il s'agit du boxing.  
  
 Les indications suivantes s'appliquent à l'incorporation d'un type valeur à l'intérieur d'un type `__nogc` :  
  
-   Le type valeur doit être **LayoutSequential** ou **LayoutExplicit**.  
  
-   Il ne peut pas comporter de membres de pointeurs gc.  
  
-   Le type valeur ne peut pas contenir des données membres privées.  
  
 Dans les Extensions managées pour C\+\+, les équivalents pour C\# class et C\# struct sont les suivants :  
  
|Extensions managées pour C\+\+|C\#|Pour plus d'informations|  
|------------------------------------|---------|------------------------------|  
|\_\_gc struct<br /><br /> ou<br /><br /> \_\_gc class|classe|mot clé [class](/dotnet/csharp/language-reference/keywords/class)|  
|\_\_value struct<br /><br /> ou<br /><br /> \_\_value class|struct|mot clé [struct](/dotnet/csharp/language-reference/keywords/struct)|  
  
## Exemple  
 Dans l'exemple suivant, un type `__value` \(`V`\) est déclaré puis deux instances du type `__value` sont manipulées :  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```