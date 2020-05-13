---
title: IDebugProgramHost2::GetHostName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722230"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtient le titre, le nom amical, ou le nom de fichier du processus d’hébergement de ce programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Paramètres
`dwType`\
[dans] Une valeur de [l’énumération GETHOSTNAME_TYPE.](../../../extensibility/debugger/reference/gethostname-type.md)

`pbstrHostName`\
[out] Retourne le nom demandé du processus d’hébergement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Dans une mise en œuvre typique de cette méthode, le `dwType` paramètre est ignoré et un nom amical de la machine hôte est retourné. Une autre implémentation `dwType` possible est de passer le paramètre à un appel à la méthode [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) pour obtenir le nom.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
