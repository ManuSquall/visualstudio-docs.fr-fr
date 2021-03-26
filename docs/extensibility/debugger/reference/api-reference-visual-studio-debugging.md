---
description: La section de référence comprend une vue d’ensemble conceptuelle de l’API, un guide qui montre la syntaxe et l’utilisation de tous les éléments d’API, ainsi qu’un assortiment d’exemples de code.
title: Référence d’API (débogage Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8a43e4bae5afce98e07b196f5a01c33d44c72ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085544"
---
# <a name="api-reference-visual-studio-debugging"></a>Informations de référence sur les API (débogage Visual Studio)
La section de référence comprend une vue d’ensemble conceptuelle de l’API, un guide qui montre la syntaxe et l’utilisation de tous les éléments d’API, ainsi qu’un assortiment d’exemples de code. Toutes les références sont classées par catégorie dans l’ordre alphabétique.

 Le tableau suivant indique les `HRESULT` valeurs communes retournées par les méthodes.

|Nom|Description|Valeur|
|----------|-----------------|-----------|
|S_OK|Réussite.|0x00000000|
|E_UNEXPECTED|Erreur inattendue.|0x8000FFFF|
|E_NOTIMPL|Non implémenté.|0x80004001|
|E_OUTOFMEMORY|Mémoire insuffisante pour terminer l’opération.|0x8007000E|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|0x80070057|
|E_NOINTERFACE|Aucune interface de ce type n’est prise en charge.|0x80004002|
|E_POINTER|Pointeur non valide.|0x80004003|
|E_HANDLE|Handle non valide.|0x80070006|
|E_ABORT|Opération abandonnée.|0x80004004|
|E_FAIL|Erreur inattendue.|0x80004005|
|E_ACCESSDENIED|Erreur d’accès général refusé.|0x80070005|

> [!NOTE]
> Lorsqu’une [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] méthode de débogage retourne `S_OK` , il est supposé que tous les pointeurs de paramètre de sortie sont valides, autrement dit, aucune validation n’est effectuée sur les pointeurs de paramètre en sortie lorsque `S_OK` est retourné.
>
> [!NOTE]
> Les paramètres non valides ou `NULL` [out] peuvent provoquer le blocage de l’IDE.

## <a name="see-also"></a>Voir aussi
- [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
