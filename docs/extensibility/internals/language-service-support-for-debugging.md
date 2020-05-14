---
title: Soutien aux services linguistiques pour le débogage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707437"
---
# <a name="language-service-support-for-debugging"></a>Prise en charge du service de langage pour le débogage
Un service linguistique peut fournir des fonctionnalités <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> qui prennent en charge un débbugger à travers l’interface. Ces caractéristiques comprennent la validation des points d’arrêt et la fourniture d’une liste d’expressions à la fenêtre **Autos.**

 Cependant, vous devez avoir un évaluateur d’expression pour déboiffer votre langue. L’évaluateur de l’expression est chargé d’évaluer les expressions pour produire des valeurs tout en débogage. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter :

- [Évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Échantillon d’évaluateur d’expression géré](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Sortie du compilateur
 Le type de compilateur détermine ce que vous devez faire pour implémenter le débogage pour votre langue. Si votre compilateur cible le système d’exploitation Windows et écrit un fichier .pdb, vous pouvez déboguer des programmes avec le moteur de débogage de code natif qui est intégré dans Visual Studio. Si votre compilateur produit la langue intermédiaire Microsoft (MSIL), vous pouvez déboguer des programmes avec le moteur de débogage de code géré, qui est également intégré dans Visual Studio. Si votre compilateur cible un système d’exploitation propriétaire ou un environnement de temps d’exécution différent, vous devez écrire votre propre moteur de débogage.

 Pour plus d’informations sur la mise en œuvre de débogage pour votre langue, voir [Getting Started](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in the Visual Studio Debugging SDK.
