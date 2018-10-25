---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c38d1f834e9eb7deae62701a17c0d24ea21937c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915332"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Appelé par un gestionnaire d’événements pour récupérer les résultats sur un processus de chargement de symboles.  
  
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
 [in, out] Retourne une chaîne contenant les messages d’erreur à partir du module. S’il n’existe aucune erreur, cette chaîne contient uniquement le nom du module, mais il n’est jamais vide.  
  
> [!NOTE]
>  (C++) `pbstrDebugMessage` ne peut pas être `NULL` et doit être libérée avec `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Une combinaison d’indicateurs de la [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) énumération qui indique si tous les symboles ont été chargés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Quand un gestionnaire reçoit la [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) événement après une tentative est effectuée pour charger les symboles de débogage pour un module, le gestionnaire peut appeler cette méthode pour déterminer les résultats de cette charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)