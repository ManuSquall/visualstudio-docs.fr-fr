---
title: 'IActiveScriptSiteDebug32 :: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572197"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Retourne l’objet d’application de débogage associé à ce site de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppda`  
 à Pointeur vers l’objet d’application de débogage associé au site de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’hôte ne prend pas directement en charge le débogage.|  
  
## <a name="remarks"></a>Notes  
 La méthode `GetApplication` permet à un hôte intelligent de définir l’objet d’application auquel chaque script appartient. Les moteurs de script doivent tenter d’appeler cette méthode pour récupérer leur application conteneur et se référer à `IProcessDebugManager::GetDefaultApplication` en cas d’échec.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)