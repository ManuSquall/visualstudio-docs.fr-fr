---
title: Méthode IJsDebugProcess::CreateBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 661e584133f4ec3c4e571d157a63844c5b1145b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097563"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)