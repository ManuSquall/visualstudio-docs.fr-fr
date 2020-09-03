---
title: Extensibilité de .NET Compiler Platform ( &quot; Roslyn &quot; ) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712080"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilité .NET Compiler Platform ( &quot; Roslyn &quot; )
La mission principale du .NET Compiler Platform (« Roslyn ») ouvre les compilateurs C# et Visual Basic, et permet aux outils et aux développeurs de partager dans les programmes que les compilateurs d’informations possèdent sur les programmes. Les outils d’analyse du code améliorent la qualité du code, et les générateurs de code facilitent la construction des applications. À mesure que les outils sont plus intelligents, ils ont besoin d’accéder à de plus en plus de la connaissance du code profond que seuls les compilateurs possèdent. Au lieu d’être des traducteurs opaques (code source dans et code d’objet), les compilateurs Roslyn proposent des API que vous pouvez utiliser pour les tâches liées au code dans vos outils et vos applications.

 La meilleure partie est que les compilateurs Roslyn, leurs API, exemples et procédures pas à pas, et les véritables outils basés sur ces API sont entièrement open source sur [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Accédez au site OSS pour en savoir plus et vous familiariser avec Roslyn. Vous trouverez des liens pour obtenir les dernières fonctionnalités de C# et de Visual Basic que vous pouvez utiliser comme utilisateur final, ainsi que des liens pour commencer en tant que générateur d’outils tirant parti des API Roslyn.

## <a name="see-also"></a>Voir aussi
- [Prise en main des analyseurs Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
