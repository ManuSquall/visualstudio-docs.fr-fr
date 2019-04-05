---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ce816e20e59d407f9b3cd84e3dffa703d84a324
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952184"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles pour ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszUrlToSymbols`  
 [in] Le chemin d’accès dans le magasin de symboles.  
  
 `pbstrDebugMessage`  
 [out] Retourne un message d’information, par exemple, un message état ou d’erreur qui s’affiche à droite du nom du module dans la fenêtre Modules.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Un moteur de débogage doit toujours retourner `E_FAIL`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est plus pris en charge. Implémentez le [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) méthode à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
