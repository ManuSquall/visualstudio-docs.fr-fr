---
title: IDiaStackWalkHelper::readMemory | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14a8e435dddaf0d6fb3908a1ccb6233f08ccd28b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468500"
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