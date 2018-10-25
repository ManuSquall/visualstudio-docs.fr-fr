---
title: IDiaEnumSegments::Next | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c9966555c673904a423de1b215e438b5db15479
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951026"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de segments dans l’énumérateur à récupérer.  
  
 rgelt  
 [out] Un tableau qui doit être renseigné avec le texte souhaité [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objets qui représentent les segments.  
  
 pceltFetched  
 [out] Retourne le nombre de segments dans l’énumérateur extraite.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si aucun segment plus. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)