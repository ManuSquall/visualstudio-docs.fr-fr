---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69fbdef70fc9c95ef571ce0ce796199292417ca0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933555"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Représente une position dans un fichier source sous la forme d’un offset de caractère.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par l’IDE et consommé par les moteurs de débogage.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugDocumentPositionOffset2` .

|Méthode|Description|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Récupère la plage pour la position actuelle du document.|

## <a name="remarks"></a>Notes
 Cela retourne les mêmes informations que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , mais dans `char` les offsets à partir du début du document. Cela présente le document comme il existerait sur un disque, autrement dit un tableau unidimensionnel de caractères, au lieu des informations de ligne et de colonne qui sont généralement retournées.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
