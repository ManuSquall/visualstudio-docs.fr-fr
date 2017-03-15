---
title: "__sealed | Microsoft Docs"
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
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed (mot clé C++)"
  - "__sealed (mot clé)"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [sealed](/visual-cpp/windows/sealed-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Empêche une méthode d'être remplacée ou une classe d'être une classe de base.  
  
## Syntaxe  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## Notes  
 Le mot clé `__sealed` spécifie qu'une méthode de classe ne peut pas être remplacée ou qu'une classe ne peut pas être une classe de base.  
  
 En utilisant le mot clé `__sealed`, conservez les points suivants à l'esprit :  
  
-   Une méthode virtuelle `__sealed` ne peut pas être remplacée.  
  
-   Si une méthode membre non virtuelle est marquée `__sealed`, la qualification `__sealed` est ignorée.  
  
-   Une méthode `__sealed` ne peut pas être pure.  
  
-   Le **\_\_sealed** mot clé n’est pas autorisé lorsqu’il est utilisé avec le [\_\_interface](/visual-cpp/cpp/interface) \(mot clé\).  
  
 Lorsqu'une classe \(ou struct\) est marquée avec `__sealed`, la classe ne peut pas être utilisée comme classe de base. Exemple :  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser le mot clé `__sealed` avec le mot clé `__abstract`.  
  
## Exemple  
 Dans l'exemple suivant, une méthode virtuelle sealed \(`f`\) est déclarée. La fonction est ensuite remplacée dans `main()`, provoquant une erreur de compilation :  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```