---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1367d444a498c1c066cbdfb38ee4f2cec12c9a2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915319"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Appelé lorsqu’un fichier .pdb de candidat est ouvert.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdbPath`  
 [in] Le chemin d’accès complet du fichier .pdb.  
  
 `resultCode`  
 [in] Code qui indique la réussite (`S_OK`) ou l’échec de la charge appliquée à ce fichier.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le code de retour est généralement ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)