---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "11/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_nogc (déclarations de type)"
  - "classes (C++), le type non managé"
  - "classes non managées, déclaration de"
  - "classes non managées"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Dans la nouvelle syntaxe, vous n'avez pas besoin de marquer explicitement un type comme non managé.  
  
 Déclare explicitement un type non managé.  
  
## Syntaxe  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## Notes  
 Le mot clé `__nogc` est utilisé pour spécifier explicitement qu'un objet est alloué sur le tas C\+\+ standard. Ce mot clé est facultatif. Si vous ne spécifiez pas `__gc` ou `__nogc` devant une déclaration de classe, sa valeur par défaut est `__nogc`.  
  
 Les objets de ce type sont semblables aux objets C\+\+ car ils sont alloués à partir du tas C\+\+ standard et ne sont pas soumis aux restrictions d'un objet managé.  
  
 Le mot clé `__nogc` est également utilisé lorsqu'un objet de type \_\_value est explicitement alloué sur le tas C\+\+ standard :  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  Le mot clé `__nogc` peut également être appliqué aux types tableau et pointeur.  
  
 Un pointeur gc ne peut pas être membre d'une classe `__nogc`. Consultez [\_\_value](../misc/value.md) pour obtenir des instructions sur l'incorporation d'un type valeur dans une classe `__nogc`.  
  
## Exemple  
 Dans l'exemple suivant, une classe non managée est déclarée \(`X`\) et un objet est instancié et modifié :  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**