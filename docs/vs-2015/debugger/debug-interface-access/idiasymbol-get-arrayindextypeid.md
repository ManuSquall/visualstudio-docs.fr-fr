---
title: IDiaSymbol::get_arrayIndexTypeId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexTypeId method
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b33d5280e73521e636aaaf1d56861ce450c7df1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839430"
---
# <a name="idiasymbolget_arrayindextypeid"></a>IDiaSymbol::get_arrayIndexTypeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère l’identificateur de type d’index de tableau du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_arrayIndexTypeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne l’ID de type d’index de tableau du symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 L’identificateur est une valeur unique créée par le kit de développement logiciel (SDK) DIA pour marquer tous les symboles comme étant uniques.  
  
## <a name="requirements"></a>Spécifications  
  
|Condition requise|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
