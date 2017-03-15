---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof (mot clé)"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**Remarque** Cette rubrique s'applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Retourne le **System::Type** d'un type spécifié.  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 où :  
  
 *typename*  
 Nom d'un type managé pour lequel vous souhaitez obtenir le nom **System::Type**. Notez que dans un programme managé, certains types natifs ont comme alias des types du Common Langage Runtime. Par exemple, `int` est un alias pour **System::Int32**.  
  
## Notes  
 L'opérateur **\_\_typeof** vous permet d'obtenir le type **System::Type** d'un type que vous spécifiez.**\_\_typeof** peut également servir à retourner une valeur **System::Type** dans un bloc d'attributs personnalisé. Pour plus d'informations sur la création de vos propres attributs, consultez [attribute](/visual-cpp/windows/attribute).  
  
## Exemple  
 Dans l'exemple suivant, un attribut personnalisé \(`AtClass`\) est appliqué à une classe \_\_gc \(`B`\). La valeur de l'attribut personnalisé est ensuite extraite avec **\_\_typeof** :  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## Sortie  
  
```  
in Type * constructor  
AtClass  
```