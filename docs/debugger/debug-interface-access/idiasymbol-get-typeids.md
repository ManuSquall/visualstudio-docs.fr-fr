---
title: IDiaSymbol::get_hasNestedTypes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d06648c884a4406c6a5d28b2b33a7cbfd4f6d24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987464"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Récupère un tableau de valeurs d’identificateur de type spécifique au compilateur pour ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cTypeIds`  
 [in] Taille de la mémoire tampon devant contenir les données.  
  
 `pcTypeIds`  
 [out] Retourne le nombre de `typeIds` écrit, ou, si `typeIds` est `NULL`, puis le nombre total d’identificateurs de type disponibles.  
  
 `typeIds[]`  
 [out] Un tableau qui doit être remplie avec les identificateurs de type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)