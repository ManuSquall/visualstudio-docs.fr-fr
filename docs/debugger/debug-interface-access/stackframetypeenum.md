---
title: StackFrameTypeEnum | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 329661e857859a1f6452506ba2984ac962bf4ff2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
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
 Pointeur de frame omis ; Information sur FPO disponible.  
  
 `FrameTypeTrap`  
 Cadre du noyau.  
  
 `FrameTypeTSS`  
 Cadre du noyau.  
  
 `FrameTypeStandard`  
 Frame de pile EBP standard.  
  
 `FrameTypeFrameData`  
 Pointeur de frame omis ; Informations de données image disponibles.  
  
 `FrameTypeUnknown`  
 Cadre qui ne dispose pas des informations de débogage.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par un appel à la [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)