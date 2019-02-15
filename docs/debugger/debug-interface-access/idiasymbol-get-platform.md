---
title: IDiaSymbol::get_platform | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdb4ee71c05cf065f6a76ddb1ab3c2a0eddd42f5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009126"
---
# <a name="idiasymbolgetplatform"></a>IDiaSymbol::get_platform
Récupère le type de plateforme pour laquelle le module a été compilée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur de la [CV_CPU_TYPE_e (énumération)](../../debugger/debug-interface-access/cv-cpu-type-e.md) type d’énumération qui spécifie la plateforme pour laquelle du module a été compilé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CPU_TYPE_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)