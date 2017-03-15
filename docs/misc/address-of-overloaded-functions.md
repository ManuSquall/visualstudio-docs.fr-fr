---
title: "Adresse des fonctions surcharg&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fonctions surchargées des adresses (C++),"
  - "adresses (C++), surcharge retournée"
  - "adresse de la fonction, la surcharge de fonction"
  - "Ce pointeur, les fonctions surchargées"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Adresse des fonctions surcharg&#233;es
L’utilisation d’un nom de fonction sans arguments retourne l’adresse de cette fonction. Par exemple :  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 Dans l'exemple précédent, la première version de `Func` est sélectionnée et son adresse est copiée dans `pFunc`.  
  
 Le compilateur détermine la version de la fonction à sélectionner en recherchant une fonction avec une liste d'arguments qui correspond exactement à celle de la cible. Les arguments dans les déclarations de fonction surchargées sont comparés à l'un des éléments suivants :  
  
-   un objet initialisé \(comme indiqué dans l'exemple précédent\) ;  
  
-   le côté gauche d'une instruction d'assignation ;  
  
-   un argument formel d'une fonction ;  
  
-   un argument formel d'un opérateur défini par l'utilisateur ;  
  
-   un type de retour de fonction.  
  
 Si aucune correspondance exacte n'est trouvée, l'expression qui prend l'adresse de la fonction est ambiguë et une erreur est générée.  
  
 Notez que bien qu'une fonction non membre, `Func`, soit utilisée dans l'exemple précédent, les mêmes règles sont appliquées lors de la prise de l'adresse de fonctions membres surchargées.  
  
## Voir aussi  
 [Surcharge \(C\+\+\)](../misc/overloading-cpp.md)