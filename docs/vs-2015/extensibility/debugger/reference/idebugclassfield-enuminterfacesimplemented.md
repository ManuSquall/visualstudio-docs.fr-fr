---
title: 'IDebugClassField :: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45cdc4ea3d1dad911179ce7b2a4926248ee921fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191013"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour les interfaces implémentées par cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des interfaces implémentées. Retourne une valeur null s’il n’y a pas d’interface.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ou retourne S_FALSE si aucune interface n’est implémentée sur cette classe. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément de l’énumération est un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une interface. Notez que [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] le code non managé n’utilise pas les interfaces comme une entité discrète, de sorte que cette méthode retourne toujours une valeur null pour le code non managé [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
