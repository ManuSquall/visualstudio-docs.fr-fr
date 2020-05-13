---
title: IDebugClassField::DoesInterfaceExist ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734501"
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
[dans] Une chaîne contenant le nom de l’interface à rechercher.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, retourne S_OK, retourne S_FALSE si l’interface n’existe pas; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode obtient en effet un recensement de toutes les interfaces et recherche la liste pour une interface correspondante.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
