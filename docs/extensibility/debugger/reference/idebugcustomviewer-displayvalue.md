---
title: IDebugCustomViewer::DisplayValue - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
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
[dans] Fenêtre parent

`dwID`\
[dans] ID pour les téléspectateurs personnalisés qui prennent en charge plus d’un type.

`pHostServices`\
[in] Réservée. Toujours mis à annuler.

`pDebugProperty`\
[dans] Interface qui peut être utilisée pour récupérer la valeur à afficher.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur.

## <a name="remarks"></a>Notes
 L’affichage est "modal" en ce que cette méthode va créer la fenêtre nécessaire, afficher la valeur, attendre l’entrée, et fermer la fenêtre, le tout avant de retourner à l’appelant. Cela signifie que la méthode doit gérer tous les aspects de l’affichage de la valeur de la propriété, de la création d’une fenêtre pour la sortie, à l’attente de l’entrée de l’utilisateur, à la destruction de la fenêtre.

 Pour soutenir la modification de la valeur de l’objet [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) donné, vous pouvez utiliser la méthode [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , si la valeur peut être exprimée sous forme de chaîne. Sinon, il est nécessaire de créer une interface personnalisée, `DisplayValue` exclusive à l’évaluateur d’expression implémentant cette méthode, sur le même objet qui implémente l’interface. `IDebugProperty3` Cette interface personnalisée fournirait des méthodes pour modifier les données d’une taille ou d’une complexité arbitraires.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
