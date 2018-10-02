---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a8c42ddcde84524819f2c8f828fa72c8617d423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495631"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugModule2::ReloadSymbols_Deprecated](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated).  
  
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

