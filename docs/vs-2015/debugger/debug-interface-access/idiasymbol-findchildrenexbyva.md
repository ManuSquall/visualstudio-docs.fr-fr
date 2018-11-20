---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89382450b388524a5b08e04fa879e97cb5f26258
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750240"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les enfants du symbole sont valides à une adresse virtuelle spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `symtag`  
 [in] Spécifie les balises de symbole des enfants à récupérer, tel que défini dans le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md). La valeur `SymTagNull` pour tous les enfants doivent être récupérées.  
  
 `name`  
 [in] Spécifie le nom des enfants à récupérer. La valeur `NULL` pour tous les enfants doivent être récupérées.  
  
 `compareFlags`  
 [in] Spécifie les options de comparaison à appliquer à la correspondance de noms. Les valeurs de la [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md) énumération peut être utilisée seul ou combiné.  
  
 `address`  
 [in] Spécifie l’adresse virtuelle.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) de récupérer l’objet qui contient une liste des symboles enfants.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les symboles locaux qui sont retournées incluent des informations de plage dynamique.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)



