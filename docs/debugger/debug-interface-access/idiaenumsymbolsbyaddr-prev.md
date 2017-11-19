---
title: IDiaEnumSymbolsByAddr::Prev | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7edaccc32a6557071aa294884348029d2841f8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Récupère les symboles précédentes dans l’ordre par adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de symboles dans l’énumérateur doit être récupéré.  
  
 rgelt  
 [out] Un tableau qui doit être renseigné avec [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) les objets qui représentent les symboles de votre choisis.  
  
 pceltFetched  
 [out] Retourne le nombre de symboles dans l’énumérateur d’extraction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a aucun symbole précédent. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode met à jour la position de l’énumérateur par le nombre d’éléments extraits.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)