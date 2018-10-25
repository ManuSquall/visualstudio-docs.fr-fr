---
title: IDiaSymbol::get_hasNestedTypes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasNestedTypes method
ms.assetid: 1a8306bd-10dd-40a9-81fc-01f71c348484
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb894c305fa45216a0c7b6be7dfe10c19145b7d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936717"
---
# <a name="idiasymbolgethasnestedtypes"></a>IDiaSymbol::get_hasNestedTypes
Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur a imbriqué des définitions de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_hasNestedTypes (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si le type de données défini par l’utilisateur a imbriqué des définitions de type ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)