---
title: Prise en main des analyseurs de Roslyn | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec424f5e85f5bff9be5b276b3978b25dc3239fe5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-roslyn-analyzers"></a>Prise en main des analyseurs de Roslyn
Avec des analyseurs de code dynamique, basée sur le projet dans Visual Studio, les auteurs d’API peuvent être livrées analyse du code spécifique à un domaine dans le cadre de leurs packages NuGet.  Car ces analyseurs sont alimentées par la plateforme de compilateurs .NET (nom de code « Roslyn »), elles peuvent produire des avertissements dans votre code en cours de frappe avant même que vous avez terminé la ligne (pas plus en attente de générer votre code pour découvrir des problèmes).  Les analyseurs peuvent apparaître également un correctif de code automatique via l’invite d’ampoule Visual Studio pour vous permettre de nettoyer votre code immédiatement  
  
## <a name="getting-started"></a>Prise en main  
 [Les analyseurs de Code dynamique Roslyn Introduction et procédure pas à pas](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Ajout de Code résout la procédure pas à pas : Fournissent aux utilisateurs des correctifs pour les problèmes de l’analyseur](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Introduction et procédure pas à pas du monde réel analyseur Talk](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Analyseur de Roslyn monde réel](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [parler](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Plusieurs exemples sur github, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Introduction et présentation des analyseurs de quelques parler](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>Autres ressources  
 [Plusieurs documents sur le site github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Règles FxCop implémentés avec des analyseurs de Roslyn sur github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)