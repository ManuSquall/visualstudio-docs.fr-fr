---
title: Prise en charge du service de langage pour le débogage | Microsoft Docs
description: Découvrez les fonctionnalités du service de langage dans l’interface IVsLanguageDebugInfo qui assurent la prise en charge du débogage dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c17b11ce3639664a8097abeaa2a2de9a6faaadc7
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205162"
---
# <a name="language-service-support-for-debugging"></a>Prise en charge du service de langage pour le débogage
Un service de langage peut fournir des fonctionnalités qui prennent en charge un débogueur par le biais de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Ces fonctionnalités incluent la validation des points d’arrêt et la fourniture d’une liste d’expressions dans la fenêtre **automatique** .

 Toutefois, vous devez disposer d’un évaluateur d’expression pour déboguer votre langage. L’évaluateur d’expression est responsable de l’évaluation des expressions afin de produire des valeurs pendant le débogage. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez :

- [Évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Exemple d’évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Sortie du compilateur
 Le type de compilateur détermine ce que vous devez faire pour implémenter le débogage pour votre langage. Si votre compilateur cible le système d’exploitation Windows et écrit un fichier. pdb, vous pouvez déboguer des programmes à l’aide du moteur de débogage de code natif intégré à Visual Studio. Si votre compilateur produit le langage MSIL (Microsoft Intermediate Language), vous pouvez déboguer des programmes avec le moteur de débogage de code managé, qui est également intégré à Visual Studio. Si votre compilateur cible un système d’exploitation propriétaire ou un environnement d’exécution différent, vous devez écrire votre propre moteur de débogage.

 Pour plus d’informations sur l’implémentation du débogage pour votre langage, consultez [prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) dans le kit de développement logiciel (SDK) de débogage Visual Studio.
