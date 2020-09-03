---
title: 'IDebugProgram2 :: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722897"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Obtient les propriétés du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Paramètres
`ppProperty`\
à Retourne un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente les propriétés du programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les propriétés retournées par cette méthode sont spécifiques au programme. Si le programme doit retourner plusieurs propriétés, l’objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) retourné par cette méthode est un conteneur de propriétés supplémentaires et l’appel de la méthode [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) retourne une liste de toutes les propriétés.

 Un programme peut exposer n’importe quel nombre et type de propriétés supplémentaires qui peuvent être décrites par le biais de l' `IDebugProperty2` interface. Un IDE peut afficher les propriétés supplémentaires du programme par le biais d’une interface utilisateur de l’Explorateur de propriétés générique.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
