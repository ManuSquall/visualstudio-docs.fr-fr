---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
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
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b29b6eb411c511612b60faf271d23decd7370c12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503912"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugObject2::GetBackingFieldForProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty).  
  
Obtient le champ ou la variable (le cas échéant) qui peut être sauvegarde de la propriété représentée par cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
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

