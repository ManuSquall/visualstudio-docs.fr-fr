---
title: IDiaLoadCallback::NotifyOpenDBG | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8454a795200c9e0aea850a2a75a25403d5c0c2c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Appelé lorsqu’un fichier .dbg de candidat a été ouvert.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dbgPath`  
 [in] Le chemin d’accès complet du fichier .dbg.  
  
 `resultCode`  
 [in] Code qui indique la réussite (`S_OK`) ou l’échec de la charge, tel qu’appliqué à ce fichier.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le code de retour est généralement ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)