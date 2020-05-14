---
title: .NET Compiler&quot;Platform&quot;( Roslyn ) Extensibility (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712080"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler&quot;Platform&quot;( Roslyn ) extensibility
La mission principale de la plate-forme de compilateur .NET ("Roslyn") est d’ouvrir les compilateurs de base C et visuel et de permettre aux outils et aux développeurs de partager les riches compilateurs d’informations ont sur les programmes. Les outils d’analyse de code améliorent la qualité du code, et les générateurs de code aident à la construction d’applications. Au fur et à mesure que les outils deviennent plus intelligents, ils ont besoin d’accéder à de plus en plus de connaissances en code profond que seuls les compilateurs possèdent. Au lieu d’être des traducteurs opaques (code source et code d’objet), les compilateurs Roslyn offrent des API que vous pouvez utiliser pour des tâches liées au code dans vos outils et applications.

 La meilleure partie est que les compilateurs Roslyn, leurs API, des échantillons et des passerelles, et les vrais outils construits sur le dessus de ces API sont tous entièrement open source à [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). S’il vous plaît aller sur le site OSS pour en savoir plus et commencer avec Roslyn. Vous trouverez des liens pour obtenir les dernières fonctionnalités de C et visual Basic que vous pouvez utiliser en tant qu’utilisateur final, ainsi que des liens pour commencer en tant que constructeur d’outils tirant parti des API Roslyn.

## <a name="see-also"></a>Voir aussi
- [Lancez-vous avec les analyseurs Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
