---
title: IActiveScriptSite::OnScriptError | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informe l’hôte qu’une erreur d’exécution s’est produite pendant que le moteur était en cours d’exécution du script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pase`  
 [in] Adresse de l’objet d’erreur [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interface. Un hôte peut utiliser cette interface pour obtenir des informations sur l’erreur d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si l’erreur a été gérée correctement ou OLE défini le code d’erreur dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)