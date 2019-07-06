---
title: Mise en route avec les analyseurs Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6a6f4123f72afd8c310e627a9da6759f4c4548a
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586958"
---
# <a name="get-started-with-roslyn-analyzers"></a>Prise en main des analyseurs de Roslyn

Avec les analyseurs de code en direct, basée sur le projet dans Visual Studio, les auteurs de l’API peuvent être livrées analyse du code spécifique à un domaine dans le cadre de leurs packages NuGet. Étant donné que ces analyseurs sont alimentées par la plateforme de compilateur .NET (nom de code « Roslyn »), peuvent produire des avertissements dans votre code en cours de frappe avant même que vous avez terminé la ligne (pas d’autres en attente pour générer votre code pour découvrir des problèmes). Les analyseurs peuvent également se manifester un correctif de code automatique via l’invite d’ampoule Visual Studio pour vous permettre de nettoyer votre code immédiatement.

## <a name="get-started"></a>Prise en main

[Vue d’ensemble des analyseurs de Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutoriel : Écrire votre premier correctif d’analyseur et le code](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Ajoutez la procédure pas à pas des correctifs de code : Fournir des correctifs d’utilisateurs pour les problèmes de l’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analyseur Roslyn de monde réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder en tant qu’un [talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Voir aussi

- [Référence de version de package .NET du compilateur plateforme](roslyn-version-support.md)
- [Docs plus sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Règles FxCop implémentées avec des analyseurs de Roslyn](http://roslynanalyzersstatus.azurewebsites.net/)
