---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adddb92adc7f62d51efd5c87ad40c1f47de41ae7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040721"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Détermine si une interface spécifique est définie dans la classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszInterfaceName`  
 [in] Chaîne contenant le nom de l’interface à rechercher.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK, retourne S_FALSE si l’interface n’existe pas ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En effet, cette méthode obtient une énumération de toutes les interfaces et recherche dans la liste pour une interface correspondant.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)