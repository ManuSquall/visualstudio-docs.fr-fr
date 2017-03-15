---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit par sa présence si une instance d'une classe par défaut [VsgDbg, classe](../debugger/vsgdbg-class.md) qui fournit la capture de programmation interface est fournie.  
  
## Syntaxe  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## Valeur  
 Un symbole de préprocesseur qui détermine par sa présence ou absence si une instance par défaut de la classe `VsgDbg` est fournie.  Si ce symbole est défini, aucune instance par défaut de la classe `VsgDbg` n'est fournie ; sinon, une instance par défaut est fournie et initialisée avant que votre programme.  
  
 L'interface de programmation de capture est fournie via un pointeur qui a une portée globale, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## Remarques  
 L'instance par défaut suffit souvent, mais pour utiliser l'interface de programmation de capture à l'intérieur d'une DLL lorsque le périphérique D3D a été créé en dehors de la DLL, vous devez créer et gérer votre propre instance de la classe `VsgDbg`.  Si vous exécutez votre propre interface à la capture programmée API de capture de cette façon, désactivez l'instance par défaut en définissant `VSG_NODEFAULT_INSTANCE` pour éviter la charge mémoire.  
  
 Si l'instance par défaut n'est pas désactivée, elle est initialisée automatiquement avant que votre programme ne fonctionne et soit automatiquement détruit lorsque votre programme.  Vous ne devez pas initialiser ou dé\-initialiser cette instance explicitement.  
  
 Pour désactiver l'instance par défaut, vous devez définir `VSG_NODEFAULT_INSTANCE` avant d'inclure `vsgcapture.h` dans votre programme.  
  
## Exemple  
 Cet exemple montre comment désactiver l'instance par défaut :  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```