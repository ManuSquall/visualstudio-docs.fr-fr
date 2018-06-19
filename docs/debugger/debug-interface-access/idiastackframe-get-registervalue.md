---
title: IDiaStackFrame::get_registerValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1c08258c98b46536f17f7819ce01c296d2d1900
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459543"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Récupère la valeur d’un registre spécifié comme indiqué dans le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `registerIndex`  
 [in] Parmi les [cv_hreg_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) valeurs d’énumération.  
  
 `pRetVal`  
 [out] Valeur stockée dans le Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md)