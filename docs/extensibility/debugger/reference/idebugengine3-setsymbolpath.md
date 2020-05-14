---
title: IDebugEngine3:SetSymbolPath (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730660"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Définit le chemin ou les chemins qui sont recherchés pour les symboles de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Paramètres

`szSymbolSearchPath`\
[dans] Chaîne contenant le chemin de recherche de symbole ou des chemins. Voir "Remarques" pour plus de détails. Ne peut pas avoir la valeur null.

`szSymbolCachePath`\
[dans] Chaîne contenant le chemin local où les symboles peuvent être mis en cache. Ne peut pas avoir la valeur null.

`Flags`\
[dans] Non utilisé; toujours réglé à 0.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; renvoie autrement un code d’erreur.

## <a name="remarks"></a>Notes
 La `szSymbolSearchPath` chaîne est une liste d’un ou plusieurs chemins, séparés par des semi-colons, à la recherche de symboles. Ces chemins peuvent être un chemin local, un chemin de style UNC, ou une URL. Ces chemins peuvent également être un mélange de différents types. Si le chemin est UNC \\(par exemple, «Symserver-Symbols), puis le moteur de débogé devrait déterminer si le chemin est à un `szSymbolCachePath`serveur symbole et devrait être en mesure de charger des symboles à partir de ce serveur, les cachant dans le chemin spécifié par .

 Le chemin du symbole peut également contenir un ou plusieurs emplacements de cache. Les caches sont énumérées dans l’ordre prioritaire, avec le cache de priorité la plus élevée d’abord, et séparées par des symboles. Par exemple :

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 La méthode [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) effectue la charge réelle des symboles.

## <a name="see-also"></a>Voir aussi
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
