---
description: Détermine si une interface spécifique est définie dans la classe.
title: IDebugClassField ::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173466"
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
dans Chaîne contenant le nom de l’interface à rechercher.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK, retourne S_FALSE si l’interface n’existe pas ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode obtient une énumération de toutes les interfaces et recherche une interface correspondante dans la liste.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
