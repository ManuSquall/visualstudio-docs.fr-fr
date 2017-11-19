---
title: IDiaInjectedSource::get_source | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910b96d4114617957907ff1cd4eee4609ebaa250
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Récupère les octets de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 [in] Le nombre d’octets qui représente la taille du tampon de données.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets qui représente les octets retourné. Si `data` est `NULL`, puis `pcbData` le nombre total d’octets de données n’est disponible.  
  
 `data[]`  
 [out] Une mémoire tampon qui doit être remplie avec les octets de la source.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)