---
title: Démarrer avec Roslyn Analyzers (fr) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444977"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Bien démarrer avec les analyseurs Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec des analyseurs de code en direct basés sur des projets dans Visual Studio, les auteurs de l’API peuvent expédier des analyses de code spécifiques au domaine dans le cadre de leurs paquets NuGet.  Parce que ces analyseurs sont alimentés par la plate-forme de compilateur .NET (nom de code "Roslyn"), ils peuvent produire des avertissements dans votre code que vous tapez avant même que vous avez terminé la ligne (pas plus d’attente pour construire votre code pour découvrir les problèmes).  Les analyseurs peuvent également faire surface un correctif de code automatique à travers l’ampoule Visual Studio prompt pour vous permettre de nettoyer votre code immédiatement

## <a name="getting-started"></a>Mise en route
[Roslyn Live Code Analyzers Introduction et Procédure pas à pas](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Ajout de correctifs de code Procédure pas à pas: Fournir aux utilisateurs des correctifs pour les problèmes d’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduction et procédure pas à pas de Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [discours](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduction et visite de quelques analyseurs Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Autres ressources
[Plus de docs sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Règles FxCop mises en œuvre avec des analyseurs Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
