---
title: 'IMachineDebugManagerCookie :: EnumApplications | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e01af108e2e417976a61038d7ed3952cb33742c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573903"
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Retourne un énumérateur de la liste actuelle des applications en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppeda`  
 à Énumérateur contenant la liste actuelle des applications en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un énumérateur de la liste actuelle des applications en cours d’exécution. L’IDE du débogueur utilise cette méthode pour afficher et attacher des applications à des fins de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)