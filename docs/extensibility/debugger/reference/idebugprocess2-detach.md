---
title: IDebugProcess2::Detach Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9036ebc44835ab6c3ebd08b9fad4408d9cb97461
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724129"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Détache le débbugger de ce processus en détachant tous les programmes dans le processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Tous les programmes et le processus continuent d’être en cours d’exécution, mais ne font plus partie de la session de déboguer. Une fois l’opération de détachement terminée, plus d’événements de débogé pour ce processus (et ses programmes) ne seront envoyés.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
