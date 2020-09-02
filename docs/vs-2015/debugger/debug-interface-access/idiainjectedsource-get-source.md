---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 856d0111e65b51b798dfe44a324c58c4db5457fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192421"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les octets de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 dans Nombre d’octets qui représente la taille de la mémoire tampon de données.  
  
 `pcbData`  
 à Retourne le nombre d’octets qui représente les octets retournés. Si `data` est `NULL` , `pcbData` est le nombre total d’octets de données disponibles.  
  
 `data[]`  
 à Mémoire tampon qui doit être remplie avec les octets sources.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
