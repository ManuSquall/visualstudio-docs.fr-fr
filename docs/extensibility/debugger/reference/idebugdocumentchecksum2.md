---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731899"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Représente une somme de contrôle pour un document de débogage et permet de passer la somme de contrôle entre les composants.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface peut être implémentée par n’importe quel composant qui expose l’interface [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Toutefois, elle est implémentée principalement par les moteurs de débogage afin que la somme de contrôle incorporée dans un fichier de symboles (*. pdb) puisse être repassée à l’IDE et utilisée lors de la recherche d’une source.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugDocumentChecksum2` .

|Méthode|Description|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Récupère la somme de contrôle de document et l’identificateur d’algorithme en fonction du nombre maximal d’octets à utiliser.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
