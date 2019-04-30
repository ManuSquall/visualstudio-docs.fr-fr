---
title: IDiaFrameData::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_cplusplusExceptionHandling method
ms.assetid: 54ee9cde-ce8e-45f1-809c-6fbad800d850
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12ccb2770cc15962f3899b99f14dd8c7f342c3cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553030"
---
# <a name="idiaframedatagetcplusplusexceptionhandling"></a>IDiaFrameData::get_cplusplusExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui indique si des exceptions C++ sont en vigueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si C++ gestion des exceptions est en vigueur ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Pour déterminer si des structured exception gestion est en vigueur (qui est très différent de C++ gestion des exceptions), appelez le [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)
