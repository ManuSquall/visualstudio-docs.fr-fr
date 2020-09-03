---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179194"
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
 Pointeur de frame omis ; Informations FPO disponibles.  
  
 `FrameTypeTrap`  
 Trame d’interruption du noyau.  
  
 `FrameTypeTSS`  
 Trame d’interruption du noyau.  
  
 `FrameTypeStandard`  
 Frame de pile EBP standard.  
  
 `FrameTypeFrameData`  
 Pointeur de frame omis ; Informations sur les données de frame disponibles.  
  
 `FrameTypeUnknown`  
 Frame qui ne contient aucune information de débogage.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaStackFrame :: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
