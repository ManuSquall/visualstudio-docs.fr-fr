---
title: 'IJsDebugDataTarget :: WriteMemory,, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572417"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory, méthode
Lit la mémoire du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 dans Adresse de base à partir de laquelle écrire la mémoire du processus cible.  
  
 `pMemory`  
 dans Données à écrire dans l’espace d’adressage du processus spécifié.  
  
 `size`  
 dans Nombre d’octets à écrire dans le processus.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Avant le transfert de données, le système vérifie que toutes les données de l’adresse de base et la mémoire de la taille spécifiée sont accessibles pour l’accès en écriture, et si elles ne sont pas accessibles, la fonction génère une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)