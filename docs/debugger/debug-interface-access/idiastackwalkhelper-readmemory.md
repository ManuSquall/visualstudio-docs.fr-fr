---
title: IDiaStackWalkHelper::readMemory | Documents Microsoft
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
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f528d377dc75f940a10f1a38ae04cc3eb71cdd22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lit un bloc de données à partir de l’image de l’exécutable dans la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
 [in] Une valeur à partir de la [memorytypeenum, énumération](../../debugger/debug-interface-access/memorytypeenum.md) énumération spécifiant le type de mémoire à lire.  
  
 va  
 [in] Adresse virtuelle dans l’image à partir duquel commencer la lecture.  
  
 `cbData`  
 [in] La taille du tampon de données en octets.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets réellement lus. Si `pbData` est `NULL`, il s’agit du nombre total d’octets de données disponibles.  
  
 `pbData`  
 [dans, out] Une mémoire tampon est remplie avec la mémoire à lire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum (énumération)](../../debugger/debug-interface-access/memorytypeenum.md)