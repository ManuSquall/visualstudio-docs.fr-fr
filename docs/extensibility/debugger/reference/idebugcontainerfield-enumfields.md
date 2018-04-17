---
title: IDebugContainerField::EnumFields | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0af939253de7b592e7c0ec35be9ea2b9bbff2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crée un énumérateur pour les champs du conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwKindFilter`  
 [in] Une combinaison de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que vous sélectionnez les champs à énumérer. Types de champ peuvent décrire des types de stockage, telles que la classe ou informations primitives ou spécifiques, tels que local, le paramètre ou le pointeur « this ».  
  
 `dwModifiersFilter`  
 [in] Une combinaison de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que vous sélectionnez les champs à énumérer. Modificateurs de champ peuvent être des autorisations d’accès, tel que public ou privé ou les informations de stockage, telles que virtuelle, statique ou final.  
  
 `pszNameFilter`  
 [in] Le nom du champ à énumérer. Cela peut être une valeur null si tous les champs doivent être retournées.  
  
 `nameMatch`  
 [in] Une valeur à partir de la [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) énumération qui détermine si la recherche respecte la casse ou non.  
  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des champs. Retourne une valeur null si aucun champ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou S_FALSE si aucun champ. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le `dwKindFilter`, `dwModifiersFilter`, et `pszNameFilter` paramètres peuvent être combinés, par exemple, pour sélectionner toutes les méthodes publiques virtuels nommés « MyMethod ».  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)