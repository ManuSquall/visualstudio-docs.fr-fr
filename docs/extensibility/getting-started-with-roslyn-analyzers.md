---
title: Démarrer avec Roslyn Analyzers (fr) Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711269"
---
# <a name="get-started-with-roslyn-analyzers"></a>Lancez-vous avec les analyseurs Roslyn

Avec des analyseurs de code en direct basés sur des projets dans Visual Studio, les auteurs de l’API peuvent expédier des analyses de code spécifiques au domaine dans le cadre de leurs paquets NuGet. Parce que ces analyseurs sont alimentés par la plate-forme de compilateur .NET (nom de code "Roslyn"), ils peuvent produire des avertissements dans votre code que vous tapez avant même que vous avez terminé la ligne (pas plus d’attente pour construire votre code pour découvrir les problèmes). Les analyseurs peuvent également faire surface un correctif de code automatique à travers l’ampoule Visual Studio prompt pour vous permettre de nettoyer votre code immédiatement.

## <a name="get-started"></a>Bien démarrer

[Aperçu des analyseurs Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutoriel : Écrire votre premier analyseur et correctif de code](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Ajouter des correctifs de code Procédure pas à pas : fournir aux utilisateurs des correctifs pour les problèmes d’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analyseur Roslyn du monde réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [discours](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Voir aussi

- [.NET compiler plate-forme de référence de version paquet](roslyn-version-support.md)
- [Plus de docs sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Règles FxCop mises en œuvre avec les analyseurs Roslyn](../code-quality/fxcop-rule-port-status.md)
