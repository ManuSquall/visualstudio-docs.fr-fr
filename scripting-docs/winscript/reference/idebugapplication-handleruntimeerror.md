---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574330"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Provoque le blocage du thread actuel et envoie une notification de l’erreur à l’IDE du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 dans Erreur qui s’est produite.  
  
 `pScriptSite`  
 dans Site de script du thread.  
  
 `pbra`  
 à Action à entreprendre lorsque le débogueur reprend l’application.  
  
 `perra`  
 à Action à entreprendre lorsque le débogueur reprend l’application en cas d’erreur.  
  
 `pfCallOnScriptError`  
 à Indicateur qui est `TRUE` si le moteur doit appeler la méthode `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui provoque une erreur au moment de l’exécution. Cette méthode provoque le blocage du thread actuel et envoie une notification d’erreur à envoyer à l’IDE du débogueur. Lorsque l’IDE du débogueur reprend l’application, cette méthode retourne avec l’action à effectuer.  
  
> [!NOTE]
> Dans l’erreur d’exécution, le moteur de langage peut être appelé par le thread pour effectuer des tâches telles que l’énumération des frames de pile ou l’évaluation des expressions.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
   de l' [interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
   de l' [énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)