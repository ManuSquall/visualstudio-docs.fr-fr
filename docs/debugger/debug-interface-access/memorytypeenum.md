---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a83a37a3aa454885d714be667ca7678ae543ff09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875914"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Spécifie le type de mémoire à accéder.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 `MemTypeCode`  
 Accède à du code uniquement mémoire.  
  
 `MemTypeData`  
 Accède aux données ou pile de mémoire.  
  
 `MemTypeStack`  
 Accès uniquement mémoire de la pile.  
  
 `MemTypeAny`  
 Accède à n’importe quel type de mémoire.  
  
## <a name="remarks"></a>Notes  
 Les valeurs dans cette énumération sont transmises à la [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) méthode pour limiter l’accès à différents types de mémoire.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)