---
title: Mise en route avec les analyseurs Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57573adeceda942b2968bfe07108ff4d54a8435f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911805"
---
# <a name="get-started-with-roslyn-analyzers"></a>Prise en main des analyseurs de Roslyn

Avec les analyseurs de code en direct, basée sur le projet dans Visual Studio, les auteurs de l’API peuvent être livrées analyse du code spécifique à un domaine dans le cadre de leurs packages NuGet. Étant donné que ces analyseurs sont alimentées par la plateforme de compilateur .NET (nom de code « Roslyn »), peuvent produire des avertissements dans votre code en cours de frappe avant même que vous avez terminé la ligne (pas d’autres en attente pour générer votre code pour découvrir des problèmes). Les analyseurs peuvent également se manifester un correctif de code automatique via l’invite d’ampoule Visual Studio pour vous permettre de nettoyer votre code immédiatement.

## <a name="get-started"></a>Prise en main

[Procédure pas à pas et présentation des analyseurs de Roslyn code en direct](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Ajoutez la procédure pas à pas des correctifs de code : Fournir des correctifs d’utilisateurs pour les problèmes de l’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduction et procédure pas à pas de l’analyseur du monde réel de communiquer avec](https://channel9.msdn.com/events/Build/2015/3-725)

[Analyseur Roslyn de monde réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder en tant qu’un [talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduction et présentation des analyseurs quelques talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Tutoriel : Écrire votre premier correctif d’analyseur et le code](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)
- [Référence de version de package .NET du compilateur plateforme](roslyn-version-support.md)
- [Docs plus sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Règles FxCop implémentées avec des analyseurs de Roslyn](http://roslynanalyzersstatus.azurewebsites.net/)
