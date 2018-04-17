---
title: IDiaSymbol::findChildrenExByAddr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c880d4b51b484f53b0098c0606fa4a11904eb3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Récupère les enfants du symbole valides à une adresse spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
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
  
 `address`  
 [in] L’adresse du symbole.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) de récupérer l’objet qui contient une liste des symboles enfants.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les symboles locaux qui sont retournées incluent des informations de plage dynamique.  
  
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