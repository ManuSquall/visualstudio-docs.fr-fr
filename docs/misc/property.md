---
title: "__property | Microsoft Docs"
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
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property (mot clé)"
  - "classes managées"
  - "classes de propriétés (C++), gérée"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [property](/visual-cpp/windows/property-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Déclare une propriété scalaire ou indexée pour la classe managée.  
  
## Syntaxe  
  
```  
  
__property  
function-declarator  
  
```  
  
## Notes  
 Le mot clé `__property` introduit la déclaration d'une propriété et peut figurer dans un type classe, interface ou valeur. Une propriété peut avoir une fonction d'accesseur Get \(lecture seule\), une fonction d'accesseur Set \(écriture seule\) ou les deux \(lecture\-écriture\).  
  
> [!NOTE]
>  Un nom de propriété ne peut pas correspondre au nom de la classe managée qui la contient. Le type de retour de la fonction d'accesseur Get doit correspondre au type du dernier paramètre d'une fonction d'accesseur Set correspondante.  
  
## Exemple  
 Dans l'exemple ci\-dessous, une propriété scalaire \(`Size`\) est ajoutée à la déclaration `MyClass`. La propriété est alors implicitement définie et extraite à l'aide des fonctions `get_Size` et `set_Size` :  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## Sortie  
  
```  
0  
4  
4  
```