---
title: StackFrameTypeEnum | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37d8e960d256b8746781668068978aa72f45155c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Les valeurs de cette énumération sont retournées par un appel à la [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)