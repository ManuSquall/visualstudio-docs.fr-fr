---
title: 'IJsDebugBreakPoint :: GetDocumentPosition, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f3bc5aff0b7079e20e2bcd49189153d2ec20d9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577691"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition, méthode
Retourne la position de l’instruction à laquelle le point d’arrêt a été lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentId`  
 à ID unique d’un document source (pointeur vers IDebugDocumentText).  
  
 `pCharacterOffset`  
 à Offset de caractère de base zéro à partir du début du script.  
  
 `pStatementCharCount`  
 à Longueur de l’instruction en cours, qui commence à * pCharacterOffset, en caractères.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)