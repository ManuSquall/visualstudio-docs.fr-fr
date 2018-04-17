---
title: IDiaStackWalkFrame::readMemory | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9874972bd5d6ec72ecd36e32d4487343fa4c231e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lit la mémoire à partir de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
 [in] Parmi les [MemoryTypeEnum (énumération)](../../debugger/debug-interface-access/memorytypeenum.md) des valeurs d’énumération qui spécifie le type de mémoire pour accéder à.  
  
 `va`  
 [in] Emplacement de l’adresse virtuelle dans l’image de la lecture doit commencer.  
  
 `cbData`  
 [in] Taille de la mémoire tampon de données, en octets.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets retournés. Si `data` est `NULL`, puis `pcbData` contient le nombre total d’octets de données disponibles.  
  
 `data`  
 [out] Une mémoire tampon qui doit être remplie avec les données à partir de l’emplacement spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)