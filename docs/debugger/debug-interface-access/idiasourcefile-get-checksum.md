---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum (méthode)"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les octets de checksum.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Paramètres  
 `cbData`  
 \[in\]  taille de la mémoire tampon de données, en octets.  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets de checksum.  Ce paramètre ne peut pas être `NULL`.  
  
 `data`  
 \[in, out\]  Une mémoire tampon qui est remplie avec les octets de checksum.  Si ce paramètre est `NULL`, alors `pcbData` retourne le nombre d'octets requis.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour déterminer le type d'algorithme de checksum utilisé pour générer des octets de checksum, appelez la méthode d' [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 Le checksum est habituellement générée de l'image du fichier source afin de les modifications apportées au fichier source sont répercutées dans les modifications des octets de checksum.  Si les octets de checksum ne correspondent pas à un checksum générée de l'image chargée du fichier, le fichier doit être considéré comme endommagé ou falsifié.  
  
 Les checksums classiques ne sont jamais supérieures à une taille de 32 octets mais ne supposent pas qui est la taille maximale d'un checksum.  Définissez le paramètre d' `data` à `NULL` pour obtenir le nombre d'octets requis pour récupérer le checksum.  Ensuite allouez une mémoire tampon de la taille appropriée et appelez cette méthode une fois de plus avec la nouvelle mémoire tampon.  
  
## Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)