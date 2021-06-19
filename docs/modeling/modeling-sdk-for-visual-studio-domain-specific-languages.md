---
title: Kit de développement logiciel de modélisation pour Visual Studio - Langages spécifiques à un domaine
description: Découvrez qu’en utilisant le kit de développement logiciel (SDK) Modeling pour Visual Studio, vous pouvez créer de puissants outils de développement basés sur des modèles, que vous pouvez intégrer à Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b858e193065b5cee66772b6ec98321b505e9a8c3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391047"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Kit de développement logiciel de modélisation pour Visual Studio - Langages spécifiques à un domaine

En utilisant le kit de développement logiciel (SDK) Modeling pour Visual Studio, vous pouvez créer de puissants outils de développement basés sur des modèles, que vous pouvez intégrer à Visual Studio. De la même manière, vous pouvez créer une ou plusieurs définitions de modèle et la/les intégrer dans un ensemble d'outils.

La définition d'un modèle créé pour représenter les concepts de votre secteur d'activité est au cœur du MSDK. Vous pouvez entourer le modèle de divers outils, tels qu’une vue schématique, la capacité de générer du code et d’autres artefacts, des commandes pour transformer le modèle et la possibilité d’interagir avec du code et d’autres objets dans Visual Studio. Lorsque vous développez le modèle, vous pouvez le combiner avec d'autres modèles et outils et créer un ensemble d'outils puissant centré sur le développement.

MSDK vous permet de développer un modèle rapidement sous forme de langage spécifique à un domaine (DSL). Commencez par utiliser un éditeur spécialisé pour définir un schéma ou une syntaxe abstraite avec une notation graphique. À partir de cette définition, MSDK génère :

- une implémentation du modèle avec une API fortement typée qui s'exécute dans un magasin basé sur la transaction ;

- un explorateur basé sur l'arborescence ;

- un éditeur graphique dans lequel les utilisateurs peuvent afficher le modèle, ou une partie du modèle que vous définissez ;

- des méthodes de sérialisation qui enregistrent les modèles lisibles au format XML ;

- des fonctionnalités pour générer du code de programme et autres artefacts à l'aide de création de modèles de texte.

Toutes ces fonctionnalités peuvent être personnalisées et étendues. Les extensions sont intégrées de telle façon que vous pouvez toujours mettre à jour la définition DSL et générer de nouveau les fonctionnalités sans perdre ces extensions.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Billets de blog connexes](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
