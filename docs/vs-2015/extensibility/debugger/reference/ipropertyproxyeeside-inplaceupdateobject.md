---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953320"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Met à jour des données de l’objet avec l’objet de données spécifié et retourne un nouvel objet de données représentant les nouvelles données de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet contenant les nouvelles données.  
  
 `dataOut`  
 [out] Retourne un nouvel `IEEDataStorage` objet contenant les données remplacées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode met à jour les données de l’objet. Les données dans la liste retournée [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet n’a pas besoin être le même que les données d’entrant `IEEDataStorage` objet, mais l’objet retourné doit refléter la valeur actuelle de la propriété.  
  
 L’objet de données entrantes n’est pas généralement implémentée par le EE. Toutefois, l’objet retourné par cette méthode est toujours implémentée par EE, ce qui vous permet de l’implémenter EE la `IEEDataStorage` interface sur toute classe est souhaitée.  
  
 Le [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) méthode crée un objet de données basé sur l’objet de données entrantes mais n’affecte pas les données d’origine de la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
