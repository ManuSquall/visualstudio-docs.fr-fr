---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ef0ce265bc63ce9a00fd748c50a338d52294557
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211698"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Obtient le nom et l’identificateur du moteur de débogage (DE) un programme en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Paramètres
`pbstrEngine`\
[out] Retourne le nom de la DE l’exécution du programme (C++-spécifiques : cela peut être un pointeur null, indiquant que l’appelant n’est pas intéressés par le nom du moteur).

`pguidEngine`\
[out] Retourne l’identificateur global unique de la DE l’exécution du programme (C++-spécifiques : cela peut être un pointeur null, indiquant que l’appelant n’est pas intéressé par le GUID du moteur de données).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)