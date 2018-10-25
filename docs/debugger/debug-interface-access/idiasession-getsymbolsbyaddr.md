---
title: IDiaSession::getSymbolsByAddr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getSymbolsByAddr method
ms.assetid: eafcc757-b488-487d-a063-ad3703ff42e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c266839334184dc40af6424147dcb8b59420ee5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913993"
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
 [out] Retourne un [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) objet. Cette interface permet de rechercher des symboles dans le magasin de symboles par emplacement de mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)