---
title: DiaAddressMapEntry | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1324ea79ec60a61e315253573b9d4aa3ced2695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Décrit une entrée dans une table d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Éléments  
 `rva`  
 Une adresse virtuelle relative (RVA) dans l’image A.  
  
 `rvaTo`  
 L’adresse virtuelle relative `rva` est mappé dans l’image B.  
  
## <a name="remarks"></a>Remarques  
 Un mappage d’adresse fournit une traduction à partir de la disposition d’une image (A) à un autre (B). Un tableau de `DiaAddressMapEntry` structures triés par `rva` définit un mappage d’adresse.  
  
 Pour convertir une adresse, `addrA`, dans l’image A une adresse, `addrB`, dans l’image B, procédez comme suit :  
  
1.  Rechercher le mappage de l’écriture, `e`, avec le plus grand `rva` inférieure ou égale à `addrA`.  
  
2.  Set `delta = addrA - e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 Un tableau de `DiaAddressMapEntry` structures est passé à la [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dia2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)