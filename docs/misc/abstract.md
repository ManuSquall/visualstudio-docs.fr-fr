---
title: "__abstract | Microsoft Docs"
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
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes (C++), abstract"
  - "__abstract (mot clé)"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Déclare une classe managée qui ne peut pas être instanciée directement.  
  
## Syntaxe  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## Notes  
 Le mot clé `__abstract` déclare que la classe cible peut être utilisée uniquement comme une classe de base d'une autre classe. L'application de `__abstract` à une classe ou à une structure n'implique pas que le résultat est un classe \_\_gc ou une structure \_\_gc.  
  
 Différente de la notion C\+\+ de classe de base [abstraite](/visual-cpp/cpp/abstract-classes-cpp), une classe avec le mot clé `__abstract` peut définir ses fonctions membres.  
  
> [!NOTE]
>  Le mot clé `__abstract` n'est pas autorisé en cas d'utilisation avec le mot clé `__value` ou `__sealed` et il est redondant en cas d'utilisation avec le mot clé `__interface`.  
  
## Exemple  
 Dans l'exemple suivant, la classe `Derived` est dérivée d'une classe de base abstraite \(`Base`\). L'instanciation est ensuite tentée sur les deux, mais seule `Derived` réussit.  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```