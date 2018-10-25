---
title: IDiaSymbol::get_oemSymbolId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3b15cbfc289a88059960603159db3a7d57fd011
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917165"
---
# <a name="idiasymbolgetoemsymbolid"></a>IDiaSymbol::get_oemSymbolId
Récupère la valeur d’ID du symbole fabricant (OEM).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] ID de symboles retourne d’un OEM affecté en interne  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 L’identificateur est une valeur unique créée par le SDK DIA pour marquer tous les symboles comme étant unique.  
  
 Cette propriété s’applique uniquement aux symboles avec un [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) type de `SymTagCustomType`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)