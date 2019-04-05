---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0edf1d1da0538c33556af84913c5bb959a0328c7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953646"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le type d’un pointeur de la table de base virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Notes  
 Un pointeur de la table de base virtuelle (`vbtptr`) est un pointeur masqué dans un [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vtable qui gère l’héritage de classes de base virtuelles. Un `vbtptr` peut avoir différentes tailles variables selon les classes héritées.  
  
 Cette méthode retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui peut être utilisée pour déterminer la taille de la vbtptr.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
