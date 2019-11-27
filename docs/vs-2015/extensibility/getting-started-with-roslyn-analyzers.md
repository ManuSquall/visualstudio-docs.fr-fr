---
title: Prise en main avec des analyseurs Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300013"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Bien démarrer avec les analyseurs Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec des analyseurs de code en direct basés sur des projets dans Visual Studio, les créateurs d’API peuvent envoyer une analyse de code spécifique à un domaine dans le cadre de leurs packages NuGet.  Étant donné que ces analyseurs sont alimentés par le .NET Compiler Platform (nom de code « Roslyn »), ils peuvent produire des avertissements dans votre code au fur et à mesure que vous tapez avant la fin de la ligne (plus besoin d’attendre pour générer votre code pour détecter les problèmes).  Les analyseurs peuvent également faire apparaître un correctif de code automatique par le biais de l’invite de l’ampoule Visual Studio pour vous permettre de nettoyer immédiatement votre code

## <a name="getting-started"></a>Mise en route
[Présentation et procédure pas à pas des analyseurs de code Roslyn Live](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Ajout de correctifs de code procédure pas à pas : fournir aux utilisateurs des correctifs pour les problèmes d’analyseur](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Présentation et procédure pas à pas de l’analyse du monde réel](https://channel9.msdn.com/events/Build/2015/3-725)

[Analyseur Roslyn réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [contact](https://channel9.msdn.com/events/Build/2015/3-725)

[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Présentation et présentation d’un certain nombre d’analyseurs](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Autres ressources
[Autres documents sur le site OSS GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Règles FxCop implémentées avec des analyseurs Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
