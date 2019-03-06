---
title: IActiveScriptSite::OnScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344562"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informe l’hôte qu’une erreur d’exécution s’est produite pendant que le moteur a été exécute le script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pase`  
 [in] Adresse de l’objet erreur [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interface. Un hôte peut utiliser cette interface pour obtenir des informations sur l’erreur d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si l’erreur a été gérée correctement ou OLE défini le code d’erreur dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)