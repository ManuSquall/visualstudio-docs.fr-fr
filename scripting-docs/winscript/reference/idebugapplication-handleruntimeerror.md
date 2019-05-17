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
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412433"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Provoque le blocage du thread actuel et envoie une notification de l’erreur à l’IDE de débogueur.  
  
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
 [in] L’erreur s’est produite.  
  
 `pScriptSite`  
 [in] Le site de script du thread.  
  
 `pbra`  
 [out] Action à entreprendre lorsque le débogueur reprend l’application.  
  
 `perra`  
 [out] Action à entreprendre lorsque le débogueur reprend l’application s’il existe une erreur.  
  
 `pfCallOnScriptError`  
 [out] Indicateur qui est `TRUE` si le moteur doit appeler le `IActiveScriptSite::OnScriptError` (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui provoque une erreur d’exécution. Cette méthode provoque le blocage du thread actuel et envoie une notification d’erreur à envoyer à l’IDE de débogueur. Lorsque l’IDE de débogueur reprend l’application, cette méthode est retournée avec l’action à entreprendre.  
  
> [!NOTE]
> Dans l’erreur d’exécution, le moteur de langage peut être appelé par le thread pour effectuer des tâches telles qu’énumérer les frames de pile ou d’évaluer des expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug (Interface)](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)