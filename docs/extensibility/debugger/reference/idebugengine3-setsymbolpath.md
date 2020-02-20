---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fe3000804971c8bd8cbf896a592bd11b875bfa8
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506380"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Définit le ou les chemins d’accès dans lesquels sont recherchés les symboles de débogage.

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
dans Chaîne contenant le chemin d’accès ou les chemins d’accès de recherche des symboles. Pour plus d’informations, consultez « Remarques ». Ne peut pas avoir la valeur null.

`szSymbolCachePath`\
dans Chaîne contenant le chemin d’accès local dans lequel les symboles peuvent être mis en cache. Ne peut pas avoir la valeur null.

`Flags`\
dans Non utilisé ; toujours défini sur 0.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La chaîne `szSymbolSearchPath` est une liste d’un ou plusieurs chemins d’accès, séparés par des points-virgules, pour rechercher des symboles. Ces chemins d’accès peuvent être un chemin d’accès local, un chemin d’accès de style UNC ou une URL. Ces chemins d’accès peuvent également être une combinaison de différents types. Si le chemin d’accès est UNC (par exemple, \\\Symserver\Symbols), le moteur de débogage doit déterminer si le chemin d’accès est un serveur de symboles et doit être en mesure de charger les symboles à partir de ce serveur, en les mettant en cache dans le chemin d’accès spécifié par `szSymbolCachePath`.

 Le chemin d’accès aux symboles peut également contenir un ou plusieurs emplacements du cache. Les caches sont répertoriés par ordre de priorité, avec le cache avec la priorité la plus élevée en premier, et séparés par des symboles *. Par exemple :

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 La méthode [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) effectue la charge réelle des symboles.

## <a name="see-also"></a>Voir aussi
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)