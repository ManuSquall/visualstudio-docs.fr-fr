---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57bf8d0af54773b03fd23994b83fe6d2fac1306c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337230"
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

## <a name="parameters"></a>Paramètres
`pszInterfaceName`\
[in] Chaîne contenant le nom de l’interface à rechercher.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK, retourne S_FALSE si l’interface n’existe pas ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En effet, cette méthode obtient une énumération de toutes les interfaces et recherche dans la liste pour une interface correspondant.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)