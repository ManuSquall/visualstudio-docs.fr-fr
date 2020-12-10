---
title: Prise en main avec des analyseurs Roslyn | Microsoft Docs
description: Utilisez ces ressources pour vous familiariser avec les analyseurs Roslyn dans Visual Studio. comprend un didacticiel et plusieurs exemples.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c63510083f227f617b2a11ddec07510ffd792433
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994353"
---
# <a name="get-started-with-roslyn-analyzers"></a>Prise en main des analyseurs Roslyn

Avec des analyseurs de code en direct basés sur des projets dans Visual Studio, les créateurs d’API peuvent envoyer une analyse de code spécifique à un domaine dans le cadre de leurs packages NuGet. Étant donné que ces analyseurs sont alimentés par le .NET Compiler Platform (nom de code « Roslyn »), ils peuvent produire des avertissements dans votre code au fur et à mesure que vous tapez avant la fin de la ligne (plus besoin d’attendre pour générer votre code pour détecter les problèmes). Les analyseurs peuvent également faire apparaître un correctif de code automatique par le biais de l’invite de l’ampoule Visual Studio pour vous permettre de nettoyer immédiatement votre code.

## <a name="get-started"></a>Bien démarrer

[Vue d’ensemble des analyseurs Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutoriel : Écrire votre premier analyseur et correctif de code](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Ajouter des correctifs de code procédure pas à pas : fournir aux utilisateurs des correctifs pour les problèmes d’analyse](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Analyseur Roslyn réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [contact](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Voir aussi

- [Référence de la version du package .NET Compiler Platform](roslyn-version-support.md)
- [Autres documents sur le site OSS GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Règles FxCop implémentées avec des analyseurs Roslyn](../code-quality/fxcop-rule-port-status.md)
