---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cb880f82097b8780b7203886977077dd3c16682
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036899"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Récupère le type d’un pointeur de la table de base virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`pRetVal`|[out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui spécifie le type de table de base.|  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Un pointeur de la table de base virtuelle (`vbtptr`) est un pointeur masqué dans un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable qui gère l’héritage de classes de base virtuelles. Un `vbtptr` peut avoir différentes tailles variables selon les classes héritées.  
  
 Cette méthode retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui peut être utilisée pour déterminer la taille de la vbtptr.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)