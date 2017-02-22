---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType (méthode)"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type de checksum.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le type de checksum.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le type de checksum est une valeur qui peut être mappée à un algorithme de checksum.  Par exemple, le format de fichier PDB standard peut généralement avoir une des valeurs suivantes :  
  
|Type de checksum|nom de CryptoAPI|Description|  
|----------------------|----------------------|-----------------|  
|0|\<aucune\>|Aucun présent de checksum.|  
|1|`CALG_MD5`|checksum générée avec l'algorithme de hachage MD5.|  
|2|`CALG_SHA1`|checksum générée avec l'algorithme de hachage SHA1.|  
  
 les noms d' `CryptoAPI` sont de l'énumération d' `ALG_ID` .  Pour plus d'informations sur les algorithmes de hachage, consultez la section d' `CryptoAPI` Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Pour obtenir les octets de checksum réel du fichier source, appelez la méthode d' [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .  
  
## Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)