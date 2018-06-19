---
title: IActiveScriptAuthor::GetLanguageFlags | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645539"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Retourne des informations de langue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pgrfasa`  
 [out] Les indicateurs qui contiennent des informations de langue. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0 x 0001|Le langage préfère la création du Gestionnaire d’événements script par le moteur au lieu de l’application de création de script.|  
|fasaSupportInternalHandler|0 x 0002|Le langage prend en charge les gestionnaires d’événements de script créées par le moteur de création de script.|  
|fasaCaseSensitive|0 x 0004|Le langage de script respecte la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Si le moteur de création de script gère des gestionnaires d’événements, votre application doit appeler `CreateChildHandler` d’un `IScriptEntry` objet. Cette opération crée un `IScriptScriptlet` objet qui correspond au gestionnaire d’événements. Le moteur ajoute également un gestionnaire d’événements à l’écriture de script. Le Gestionnaire d’événements est une fonction vide qui contient les informations de signature spécifié.  
  
 Si votre application gère des gestionnaires d’événements, il doit appeler `CreateChildHandler` d’un `IScriptNode` objet qui représente un scriptlet de gestionnaire d’événements. Cette opération crée un `IScriptScriptlet` objet qui est associé avec le scriptlet de gestionnaire d’événements. L’application doit également ajouter une fonction vide en tant qu’événement gestionnaire vers une nouvelle ou existante `IScriptEntry` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)