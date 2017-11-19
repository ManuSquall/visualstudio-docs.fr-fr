---
title: IDiaStackWalkFrame::get_registerValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d4a71d96e8072dcf56d848e43bb81fdf9e37172
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
Récupère la valeur d’un Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] Une valeur à partir de la [cv_hreg_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant le Registre pour obtenir la valeur.  
  
 `pRetVal`  
 [out] Retourne la valeur actuelle du Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md)