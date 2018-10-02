---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dde77e3468374d0e82aaaf3135407992171c837
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505302"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IPropertyProxyEESide::InitSourceDataProvider](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider).  
  
Initialise les données source pour cet objet et retourne un objet contenant les données initiales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataOut`  
 [out] Retourne un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode fait le nécessaire pour initialiser un objet afin qu’il peut retourner un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interface sur les données de l’objet. Ainsi, les données de l’objet à afficher et, si autorisée, modifié par un visualiseur de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

