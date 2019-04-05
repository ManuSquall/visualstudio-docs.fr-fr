---
title: IDiaStackFrame::get_type | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4b0653de51ece59584076def76988958ae612d5
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58954146"
---
# <a name="idiastackframegettype"></a>IDiaStackFrame::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le type de trame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur de la [StackFrameTypeEnum (énumération)](../../debugger/debug-interface-access/stackframetypeenum.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [StackFrameTypeEnum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md)
