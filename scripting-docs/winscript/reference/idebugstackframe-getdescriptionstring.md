---
title: 'IDebugStackFrame :: GetDescriptionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb29574d240a02073721046cec65bdf483b3eb0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576744"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Retourne une description textuelle courte ou longue du frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fLong`  
 dans , Où `TRUE` retourne une description longue et `FALSE` retourne une brève description.  
  
 `pbstrDescription`  
 à Description du frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 En général, si `fLong` est `FALSE`, cette méthode fournit uniquement le nom de la fonction associée au frame de pile. Lorsque `fLong` est `TRUE`, cette méthode peut également fournir les paramètres de fonction et d’autres informations pertinentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)