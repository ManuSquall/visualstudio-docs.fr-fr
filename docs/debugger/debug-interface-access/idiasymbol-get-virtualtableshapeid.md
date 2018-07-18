---
title: IDiaSymbol::get_virtualTableShapeId | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 694dddcbfed79a66c27e2069b3fc7aab7ce7c5f0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472267"
---
# <a name="idiasymbolgetvirtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
Récupère l’identificateur de symbole de forme de table virtuelle du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_virtualTableShapeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’ID de symbole de forme de table virtuelle du symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 L’identificateur est une valeur unique créée par le SDK DIA pour marquer tous les symboles de manière unique.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)