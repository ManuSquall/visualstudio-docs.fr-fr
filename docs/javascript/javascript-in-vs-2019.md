---
title: JavaScript et TypeScript dans Visual Studio 2019
description: Découvrez comment Visual Studio 2019 offre une prise en charge enrichie pour le développement JavaScript, à la fois en utilisant directement JavaScript et en utilisant le langage de programmation de machine à écrire.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 267bd8567b60a66bcf9d78c3aef8f02bbc942e0d
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025876"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript et TypeScript dans Visual Studio 2019

## <a name="overview"></a>Vue d’ensemble

Visual Studio 2019 assure une prise en charge complète du développement JavaScript, à la fois directement et avec le [langage de programmation TypeScript](http://www.typescriptlang.org/), qui a été développé pour offrir une expérience de développement JavaScript plus productive et plus agréable, en particulier pour des projets à grande échelle. Il est possible d’écrire du code JavaScript ou TypeScript dans Visual Studio pour de nombreux types d’applications et services.

## <a name="javascript-language-service"></a>Service de langage JavaScript

L’expérience JavaScript dans Visual Studio 2019 s’appuie sur le même moteur que la prise en charge de TypeScript, ce qui assure une meilleure prise en charge de fonctionnalités, une plus grande richesse et une intégration immédiatement prête à l’emploi.

La possibilité de revenir à l’ancien service de langage JavaScript n’est plus disponible. Les utilisateurs disposent maintenant du nouveau service de langage JavaScript intégré. Il s’appuie uniquement sur le service de langage TypeScript, qui repose sur l’analyse statique, ce qui nous permet de proposer de meilleurs outils : votre code JavaScript bénéficie ainsi de fonctionnalités IntelliSense plus riches, basées sur les définitions de type. Le nouveau service est léger et consomme moins de mémoire que l’ancien, ce qui assure de meilleurs résultats lorsque le code prend de l’ampleur. Nous avons également amélioré les performances du service de langage pour gérer les projets volumineux.

## <a name="typescript-support"></a>Prise en charge de TypeScript

Visual Studio 2019 propose plusieurs options d’intégration de la compilation TypeScript dans un projet :

* [Package NuGet de machine à écrire](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). lorsque le package NuGet pour TypeScript 3.2 (ou version ultérieure) est installé dans un projet, la version correspondante du service de langage TypeScript est chargée dans l’éditeur.
* [Package NPM de machine à écrire](https://www.npmjs.com/package/typescript). lorsque le package npm pour TypeScript 2.1 (ou version ultérieure) est installé dans un projet, la version correspondante du service de langage TypeScript est chargée dans l’éditeur.
* Le kit de développement logiciel (SDK) TypeScript, disponible par défaut dans Visual Studio Installer, ainsi qu’un kit SDK en téléchargement autonome sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395).

> [!TIP]
> Pour les projets développés dans Visual Studio 2019, nous vous encourageons à utiliser le package NuGet NuGet ou la NPM de machine à écrire pour une plus grande portabilité sur différents environnements et plateformes. Pour plus d’informations, consultez [compiler du code de machine à écrire à l’aide de NuGet](../javascript/compile-typescript-code-nuget.md) et compiler du [code machine à l’aide de TSC](../javascript/compile-typescript-code-npm.md).

## <a name="projects"></a>Projets

Les applications JavaScript UWP ne sont plus prises en charge dans Visual Studio 2019. Il n’est pas possible de créer ni d’ouvrir de projets UWP JavaScript (fichiers portant l’extension *.jsproj*). Pour plus d’informations, voir notre documentation sur la [création d’applications web progressives (PWA)](/microsoft-edge/progressive-web-apps-chromium) qui s’exécutent correctement sur Windows.
