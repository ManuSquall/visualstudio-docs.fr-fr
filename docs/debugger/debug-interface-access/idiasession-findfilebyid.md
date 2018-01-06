---
title: IDiaSession::findFileById | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 176e6a482212ee0cb6531d558e2b322ce4bec2d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Récupère un fichier source par l’identificateur du fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `uniqueId`  
 [in] Spécifie l’identificateur de fichier source.  
  
 `ppResult`  
 [out] Retourne un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) de récupérer l’objet qui représente le fichier source.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’identificateur du fichier source est une valeur unique utilisée en interne pour le SDK DIA pour que tous les fichiers source unique. Cette méthode est généralement utilisée en interne pour le SDK DIA.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)