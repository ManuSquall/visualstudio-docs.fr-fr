---
title: IDiaLoadCallback::RestrictSymbolServerAccess | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0860741429599630f99c5e2c7c538eff08ecda2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459426"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Détermine si l’accès est autorisé à un serveur de symboles pour résoudre les symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Aucun code de retour autre que `S_OK` empêche d’utiliser un serveur de symboles pour résoudre les symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)