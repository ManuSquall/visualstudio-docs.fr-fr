---
title: Mise en route avec les analyseurs de Roslyn | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a71add3ac837e3727d54b379b6e82ee126e4a3f
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-roslyn-analyzers"></a>Mise en route avec les analyseurs de Roslyn
Avec des analyseurs de code dynamique, basée sur le projet dans Visual Studio, les auteurs de l’API peuvent envoyer analyse du code spécifique à un domaine dans le cadre de leurs packages NuGet.  Étant donné que ces analyseurs sont alimentées par la plateforme des compilateurs .NET (nom de code « Roslyn »), ils peuvent produire des avertissements dans votre code en cours de frappe avant même que vous avez fini de la ligne (pas plus en attente pour générer votre code pour découvrir des problèmes).  Analyseurs peuvent également faire apparaître un correctif de code automatique via l’invite d’ampoule Visual Studio pour vous permettre de nettoyer votre code immédiatement  
  
## <a name="getting-started"></a>Commencer  
 [Les analyseurs de Code dynamique Roslyn Introduction et une procédure pas à pas](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Ajout de Code résout la procédure pas à pas : Fournissent aux utilisateurs des correctifs pour les problèmes d’analyseur](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Introduction et une procédure pas à pas de présentation d’analyseur de monde réel](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Analyseur de Roslyn Real World](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que vous pouvez également regarder comme un [parler](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Plusieurs exemples sur github, regroupées en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Introduction et présentation des analyseurs quelques parler](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>Autres ressources  
 [Plus de documents sur le site github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Règles de FxCop implémentés avec les analyseurs de Roslyn sur github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
