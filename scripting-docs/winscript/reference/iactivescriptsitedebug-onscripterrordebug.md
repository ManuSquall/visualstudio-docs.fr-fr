---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5680d22ffa5ec648afaced5e98f651e35758f929
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092116"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permet à un hôte intelligent déterminer comment gérer les erreurs d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pErrorDebug`  
 [in] L’erreur d’exécution s’est produite  
  
 `pfEnterDebugger`  
 [out] Indicateur précisant s’il faut passer l’erreur au débogueur d’effectuer un débogage JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Indicateur qui spécifie s’il faut appeler `IActiveScriptSite::OnScriptError` lorsque l’utilisateur décide de continuer sans le débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles incluent, mais ne sont pas limités à la valeur dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un hôte intelligent peut utiliser cette méthode pour déterminer comment gérer les erreurs d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)