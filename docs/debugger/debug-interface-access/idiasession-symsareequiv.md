---
title: IDiaSession::symsAreEquiv | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 776e3868e8529657fb77cc9fac1d42eb04cdd722
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Vérifie si deux symboles sont équivalents.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `symbolA`  
 [in] La première [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet utilisé dans la comparaison.  
  
 `symbolB`  
 [in] La seconde `IDiaSymbol` objet utilisé dans la comparaison.  
  
## <a name="return-value"></a>Valeur de retour  
 Si les symboles sont équivalentes, retourne `S_OK`; sinon, retourne `S_FALSE`, les symboles ne sont pas équivalents. Sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)