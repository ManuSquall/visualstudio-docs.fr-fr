---
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6276247bb93e7482dda713c95b40a68809c0237
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839861"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retourne le nom du compilateur utilisé pour générer le [compiland](../../debugger/debug-interface-access/compiland.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_compilerName (  
   BSTR *pName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pName`  
 Pointeur vers un BSTR qui contient le nom Unicode du compilateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
  
|Condition requise|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
