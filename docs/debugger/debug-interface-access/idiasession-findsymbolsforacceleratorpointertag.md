---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f67263b385c184b0182716469f110c87bcebb50
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Retourne une énumération de symboles de la valeur de la balise spécifiée correspond à la variable dans la fonction de stub accélérateur parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] IDiaSymbol qui correspond à la fonction de stub accélérateur à rechercher.  
  
 `tagValue`  
 [in] La valeur de balise de pointeur.  
  
 `ppResult`  
 [out] Un pointeur vers un `IDiaEnumSymbols` pointeur d’interface qui est initialisé avec le résultat.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)