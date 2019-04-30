---
title: Méthode IJsDebugProcess::CreateBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557970"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint, méthode
Définit le point d’arrêt à la position du document spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `documentId`  
 [in] Pointeur vers IDebugDocumentText.  
  
 `characterOffset`  
 [in] Offset de caractère à partir du début du fichier.  
  
 `characterCount`  
 [in] Longueur du texte du document dans lequel le point d’arrêt doit être inséré.  
  
 `isEnabled`  
 [in] Spécifie si le point d’arrêt est activé.  
  
 `ppDebugBreakPoint`  
 [out] Objet représentant le point d’arrêt a été créé.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)