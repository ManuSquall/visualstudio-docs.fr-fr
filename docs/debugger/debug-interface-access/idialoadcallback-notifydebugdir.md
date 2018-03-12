---
title: IDiaLoadCallback::NotifyDebugDir | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fad37acafae21c6e82839979360f4ed9574aef1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Appelé lorsqu’un répertoire de débogage a été trouvé dans le fichier .exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fExecutable`  
 [in] `TRUE` si le répertoire de débogage est en lecture à partir d’un fichier exécutable (plutôt qu’un fichier .dbg).  
  
 `cbData`  
 [in] Nombre d’octets de données dans le répertoire de débogage.  
  
 `data[]`  
 [in] Tableau qui contient le répertoire de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le code de retour est généralement ignoré.  
  
## <a name="remarks"></a>Notes  
 Le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode appelle ce rappel lorsqu’il détecte un répertoire de débogage lors du traitement du fichier exécutable.  
  
 Cette méthode supprime la nécessité pour le client rétroconcevoir le fichier exécutable et/ou de débogage pour prendre en charge les informations de débogage autre que celle trouvée dans le fichier .pdb. Avec ces données, le client peut reconnaître le type d’informations de débogage disponibles et si elle se trouve dans le fichier exécutable ou le fichier .dbg.  
  
 La plupart des clients n’aurez pas ce rappel car le `IDiaDataSource::loadDataForExe` méthode ouvre en toute transparence les fichiers .pdb et .dbg lorsque cela est nécessaire pour traiter des symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)