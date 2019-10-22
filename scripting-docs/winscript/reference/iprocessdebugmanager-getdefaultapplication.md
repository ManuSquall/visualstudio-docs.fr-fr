---
title: 'IProcessDebugManager :: GetDefaultApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576794"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Retourne un objet d’application par défaut pour le processus en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppda`  
 à Objet d’application de débogage pour cette application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un nouvel objet d’application de débogage et l’ajoute à la liste des applications en cours d’exécution, si nécessaire.  
  
 Les moteurs de langage doivent utiliser l’application spécifiée par la méthode `GetDefaultApplication` s’ils s’exécutent sur un hôte qui ne fournit pas d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)