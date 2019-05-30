---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d6ff987e12e70a9d3dd443cfafc45d2698469b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335701"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Cette méthode est appelée pour afficher la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Paramètres
`hwnd`\
[in] Fenêtre parente

`dwID`\
[in] ID de visionneuses personnalisées qui prennent en charge plusieurs types.

`pHostServices`\
[in] Réservée. Toujours défini sur null.

`pDebugProperty`\
[in] Interface qui peut être utilisé pour récupérer la valeur à afficher.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur.

## <a name="remarks"></a>Notes
 L’affichage est « modal » dans la mesure où cette méthode créer la fenêtre nécessaires, afficher la valeur, attendre une entrée et fermez la fenêtre, tous avant de retourner à l’appelant. Cela signifie que la méthode doit gérer tous les aspects de l’affichage de la valeur de propriété, à partir de la création d’une fenêtre de sortie, à l’attente de l’entrée d’utilisateur, de la destruction de la fenêtre.

 Pour prendre en charge la modification de la valeur sur la donnée [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de l’objet, vous pouvez utiliser la [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) (méthode), si la valeur peut être exprimée sous forme de chaîne. Sinon, il est nécessaire de créer une interface personnalisée — exclusifs à l’évaluateur d’expression que l’implémentation de cela `DisplayValue` (méthode), sur le même objet qui implémente le `IDebugProperty3` interface. Cette interface personnalisée devriez normalement fournir des méthodes pour modifier les données d’une taille arbitraire ou de la complexité.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)