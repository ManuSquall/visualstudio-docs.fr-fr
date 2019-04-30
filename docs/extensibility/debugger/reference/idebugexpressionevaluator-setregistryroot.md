---
title: IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7b1d6fd8bb959bc789f52a2955abb13ee4f1165
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874164"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Cette méthode définit la racine du Registre. Utilisé pour le débogage côte à côte.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

#### <a name="parameters"></a>Paramètres
 `ustrRegistryRoot`

 [in] La nouvelle racine du Registre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La racine de Registre spécifiée est généralement définie lorsque l’évaluateur d’expression est instanciée et pointe vers la clé de Registre pour une version spécifique de Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y* , où *X.Y* est un numéro de version).

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)