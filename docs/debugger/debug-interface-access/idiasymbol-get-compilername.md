---
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7f8b9c0f670522e9ea8b2d6fa46e79e3f01594d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938056"
---
# <a name="idiasymbolgetcompilername"></a>IDiaSymbol::get_compilerName
Retourne le nom du compilateur utilisé pour générer le [Compiland](../../debugger/debug-interface-access/compiland.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_compilerName (  
   BSTR *pName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pName`  
 Pointeur vers un BSTR qui contiendra le nom Unicode du compilateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)