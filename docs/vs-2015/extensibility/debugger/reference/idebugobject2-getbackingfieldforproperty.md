---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947616"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le champ ou la variable (le cas échéant) qui peut être sauvegarde de la propriété représentée par cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppObject`  
 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet décrivant le champ de stockage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objet représente une propriété de classe de code managé, autrement dit, une méthode avec une commande get et/ou l’accesseur set. Ces propriétés requièrent généralement une variable pour contenir la valeur manipulée par la propriété. Cette variable est connue en tant que le champ de stockage. S’il n’existe aucun champ de stockage pour l’objet, veillez à retourner une valeur null : certains les appelants ne peuvent pas payer une attention particulière à la valeur de retour mais ressemblera à la place pour voir si une valeur null a été retournée dans `ppObject`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
