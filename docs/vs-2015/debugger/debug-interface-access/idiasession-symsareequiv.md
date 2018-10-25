---
title: IDiaSession::symsAreEquiv | Microsoft Docs
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
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c27cc4b984b250e70ba44122067df0bbfb4dc86
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885797"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vérifie si deux symboles sont équivalentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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



