---
title: IDebugCustomViewer ::D isplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732443"
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
dans Fenêtre parente

`dwID`\
dans ID des visionneuses personnalisées qui prennent en charge plusieurs types.

`pHostServices`\
[in] Réservée. Toujours défini sur null.

`pDebugProperty`\
dans Interface qui peut être utilisée pour récupérer la valeur à afficher.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 L’affichage est « modal » dans le fait que cette méthode crée la fenêtre nécessaire, affiche la valeur, attend une entrée, puis ferme la fenêtre, tout avant de retourner à l’appelant. Cela signifie que la méthode doit gérer tous les aspects de l’affichage de la valeur de la propriété, de la création d’une fenêtre pour la sortie, à l’attente de l’entrée de l’utilisateur, à la destruction de la fenêtre.

 Pour prendre en charge la modification de la valeur de l’objet [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) donné, vous pouvez utiliser la méthode [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , si la valeur peut être exprimée sous la forme d’une chaîne. Dans le cas contraire, il est nécessaire de créer une interface personnalisée, à l’exception de l’évaluateur d’expression qui implémente cette `DisplayValue` méthode, sur le même objet qui implémente l' `IDebugProperty3` interface. Cette interface personnalisée fournit des méthodes pour modifier les données d’une taille ou d’une complexité arbitraire.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
