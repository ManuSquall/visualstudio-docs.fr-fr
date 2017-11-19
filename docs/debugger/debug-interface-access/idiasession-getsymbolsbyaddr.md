---
title: IDiaSession::getSymbolsByAddr | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::getSymbolsByAddr method
ms.assetid: eafcc757-b488-487d-a063-ad3703ff42e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3467ad1129ea7f64444bfff0c8762c117cea1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessiongetsymbolsbyaddr"></a>IDiaSession::getSymbolsByAddr
Récupère un énumérateur qui recherche les symboles dans l’ordre de leurs adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT getSymbolsByAddr(   
   IDiaEnumSymbolsByAddr** ppEnumbyAddr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnumbyAddr`  
 [out] Retourne un [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) objet. Cette interface permet de rechercher des symboles dans le magasin de symboles à l’emplacement de mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)