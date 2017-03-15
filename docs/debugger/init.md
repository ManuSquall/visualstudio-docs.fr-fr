---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prépare le composant dans les applications du diagnostic graphiques à capturer et enregister des informations graphiques dans un fichier journal de graphique.  
  
## Syntaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### Paramètres  
 `vsgLogGetter`  
 Un entité pouvant être appelée \- telle qu'une fonction, un pointeur de fonction, lambda, ou un object fonction \- qui prennent comme paramètres la longeur d'une mémoire tampon composée de `wchar_t` et un pointeur vers cette mémoire tampon, et retourne `void`.  Une fois appelée, l'entité appelée détermine le nom de fichier qui sera utilisé pour stocker des informations graphiques, et écrit à la mémoire tampon spécifiée avant de retourner.  
  
## Remarques  
 La fonction `Init` est appelée automatiquement lorsqu'une instance de la classe `VsgDbg` est construite en spécifiant le paramètre `bDefaultInit` de son constructeur comme `true`; sinon, `Init` doit être appelé explicitement avant de pouvoir activement entrer et les informations graphiques.  
  
 Vous pouvez valider et fermer le fichier journal en cours de utilisation de graphiques en appelant `UnInit`, puis tapez et stockez des informations graphiques dans un nouveau fichier journal de graphiques en appelant à nouveau `Init`.  Vous pouvez répéter cette opération autant de fois que vous souhaitez créer plusieurs fichier journal de graphiques indépendants en utilisant l'instance `VsgDbg`.  
  
## Voir aussi  
 [UnInit](../debugger/init.md)