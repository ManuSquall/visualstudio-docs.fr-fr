---
description: Représente une somme de contrôle pour un document de débogage et permet de passer la somme de contrôle entre les composants.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 518e5b089d0d34e2492297b27dd0829e5f00ef2f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066735"
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

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
