---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c843291aa87671d11293b72795222af9e96b03d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904425"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lit un bloc de données à partir de l’image de l’exécutable en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 [in] Une valeur comprise entre le [MemoryTypeEnum (énumération)](../../debugger/debug-interface-access/memorytypeenum.md) énumération spécifiant le type de mémoire à lire.  
  
 Évaluation des vulnérabilités  
 [in] Adresse virtuelle dans l’image à partir duquel commencer la lecture.  
  
 `cbData`  
 [in] La taille du tampon de données en octets.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets réellement lus. Si `pbData` est `NULL`, puis il s’agit du nombre total d’octets de données disponibles.  
  
 `pbData`  
 [in, out] Une mémoire tampon est remplie avec la mémoire à lire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum, énumération](../../debugger/debug-interface-access/memorytypeenum.md)



