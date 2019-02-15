---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7814043b28e80e7c87543b94ef95e958434ddf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031246"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Retourne une énumération de symboles pour les frames en ligne correspondant au nom de fonction inline spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 [in] Le nom de fonction inline à rechercher.  
  
 `option`  
 [in] Les options de recherche de nom à utiliser lors de la recherche d’inline des frames qui correspondent aux `name`. Pour plus d’informations, consultez [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction recherche les éléments inline uniquement dans les fonctions de stub d’accélérateur. Il ignore les enregistrements de procédure C++ natifs.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)