---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box (mot clé)"
  - "boxing"
  - "unboxing"
  - "conversion boxing, le mot clé __box"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  Cette rubrique s’applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [Boxing](/visual-cpp/windows/boxing-cpp-component-extensions) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Crée une copie managée d'un objet classe \_\_value.  
  
## Syntaxe  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## Notes  
 Le mot clé `__box` est utilisé pour créer un objet managé \(dérivé de **System::ValueType**\) à partir d'un objet classe\_\_value existant. Lorsque le mot clé `__box` est appliqué à une classe\_\_value :  
  
-   Un objet managé est alloué sur le tas du Common Language Runtime.  
  
-   La valeur actuelle de l'objet classe\_\_value est copiée au niveau du bit dans l'objet managé.  
  
-   L'adresse du nouvel objet managé est retournée.  
  
 Ce processus est appelé « boxing ». Cela permet à tout objet classe\_\_value d'être utilisé dans les routines génériques qui fonctionnent pour tout objet managé car l'objet managé hérite indirectement de **System::Object** \(puisque **System::ValueType** hérite de **System::Object**\).  
  
> [!NOTE]
>  L'objet boxed nouvellement créé est une copie de l'objet classe\_\_value. Par conséquent, les modifications apportées à la valeur de l'objet boxed n'affectent pas le contenu de l'objet classe\_\_value.  
  
## Exemple  
 Voici un exemple qui effectue la conversion boxing et unboxing :  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 Dans l'exemple suivant, un type de valeur non managé \(`V`\) est boxed et passé comme paramètre managé à la fonction `Positive`.  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**