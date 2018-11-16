---
title: IDiaEnumSymbols::Next | Microsoft Docs
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
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fcb55a6d6dab2f6c8646909c62fff6d3ec002b2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767467"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un nombre spécifié de caractères de la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,  
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de symboles dans l’énumérateur à récupérer.  
  
 rgelt  
 [out] Un tableau qui doit être rempli avec le [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objets qui représentent les symboles de votre choisis.  
  
 pceltFetched  
 [out] Retourne le nombre de symboles dans l’énumérateur extraite.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’existe plus aucun symbole. Sinon, retourne un code d'erreur.  
  
## <a name="example"></a>Exemple  
  
```cpp#  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



