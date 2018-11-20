---
title: StackFrameTypeEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de80fd054459556e273427b666175751ced203fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740370"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie le type de frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



