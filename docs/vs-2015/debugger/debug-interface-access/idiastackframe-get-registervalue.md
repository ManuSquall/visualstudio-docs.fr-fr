---
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 496d15d8bfed0fc6d674e09a2bc9046788e11ca1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505356"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaStackFrame::get_registerValue](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackframe-get-registervalue).  
  
Récupère la valeur d’un registre spécifié, tel que stocké dans le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `registerIndex`  
 [in] Parmi les [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) valeurs d’énumération.  
  
 `pRetVal`  
 [out] Valeur stockée dans le Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)



