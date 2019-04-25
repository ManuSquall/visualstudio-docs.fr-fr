---
title: .NET compiler Platform (&quot;Roslyn&quot;) extensibilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947300"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilité de .NET Compiler Platform (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La mission centrale des .NET Compiler Platform (« Roslyn ») est ouvrant les compilateurs C# et Visual Basic autorisant des outils et aux développeurs de partager dans les compilateurs riche d’informations sur les programmes. Outils d’analyse de code améliorent la qualité du code et facilitent la construction d’applications générateurs de code. Comme les outils gagnent en, ils doivent d’accéder à plus de la connaissance approfondie de code qui possèdent des seuls les compilateurs. Au lieu d’être opaques traducteurs (code source et du code objet), les compilateurs Roslyn offrent des API que vous pouvez utiliser pour les tâches liées à code dans vos outils et applications.  
  
 Le plus intéressant est que les compilateurs Roslyn, leurs API, exemples et procédures pas à pas et les outils réels reposant sur ces API sont entièrement open source chez [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Accédez au site Open source pour en savoir plus et prise en main Roslyn. Vous trouverez des liens pour obtenir les dernières C# et VB les fonctionnalités que vous pouvez utiliser comme un utilisateur final, ainsi que des liens vers la prise en main comme un générateur d’outil exploitant APIs Roslyn.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer avec les analyseurs Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
