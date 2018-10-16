---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9e6093f8abcb73ac98b523906d8e6afe2cfda9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289666"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour les champs du conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Une combinaison de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que vous sélectionnez les champs à énumérer. Types de champ peuvent décrire des types de stockage, telles que la classe ou aux informations de primitives ou spécifiques, comme local, paramètre ou pointeur « this ».  
  
 `dwModifiersFilter`  
 [in] Une combinaison de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que vous sélectionnez les champs à énumérer. Modificateurs de champ peuvent être des autorisations d’accès, tels que public ou privé ou des informations de stockage, comme virtuelle, statique ou finale.  
  
 `pszNameFilter`  
 [in] Le nom du champ à énumérer. Cela peut être une valeur null si tous les champs doivent être retournées.  
  
 `nameMatch`  
 [in] Une valeur comprise entre le [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) énumération qui détermine si la recherche respecte la casse ou non.  
  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des champs. Retourne une valeur null si aucun champ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou S_FALSE si aucun champ. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le `dwKindFilter`, `dwModifiersFilter`, et `pszNameFilter` paramètres peuvent être combinés, par exemple, pour sélectionner toutes les méthodes virtuelles publics nommés « MyMethod ».  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)

