---
title: IDiaSession::symbolById | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70139b7bf3286e7c4527bd71cf78b4ba86aeac1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 L’identificateur spécifié est une valeur unique utilisée en interne par le SDK DIA pour que tous les symboles unique.  
  
 Cette méthode peut être utilisée, par exemple, pour récupérer le symbole représentant le type d’un autre symbole (voir l’exemple).  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le type d’un autre symbole. Cet exemple montre comment utiliser la `symbolById` méthode dans la session. Une approche plus simple consiste à appeler la [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) méthode pour récupérer le symbole de type directement.  
  
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