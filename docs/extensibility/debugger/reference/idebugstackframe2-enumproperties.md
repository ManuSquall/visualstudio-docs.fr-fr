---
title: IDebugStackFrame2::EnumProperties | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5359698b2ae148abd5fc38da346ebcd5c456634c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crée un énumérateur pour les propriétés associées avec le frame de pile, tels que des variables locales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Une combinaison d’indicateurs à partir de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui spécifie les champs dans la liste énumérée [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures doivent être renseignés.  
  
 `nRadix`  
 [in] La base à utiliser dans toutes les informations numériques de mise en forme.  
  
 `refiid`  
 [in] Un GUID d’un filtre pour sélectionner les [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures sont énumérées, tel que `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Temps maximal, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `pcelt`  
 [out] Retourne le nombre de propriétés énumérées. Cela revient à appeler la [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) (méthode).  
  
 `ppEnum`  
 [out] Retourne un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet contenant la liste des propriétés souhaitées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Étant donné que cette méthode permet de toutes les propriétés sélectionnées être récupérés avec un seul appel, il est plus rapide que l’appel de manière séquentielle les [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) et [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
