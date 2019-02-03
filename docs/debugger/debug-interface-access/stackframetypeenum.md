---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 157ee347b52a3820811693732fce183b6f54a303
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917496"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Spécifie le type de frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Éléments  
 `FrameTypeFPO`  
 Pointeur de frame omis ; Information FPO est disponible.  
  
 `FrameTypeTrap`  
 Frame d’interruption du noyau.  
  
 `FrameTypeTSS`  
 Frame d’interruption du noyau.  
  
 `FrameTypeStandard`  
 Frame de pile EBP standard.  
  
 `FrameTypeFrameData`  
 Pointeur de frame omis ; Informations de données image disponibles.  
  
 `FrameTypeUnknown`  
 Frame qui n’a pas les informations de débogage.  
  
## <a name="remarks"></a>Notes  
 Les valeurs dans cette énumération sont retournées par un appel à la [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)