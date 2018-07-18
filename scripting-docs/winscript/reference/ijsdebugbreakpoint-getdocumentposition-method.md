---
title: Ijsdebugbreakpoint::getdocumentposition, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3c33751b0173626814f042fdc54a7d496b644573
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727609"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition, méthode
Retourne la position de l’instruction où le point d’arrêt a été lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentId`  
 [out] ID unique d’un document source (pointeur vers le IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] L’offset de base zéro du caractère à partir du début du script.  
  
 `pStatementCharCount`  
 [out] La longueur de l’instruction actuelle, qui commence à * pCharacterOffset, en caractères.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)