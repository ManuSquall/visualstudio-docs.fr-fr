---
title: IDebugApplication::HandleRuntimeError | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Provoque le blocage du thread actuel et envoie une notification de l’erreur à l’IDE de débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pErrorDebug`  
 [in] L’erreur s’est produite.  
  
 `pScriptSite`  
 [in] Le site de script du thread.  
  
 `pbra`  
 [out] Action à entreprendre lorsque le débogueur sort de l’application.  
  
 `perra`  
 [out] Action à entreprendre lorsque le débogueur sort de l’application s’il existe une erreur.  
  
 `pfCallOnScriptError`  
 [out] Indicateur qui est `TRUE` si le moteur doit appeler le `IActiveScriptSite::OnScriptError` (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui provoque une erreur d’exécution. Cette méthode provoque le blocage du thread actuel et envoie une notification d’erreur à envoyer au débogueur IDE. Lorsque le débogueur IDE reprend l’application, cette méthode retourne l’action à entreprendre.  
  
> [!NOTE]
>  Lors de l’erreur d’exécution, le moteur de langage peut être appelé par le thread pour effectuer des tâches telles qu’énumérer les frames de pile ou d’évaluer des expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug (Interface)](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)