---
title: .NET compiler Platform (&quot;Roslyn&quot;) extensibilité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b910d1eb8dcbbe6696c447a7c3a94db533dbbcb3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347901"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET compiler Platform (&quot;Roslyn&quot;) extensibilité
La mission centrale des .NET Compiler Platform (« Roslyn ») est ouvrant les compilateurs c# et Visual Basic autorisant des outils et aux développeurs de partager dans les compilateurs riche d’informations sur les programmes. Outils d’analyse de code améliorent la qualité du code et facilitent la construction d’applications générateurs de code. Comme les outils gagnent en, ils doivent d’accéder à plus de la connaissance approfondie de code qui possèdent des seuls les compilateurs. Au lieu d’être opaques traducteurs (code source et du code objet), les compilateurs Roslyn offrent des API que vous pouvez utiliser pour les tâches liées à code dans vos outils et applications.

 Le plus intéressant est que les compilateurs Roslyn, leurs API, exemples et procédures pas à pas et les outils réels reposant sur ces API sont entièrement open source chez [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Accédez au site Open source pour en savoir plus et prise en main Roslyn. Vous trouverez des liens pour obtenir les dernières C# et les fonctionnalités de Visual Basic que vous pouvez utiliser en tant qu’un utilisateur final, ainsi que des liens pour démarrer comme un générateur d’outil exploitant APIs Roslyn.

## <a name="see-also"></a>Voir aussi
- [Prise en main des analyseurs de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)