---
title: IDiaSymbol::findInlineFramesByAddr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2bbfaa388ad17e688e46b2304bd770cb895d9cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
Récupère une énumération qui permet à un client itérer au sein de tous les cadres inline sur une adresse donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isect`  
 [in] Spécifie le composant de la section de l’adresse.  
  
 `offset`  
 [in] Spécifie le composant de décalage de l’adresse.  
  
 `ppResult`  
 [out] Contient un `IDiaEnumSymbols` objet qui contient la liste d’images qui sont récupérés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)