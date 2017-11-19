---
title: IDebugProgramEngines2::EnumPossibleEngines | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1cf3eead4b268dbbca5ad4333adcc647522b051
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retourne les GUID de tous les moteurs de débogage possible (DE) qui peuvent déboguer ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celtBuffer`  
 [in] Le nombre de GUID DE à retourner. Il spécifie également la taille maximale de la `rgguidEngines` tableau.  
  
 `rgguidEngines`  
 [dans, out] Un tableau de GUID DE doit être renseigné.  
  
 `pceltEngines`  
 [out] Retourne le nombre réel de GUID DE qui sont retournées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne (C++) `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [c#] 0x8007007A si la mémoire tampon n’est pas assez grande.  
  
## <a name="remarks"></a>Remarques  
 Afin de déterminer le nombre de moteurs est, appelez cette méthode une fois avec le `celtBuffer` paramètre la valeur 0 et le `rgguidEngines` paramètre défini sur une valeur null. Cela retourne `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A pour c#) et le `pceltEngines` paramètre retourne la taille nécessaire de la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)