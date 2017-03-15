---
title: "__pin | Microsoft Docs"
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
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointeurs épingle, mot clé __pin"
  - "types non managés"
  - "__pin (mot clé)"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**Remarque** Cette rubrique s'applique uniquement à la version 1 des extensions managées pour C\+\+. Cette syntaxe doit être utilisée uniquement pour conserver le code de la version 1. Consultez [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) Pour plus d’informations sur l’utilisation de la fonctionnalité équivalente dans la nouvelle syntaxe.  
  
 Empêche un objet ou un objet incorporé d’une classe managée d’être déplacé par le Common Langage Runtime pendant une opération garbage collection.  
  
## Syntaxe  
  
```  
  
__pin   
identifier  
  
```  
  
## Notes  
 Le mot clé `__pin` déclare un pointeur vers un objet ou un objet incorporé d'une classe managée et empêche le déplacement de cet objet pendant l'opération garbage collection par le Common Langage Runtime. Cela est utile lors de la transmission de l'adresse d'une classe managée à une fonction non managée car l'adresse ne changera pas de manière inattendue pendant la résolution de l'appel de fonction non managé.  
  
 Un pointeur épingle reste valide dans sa portée lexicale. Dès que le pointeur épingle est hors de portée, l'objet n'est plus considéré comme épinglé \(sauf si, bien entendu, il existe d'autres pointeurs épingle pointant vers ou dans l'objet\).  
  
 Le MSIL n'a aucun concept de « portée de bloc » \(toutes les variables locales se trouvent dans la portée de la fonction\). Pour que le système sache que l'épinglage n'a plus lieu, le compilateur génère un code qui assigne la valeur Null au pointeur épingle. C'est également ce que vous pouvez faire vous\-même, si vous devez supprimer l'objet sans laisser le bloc.  
  
 Vous ne devez pas convertir votre pointeur épingle en un pointeur non managé et continuer à utiliser ce pointeur non managé une fois que l'objet n'est plus épinglé \(une fois que le pointeur épingle est hors de portée\). Contrairement aux pointeurs gc, les pointeurs épingle peuvent être convertis en nogc, des pointeurs non managés. Toutefois, il revient à l'utilisateur de conserver l'épinglage pendant que le pointeur non managé est utilisé.  
  
 Il ne faut pas utiliser un pointeur épinglé pour obtenir l'adresse d'une variable, puis utiliser cette adresse une fois le pointeur épingle hors de portée.  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 L'exemple suivant présente le comportement correct :  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## Exemple  
 Dans l'exemple suivant, l'objet qui est pointé par `pG` est épinglé jusqu'à ce qu'il passe hors de portée :  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## Sortie  
  
```  
1  
```