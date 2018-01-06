---
title: IDebugModule2::ReloadSymbols_Deprecated | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2::ReloadSymbols
helpviewer_keywords: IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 609769b44dc4d876a1a2d13d0e126927ee47a739
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles de ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] Le chemin d’accès pour le magasin de symboles.  
  
 `pbstrDebugMessage`  
 [out] Retourne un message d’information, par exemple un message d’état ou d’erreur, qui s’affiche à droite du nom du module dans la fenêtre Modules.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Un moteur de débogage doit toujours renvoyer `E_FAIL`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est plus pris en charge. Implémentez la [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) méthode à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)