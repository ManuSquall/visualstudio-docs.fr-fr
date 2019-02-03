---
title: IDiaEnumSymbolsByAddr::symbolByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62a7955c0b8bd6971aa51ff86de16b8dae6b281b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042879"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Positionne l’énumérateur en effectuant une recherche par adresse virtuelle relative (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT symbolByRVA (   
   DWORD**      relativeVirtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 relativeVirtualAddress  
 [in] Adresse relative au démarrage de l’image.  
  
 ppsymbol  
 [out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le symbole trouvé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si le symbole est introuvable. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)