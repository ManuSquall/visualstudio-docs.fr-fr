---
title: IDebugProperty3 | Microsoft Docs
description: Cette interface fournit la prise en charge pour la récupération d’une chaîne arbitrairement longue associée à la propriété, en associant un ID unique à la propriété, en extrayant une liste de visionneuses personnalisées pour la propriété, en définissant la valeur d’une propriété avec la capacité de signaler les erreurs résultantes.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65da477c47e88699cc479f632843f839b3d02f9d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469773"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Cette interface prend en charge les éléments suivants :

- Récupération d’une chaîne arbitrairement longue associée à la propriété.

- Association d’un ID unique à la propriété.

- Récupération d’une liste de visionneuses personnalisées pour la propriété.

- Définition de la valeur d’une propriété avec la capacité de signaler les erreurs résultantes

## <a name="syntax"></a>Syntaxe

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) implémente cette interface sur le même objet qui implémente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour assurer la prise en charge des chaînes longues, des ID de propriété et des visionneuses personnalisées.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProperty2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de `IDebugProperty2` , l' `IDebugProperty3` interface expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retourne la longueur de la chaîne associée à la propriété.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Retourne la chaîne dans une mémoire tampon fournie par l’utilisateur.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crée un ID unique pour cette propriété.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Détruit l’ID unique de cette propriété.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Retourne le nombre de visionneuses personnalisées avec lesquelles cette propriété peut être affichée.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retourne la liste des visionneuses personnalisées avec lesquelles cette propriété peut être affichée.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Définit la valeur de cette propriété, en renvoyant un message d’erreur en cas de problème.|

## <a name="remarks"></a>Notes
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) est la méthode recommandée pour le gestionnaire de débogage de session (SDM) pour définir la valeur d’une propriété.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
