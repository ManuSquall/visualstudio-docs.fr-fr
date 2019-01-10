---
title: IActiveScriptError::GetSourceLineText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3186ec3edcdd0c66f06f7b769eff31e8b050c428
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091674"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Récupère la ligne dans le fichier source où une erreur s’est produite pendant l’exécution d’un moteur de script un script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Paramètre  
 `pbstrSourceLine`  
 [out] Adresse d’une mémoire tampon qui reçoit la ligne de code source dans lequel l’erreur s’est produite.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si la ligne dans le fichier source n’a pas été récupérée.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)