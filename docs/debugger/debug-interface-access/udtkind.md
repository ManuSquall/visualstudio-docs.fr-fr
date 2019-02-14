---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaca67dd56fa34993e46693d6274bc4b7b593006
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929404"
---
# <a name="udtkind"></a>UdtKind
Décrit un certain nombre de type défini par l’utilisateur (UDT).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Éléments  
 UdtStruct  
 UDT est une structure.  
  
 UdtClass  
 UDT est une classe.  
  
 UdtUnion  
 UDT est une union.  
  
 UdtInterface  
 UDT est une interface.  
  
## <a name="remarks"></a>Remarques  
 Les valeurs dans cette énumération sont retournées par la [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)