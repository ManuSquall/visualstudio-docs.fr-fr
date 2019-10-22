---
title: 'IJsDebugProcess :: CreateBreakPoint, méthode | Microsoft Docs'
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
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575090"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint, méthode
Définit le point d’arrêt à la position de document spécifiée.  
  
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
 dans Pointeur vers IDebugDocumentText.  
  
 `characterOffset`  
 dans Offset de caractère à partir du début du fichier.  
  
 `characterCount`  
 dans Longueur du texte du document dans lequel le point d’arrêt doit être inséré.  
  
 `isEnabled`  
 dans Spécifie si le point d’arrêt est activé.  
  
 `ppDebugBreakPoint`  
 à Objet représentant le point d’arrêt qui a été créé.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)