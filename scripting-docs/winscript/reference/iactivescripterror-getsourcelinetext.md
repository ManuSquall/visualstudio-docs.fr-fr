---
title: 'IActiveScriptError :: GetSourceLineText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ded57f97ec40167bac34bf0f288c2e3d15a5c4b7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576913"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Récupère la ligne dans le fichier source où une erreur s’est produite lors de l’exécution d’un script par un moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Paramètre  
 `pbstrSourceLine`  
 à Adresse d’une mémoire tampon qui reçoit la ligne de code source dans laquelle l’erreur s’est produite.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si la ligne du fichier source n’a pas été récupérée.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)