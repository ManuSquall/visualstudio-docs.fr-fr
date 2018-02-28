---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 37a25e762f15a550aa3c4d06c85c64c500065747
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Appelée par un gestionnaire d’événements pour récupérer les résultats sur un processus de chargement de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pModule`  
 [out] Objet IDebugModule3 représentant le module pour lequel les symboles ont été chargés.  
  
 `pbstrDebugMessage`  
 [dans, out] Retourne une chaîne qui contient des messages d’erreur à partir du module. S’il n’existe aucune erreur, cette chaîne contient uniquement le nom de module, mais il n’est jamais vide.  
  
> [!NOTE]
>  (C++) `pbstrDebugMessage` ne peut pas être `NULL` et doit être libérée avec `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Une combinaison d’indicateurs à partir de la [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) énumération qui indique si tous les symboles ont été chargés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un gestionnaire reçoit le [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) événement après une tentative est effectuée pour charger les symboles de débogage pour un module, le gestionnaire peut appeler cette méthode pour déterminer les résultats de cette charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)