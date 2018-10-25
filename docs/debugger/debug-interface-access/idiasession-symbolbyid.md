---
title: IDiaSession::symbolById | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ca800c4409c9c3c1b72b625aa8cedac31e5b194
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911629"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Récupère un symbole par son identificateur unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] Identificateur unique.  
  
 `ppSymbol`  
 [out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) de récupérer l’objet qui représente le symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’identificateur spécifié est une valeur unique utilisée en interne par le SDK DIA pour rendre tous les symboles unique.  
  
 Cette méthode peut être utilisée, par exemple, pour récupérer le symbole représentant le type d’un autre symbole (voir l’exemple).  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le type d’un autre symbole. Cet exemple montre comment utiliser le `symbolById` méthode dans la session. Une approche plus simple consiste à appeler le [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) méthode pour récupérer le symbole de type directement.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)