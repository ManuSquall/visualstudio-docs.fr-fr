---
title: IDebugDocumentChecksum2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731899"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Représente un checksum pour un document de débogé et permet de passer le checksum entre les composants.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface peut être implémentée par n’importe quel composant qui expose l’interface [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Cependant, il est principalement mis en œuvre par les moteurs de déboçons de sorte que le checksum intégré dans un fichier de symbole (.pdb) peut être transmis à l’IDE et utilisé lors de la recherche d’une source.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugDocumentChecksum2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Récupère l’identifiant de vérification des documents et de l’algorithme étant donné le nombre maximum d’octets à utiliser.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
