---
title: IDiaSymbol::get_isCVTCIL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34868f48cf330670c3c14b3979897d80b5525f40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839594"
---
# <a name="idiasymbolget_iscvtcil"></a>IDiaSymbol::get_isCVTCIL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui spécifie si le module a été converti à partir d’un module Common Intermediate Language (CIL) en un module natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_isCVTCIL(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 à Retourne `TRUE` si le module a été converti du code CIL en code natif ; sinon, retourne `FALSE` .  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété est disponible à partir du `SymTagCompilandDetails` type de symbole (consultez [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md).  
  
## <a name="requirements"></a>Spécifications  
  
|Condition requise|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
