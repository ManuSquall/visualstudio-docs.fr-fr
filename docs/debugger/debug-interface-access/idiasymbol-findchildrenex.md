---
title: IDiaSymbol::findChildrenEx | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 184c4ff637d281ba8bca15c16d3112dff4b6f96f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Récupère les enfants du symbole. Les symboles locaux qui sont retournées incluent des informations de plage dynamique, si le programme est compilé avec l’optimisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `symtag`  
 [in] Spécifie les balises symbol des enfants à récupérer, tel que défini dans le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md). La valeur `SymTagNull` pour tous les enfants doivent être récupérés.  
  
 `name`  
 [in] Spécifie le nom de l’enfant doit être récupéré. La valeur `NULL` pour tous les enfants doivent être récupérés.  
  
 `compareFlags`  
 [in] Spécifie les options de comparaison à appliquer à la correspondance de noms. Les valeurs à partir de la [namesearchoptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) énumération peut être utilisée seul ou combiné.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) de récupérer l’objet qui contient une liste des symboles enfants.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est la version étendue du [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md)