---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150164"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lit la mémoire à partir de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 dans L’une des valeurs d’énumération d' [énumération MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) qui spécifie le type de mémoire à laquelle accéder.  
  
 `va`  
 dans Emplacement d’adresse virtuelle dans l’image pour commencer la lecture.  
  
 `cbData`  
 dans Taille de la mémoire tampon de données, en octets.  
  
 `pcbData`  
 à Retourne le nombre d’octets retournés. Si `data` a `NULL` la valeur, `pcbData` contient le nombre total d’octets de données disponibles.  
  
 `data`  
 à Mémoire tampon qui doit être remplie avec des données provenant de l’emplacement spécifié.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
