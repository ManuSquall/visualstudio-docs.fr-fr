---
title: 'IActiveScriptAuthor :: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576205"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Retourne des informations sur la langue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pgrfasa`  
 à Indicateurs qui contiennent les informations de langue. Peut être une combinaison des valeurs suivantes :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Le langage préfère la création du gestionnaire d’événements de script par le moteur de création de script au lieu de l’application.|  
|fasaSupportInternalHandler|0x0002|Le langage prend en charge les gestionnaires d’événements de script créés par le moteur de création de script.|  
|fasaCaseSensitive|0x0004|Le langage de script respecte la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Si le moteur de création de script gère les gestionnaires d’événements, votre application doit appeler `CreateChildHandler` à partir d’un objet `IScriptEntry`. Cela crée un objet `IScriptScriptlet` qui correspond au gestionnaire d’événements. Le moteur ajoute également un gestionnaire d’événements à l’entrée de script. Le gestionnaire d’événements est une fonction vide qui contient les informations de signature spécifiées.  
  
 Si votre application gère des gestionnaires d’événements, elle doit appeler `CreateChildHandler` à partir d’un objet `IScriptNode` qui représente un scriptlet de gestionnaire d’événements. Cela crée un objet `IScriptScriptlet` associé au scriptlet du gestionnaire d’événements. L’application doit également ajouter une fonction vide en tant que gestionnaire d’événements à un objet `IScriptEntry` nouveau ou existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)