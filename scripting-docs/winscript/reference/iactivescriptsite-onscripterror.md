---
title: 'IActiveScriptSite :: OnScriptError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570274"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informe l’hôte qu’une erreur d’exécution s’est produite lors de l’exécution du script par le moteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pase`  
 dans Adresse de l’interface [IActiveScriptError](../../winscript/reference/iactivescripterror.md) de l’objet d’erreur. Un hôte peut utiliser cette interface pour obtenir des informations sur l’erreur d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si l’erreur a été gérée correctement ou un code d’erreur OLE défini dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)