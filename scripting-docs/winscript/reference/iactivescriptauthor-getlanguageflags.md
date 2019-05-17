---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
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
ms.openlocfilehash: d9f1a68db05ac0d909108ce77587ae4b071c9a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935469"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Retourne des informations de langue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pgrfasa`  
 [out] Indicateurs qui contiennent des informations de langue. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Le langage préfère la création du Gestionnaire d’événements script par le moteur plutôt que l’application de création de script.|  
|fasaSupportInternalHandler|0x0002|Le langage prend en charge les gestionnaires d’événements de script créées par le moteur de création de script.|  
|fasaCaseSensitive|0x0004|Le langage de script respecte la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Si le moteur de création de script gère des gestionnaires d’événements, votre application doit appeler `CreateChildHandler` à partir d’un `IScriptEntry` objet. Cette opération crée un `IScriptScriptlet` objet qui correspond au gestionnaire d’événements. Le moteur ajoute également un gestionnaire d’événements à l’écriture de script. Le Gestionnaire d’événements est une fonction vide qui contient les informations de signature spécifié.  
  
 Si votre application gère des gestionnaires d’événements, il doit appeler `CreateChildHandler` à partir d’un `IScriptNode` objet qui représente un scriptlet de gestionnaire d’événements. Cette opération crée un `IScriptScriptlet` objet qui est associé avec le scriptlet de gestionnaire d’événements. L’application doit également ajouter une fonction vide en tant qu’événement gestionnaire vers un nouveau ou existant `IScriptEntry` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)