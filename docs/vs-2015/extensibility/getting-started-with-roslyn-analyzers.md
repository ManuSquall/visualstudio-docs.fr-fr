---
title: Mise en route avec les analyseurs Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 104e3a30589f5892c1440266afd7917486d704ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949498"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Bien démarrer avec les analyseurs Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec les analyseurs de code en direct, basée sur le projet dans Visual Studio, les auteurs de l’API peuvent être livrées analyse du code spécifique à un domaine dans le cadre de leurs packages NuGet.  Étant donné que ces analyseurs sont alimentées par la plateforme de compilateur .NET (nom de code « Roslyn »), peuvent produire des avertissements dans votre code en cours de frappe avant même que vous avez terminé la ligne (pas d’autres en attente pour générer votre code pour découvrir des problèmes).  Les analyseurs peuvent également se manifester un correctif de code automatique via l’invite d’ampoule Visual Studio pour vous permettre de nettoyer votre code immédiatement

## <a name="getting-started"></a>Prise en main
[Les analyseurs de Code en direct de Roslyn Introduction et procédure pas à pas](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Ajout de Code résout la procédure pas à pas : Fournir des correctifs d’utilisateurs pour les problèmes de l’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduction et procédure pas à pas du monde réel analyseur Talk](http://channel9.msdn.com/events/Build/2015/3-725)

[Analyseur de Roslyn Real World](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder en tant qu’un [talk](http://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduction et présentation des analyseurs quelques Talk](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Autres ressources
[Docs plus sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Règles FxCop implémentées avec des analyseurs de Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
