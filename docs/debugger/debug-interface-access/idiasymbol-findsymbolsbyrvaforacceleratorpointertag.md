---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f12417323d0553fc6dd9ca33c65c566229454c99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Une valeur correspondante de la balise donnée, cette méthode retourne une énumération de symboles contenus dans cette fonction stub à une adresse virtuelle relative spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `tagValue`  
 [in] La valeur de balise de pointeur pour lesquels figurent les enregistrements de symbole pointee.  
  
 `rva`  
 [in] L’adresse rva est utilisée pour filtrer les symboles qui correspondent à la variable pointee avec la valeur de balise spécifié.  
  
 `ppResult`  
 [out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Appelez cette méthode uniquement sur un `IDiaSymbol` interface qui correspond à une fonction de stub accélérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)