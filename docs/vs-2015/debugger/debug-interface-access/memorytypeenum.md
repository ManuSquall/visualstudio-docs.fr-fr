---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158131"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie le type de mémoire auquel accéder.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 `MemTypeCode`  
 Accède uniquement à la mémoire de code.  
  
 `MemTypeData`  
 Accède à des données ou à la mémoire de pile.  
  
 `MemTypeStack`  
 Accède uniquement à la mémoire de pile.  
  
 `MemTypeAny`  
 Accède à n’importe quel type de mémoire.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont passées à la méthode [IDiaStackWalkHelper :: ReadMemory (](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pour limiter l’accès à différents types de mémoire.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
