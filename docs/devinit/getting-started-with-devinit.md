---
title: Prise en main avec devinit
description: Guide de mise en route pour devinit.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 660bb5a2c3d235a347e478d55ae8176e87c5d626
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672480"
---
# <a name="getting-started-with-devinit"></a>Prise en main avec devinit

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

devinit est un outil que vous pouvez utiliser pour permettre à quiconque d’accéder au code et de rester productif dans votre référentiel en exécutant une commande simple. Vous pouvez utiliser devinit pour définir toutes les dépendances à l’ensemble du système dont votre référentiel a besoin, comme SQL Server, Node.js, docker ou IIS. Devinit peut appeler d’autres outils et gestionnaires de package pour installer ce dont votre référentiel a besoin. Vous définissez ces dépendances dans un fichier JSON nommé [.devinit.jssur](devinit-json.md) , puis la personne suivante pour utiliser votre référentiel doit simplement s’exécuter [`devinit init`](devinit-commands.md#init) pour installer toutes ces dépendances. Ainsi, au lieu de passer une demi-journée à un nouveau référentiel, cette opération peut être effectuée en quelques minutes.

devinit n’est pas un gestionnaire de package ou un outil de configuration de machine virtuelle dans et de lui-même. Il s’agit d’un Runner de tâche pour un fichier manifeste, nommé [.devinit.jssur](devinit-json.md), qui définit les dépendances à l’ensemble du système dont votre application a besoin. Pour installer ces dépendances, devinit utilise des outils que vous utilisez peut-être déjà, tels que le [chocolat](https://chocolatey.org). Vous pouvez consulter les outils disponibles dans la [liste complète](devinit-tool-list.md). En utilisant ces outils plutôt que de distribuer directement les logiciels, devinit vous offre la commodité d’utiliser l’outil de votre choix et vous permet d’utiliser des configurations existantes, par exemple, un fichier [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) pour le chocolat.  

## <a name="step-1-get-devinit"></a>Étape 1 : obtenir devinit

devinit est actuellement disponible uniquement dans le cadre de GitHub Codespaces lors de l’utilisation de Visual Studio et est accessible à partir du terminal intégré dans Visual Studio. À l’avenir, devinit sera disponible dans le cadre de Visual Studio.

## <a name="step-2-define-your-environment"></a>Étape 2 : définir votre environnement

L’étape la plus importante consiste à définir votre environnement de développement dans un [.devinit.jsfichier](devinit-json.md). Ce fichier sera utilisé par devinit pour créer votre environnement lors de l’exécution de `devinit init` .

Pour cette étape, réfléchissez aux instructions permettant à quelqu’un d’être opérationnel avec un référentiel de projet. Par exemple, le SQL doit-il être installé ? Une version spécifique de .NET Core ? Et ainsi de suite. Ensuite, pour chacune de ces dépendances, recherchez un outil devinit correspondant dans la [liste des outils](devinit-tool-list.md) et ajoutez-le au fichier du référentiel `.devinit.json` .

Vous pouvez également voir une sélection d’exemples dans la [documentation des exemples](sample-readme.md)ou consulter le [didacticiel](tutorial.md).

## <a name="step-3-enjoy"></a>Étape 3 : Profitez-en !

Maintenant, toute personne doit effectuer une opération après le clonage de votre référentiel `devinit init` .

```console
devinit init
```

Si vous utilisez [GitHub Codespaces](https://github.com/features/codespaces), vous pouvez configurer `devinit init` pour qu’il s’exécute automatiquement lorsque le codeSpace est approvisionné. Pour en savoir plus, consultez la [documentation devinit et GitHub Codespaces](devinit-and-codespaces.md).
