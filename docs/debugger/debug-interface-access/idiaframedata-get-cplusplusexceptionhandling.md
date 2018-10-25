---
title: IDiaFrameData::get_cplusplusExceptionHandling | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_cplusplusExceptionHandling method
ms.assetid: 54ee9cde-ce8e-45f1-809c-6fbad800d850
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9c35668e7998cf11773cca9db4bfdbf8af11701
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832057"
---
# <a name="idiaframedatagetcplusplusexceptionhandling"></a>IDiaFrameData::get_cplusplusExceptionHandling
Récupère un indicateur qui indique si des exceptions C++ sont en vigueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si la gestion des exceptions C++ est en vigueur ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Pour déterminer si des structured exception gestion est activé (ce qui est très différent de la gestion des exceptions C++), appelez le [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)