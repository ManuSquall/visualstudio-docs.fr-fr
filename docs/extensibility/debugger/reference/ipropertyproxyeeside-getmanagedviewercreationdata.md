---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47ae1c724542d628e7f3c047efd8ed2da1f6f1f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Récupère les informations sur la visionneuse pour ce type de propriété afin d’instancier ce visualiseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `assemName`  
 [out] Retourne le nom de l’assembly contenant cet objet.  
  
 `assemBytes`  
 [out] Retourne un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet contenant les octets de l’assembly de cet objet (Ceci est une valeur null si aucun octet n’est disponible).  
  
 `assemPdb`  
 [out] Retourne un `IEEDataStorage` objet contenant le symbole de stocker les informations de cet objet (Ceci est une valeur null si aucun magasin de symboles n’est disponible).  
  
 `className`  
 [out] Retourne le nom de la classe qui contient cet objet.  
  
 `alr`  
 [out] Retourne une valeur de la [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) énumération indiquant l’emplacement de l’assembly.  
  
 `replacementOk`  
 [out] Retourne zéro (`TRUE`) si la valeur de cet objet peut être modifiée ; zéro (`FALSE`) si l’objet est en lecture seule.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée par les visualiseurs de type pour instancier une visionneuse managée.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)