---
title: IDiaSymbol::get_relativeVirtualAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_relativeVirtualAddress method
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01f2e8771b43ac71e84b1b7afb595b266f57767
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetrelativevirtualaddress"></a>IDiaSymbol::get_relativeVirtualAddress
Récupère l’adresse virtuelle relative (RVA) de l’emplacement. Quand utiliser le [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsStatic`.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’adresse virtuelle relative de l’emplacement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaSymbol* pSymbol;  
DWORD       rva;  
pSymbol->get_relativeVirtualAddress( &rva );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md)