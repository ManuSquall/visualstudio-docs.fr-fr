---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::put_loadAddress (méthode)"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit l'adresse du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.  
  
## Syntaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Paramètres  
 `NewVal`  
 \[in\]  adresse de charge pour le fichier exécutable.  
  
## Notes  
 Les propriétés d'adresse virtuelle \(VA\) de symboles sont calculées en utilisant la valeur de cette méthode.  Les adresses virtuelles ne sont pas calculées à moins que cette propriété a la valeur différente de zéro.  
  
> [!NOTE]
>  Vous devez appeler cette méthode lorsque vous obtenez l'objet d' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) et de avant de démarrer à l'aide de l'objet si vous devez utiliser les propriétés virtuelles sur des symboles.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)