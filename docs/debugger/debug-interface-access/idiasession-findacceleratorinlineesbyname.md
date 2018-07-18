---
title: IDiaSession::findAcceleratorInlineesByName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9e95193b361dcfe0935d209bf1fc3687914e1c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468760"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Retourne une énumération de symboles de cadres correspondant au nom de la fonction inline spécifiés.  
  
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
 [in] Les options de recherche de nom à utiliser lors de la recherche d’inline frames qui correspondent aux `name`. Pour plus d’informations, consultez [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette fonction recherche les éléments inline que dans les fonctions de stub d’accélérateur. Il ignore les enregistrements de procédure C++ natifs.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)