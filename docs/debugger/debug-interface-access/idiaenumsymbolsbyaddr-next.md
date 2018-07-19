---
title: IDiaEnumSymbolsByAddr::Next | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ffede509bdeb45ad1ca19b368d10928568f4fff8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462511"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Récupère les symboles suivants dans l’ordre par adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de symboles dans l’énumérateur doit être récupéré.  
  
 rgelt  
 [out] Un tableau qui doit être remplie avec les [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet représentant les symboles de votre choisis.  
  
 pceltFetched  
 [out] Retourne le nombre de symboles dans l’énumérateur d’extraction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus aucun symbole. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode met à jour la position de l’énumérateur par le nombre d’éléments extraits.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)