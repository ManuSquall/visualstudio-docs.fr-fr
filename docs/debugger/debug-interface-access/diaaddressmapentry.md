---
title: DiaAddressMapEntry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 501defcd2274ab32624a97b9a1463e8f4a515c1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819054"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Décrit une entrée dans un mappage d’adresses.  
  
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
  
## <a name="remarks"></a>Notes  
 Un mappage d’adresses fournit une traduction à partir de la disposition d’une image (A) à un autre (B). Un tableau de `DiaAddressMapEntry` structures triés par `rva` définit un mappage d’adresses.  
  
 Pour convertir une adresse, `addrA`, dans l’image A une adresse, `addrB`, dans l’image B, procédez comme suit :  
  
1. Rechercher le mappage de l’écriture, `e`, avec le plus grand `rva` inférieure ou égale à `addrA`.  
  
2. Définir `delta = addrA - e.rva`.  
  
3. Définir `addrB = e.rvaTo + delta`.  
  
   Un tableau de `DiaAddressMapEntry` structures est passé à la [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : dia2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)