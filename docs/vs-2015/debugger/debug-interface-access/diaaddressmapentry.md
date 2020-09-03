---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164353"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Décrit une entrée dans une table d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Éléments  
 `rva`  
 Une adresse virtuelle relative (RVA) dans l’image A.  
  
 `rvaTo`  
 L’adresse virtuelle relative `rva` est mappée à dans l’image B.  
  
## <a name="remarks"></a>Notes  
 Une carte d’adresses fournit une traduction d’une disposition d’image (A) à une autre (B). Un tableau de `DiaAddressMapEntry` structures triées par `rva` définit un mappage d’adresses.  
  
 Pour traduire une adresse, `addrA` , dans l’image A en une adresse, `addrB` , dans l’image B, procédez comme suit :  
  
1. Recherchez l’entrée dans la carte, `e` , avec la valeur la plus grande `rva` inférieure ou égale à `addrA` .  
  
2. Définissez `delta = addrA – e.rva`.  
  
3. Définissez `addrB = e.rvaTo + delta`.  
  
   Un tableau de `DiaAddressMapEntry` structures est passé à la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
