---
title: API Reference (Visual Studio Debugging) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738176"
---
# <a name="api-reference-visual-studio-debugging"></a>Informations de référence sur les API (débogage Visual Studio)
La section de référence comprend un aperçu conceptuel de l’API, un guide qui montre la syntaxe et l’utilisation de tous les éléments API, et un assortiment d’exemples de code. Toutes les références sont répertoriées par ordre alphabétique par catégorie.

 Le tableau suivant `HRESULT` montre les valeurs communes retournées par les méthodes.

|Nom|Description|Valeur|
|----------|-----------------|-----------|
|S_OK|Réussite.|0x00000000|
|E_UNEXPECTED|Erreur inattendue.|0x8000FFFF|
|E_NOTIMPL|Non implémenté.|0x80004001|
|E_OUTOFMEMORY|Pas assez de mémoire pour terminer l’opération.|0x8007000E|
|E_INVALIDARG|Un ou plusieurs arguments sont invalides.|0x80070057|
|E_NOINTERFACE|Aucune interface de ce type n’est prise en charge.|0x80004002|
|E_POINTER|Pointeur invalide.|0x80004003|
|E_HANDLE|Poignée invalide.|0x80070006|
|E_ABORT|Opération abandonnée.|0x80004004|
|E_FAIL|Erreur inattendue.|0x80004005|
|E_ACCESSDENIED|Accès général refusé par erreur.|0x80070005|

> [!NOTE]
> Lorsqu’une [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] méthode de `S_OK`débogage revient, on suppose que tous les pointeurs de paramètres `S_OK` sont valides, c’est-à-dire qu’aucune validation n’est effectuée sur les pointeurs de paramètres lorsqu’il est retourné.
>
> [!NOTE]
> Les `NULL` paramètres invalides ou [out] peuvent provoquer l’écrasement de l’IDE.

## <a name="see-also"></a>Voir aussi
- [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
