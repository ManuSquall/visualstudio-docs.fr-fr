---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c57072d4b8707136f0ccd2a759bc3d393720efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150436"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un fichier source par identificateur de fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `uniqueId`  
 dans Spécifie l’identificateur du fichier source.  
  
 `ppResult`  
 à Retourne un objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source récupéré.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 L’identificateur du fichier source est une valeur unique utilisée en interne par le kit de développement logiciel (SDK) DIA pour rendre tous les fichiers sources uniques. Cette méthode est généralement utilisée en interne dans le kit de développement logiciel (SDK) DIA.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession :: findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
