---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign (méthode)"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit l'alignement de l'image.  
  
## Syntaxe  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Paramètres  
 NewVal  
 \[in\]  La nouvelle valeur d'inscription d'image pour le fichier exécutable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les images \(fichiers exécutables chargés\) sont alignées aux limites spécifiées de mémoire.  Cette inscription peut être affecté par l'architecture du système actuelle et par les options de temps de compilation et de liaison.  L'alignement de l'image est toujours sur les limites d'octets.  Les valeurs suivantes d'alignement de l'image sont valides : 1, 2, 4, 8, 16, 32, et des limites de 64 octets.  
  
 L'inscription actuel d'image peut être récupéré par un appel à la méthode d' [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
>  L'image est déjà chargée pour que cette méthode peut être appelée.  La méthode d' `put_imageAlign` est adoptée en général lorsque l'image a été déplacée ou modifiée et une nouvelle inscription est requis.  
  
## Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)