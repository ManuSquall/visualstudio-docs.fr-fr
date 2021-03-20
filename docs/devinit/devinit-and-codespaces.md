---
title: devinit et GitHub Codespaces
description: Découvrez comment personnaliser un codeSpace pour Visual Studio à l’aide de devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c98c00e0b62d3a2a755790b07621d717abcb41c1
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672220"
---
# <a name="devinit-and-github-codespaces"></a>devinit et GitHub Codespaces

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

devinit est un excellent complément à [GitHub Codespaces](https://github.com/features/codespaces) et devinit peut être utilisé pour obtenir une installation codeSpace afin que les contributeurs puissent générer, exécuter et déboguer immédiatement.

> [!IMPORTANT]
> Avant d’intégrer devinit à votre codeSpace, vous devez d’abord vous assurer que vous disposez d’un `.devinit.json` fichier qui définit vos dépendances. Pour plus d’informations sur la création d’un `.devinit.json` , consultez la [documentation de prise en main](getting-started-with-devinit.md).

Dans un codeSpace GitHub, votre application est générée et exécutée dans le Cloud. Dans le Cloud, cela signifie que votre application n’a pas accès aux ressources locales sur vos ordinateurs. Ceux-ci incluent des outils ou des programmes que vous avez installés localement. Si votre application a besoin d’installer ou de configurer des dépendances à l’ensemble du système, elle doit être effectuée sur chaque codeSpace. Le moyen le plus simple d’y parvenir consiste à utiliser un `.devinit.json` fichier.

Pour vous assurer qu’un codeSpace est créé avec les dépendances dont votre application a besoin, `devinit` doit être exécuté lors de la création du codeSpace. Pour ce faire, vous pouvez appeler `devinit init` à partir du `postCreateCommand` défini dans un `.devcontainer.json` fichier placé dans la racine du référentiel. La ou les chaînes dans `postCreateCommand` sont exécutées dans l’interpréteur de commandes par défaut, une fois que le référentiel est cloné dans le codeSpace. Pour plus d’informations sur `postCreateCommand` , consultez la documentation sur la [personnalisation](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)de GitHub Codespaces. Pour ajouter la `devinit` commande, vous pouvez ajouter `devinit init` à la, `postCreateCommand` comme indiqué dans les exemples ci-dessous.

Vous pouvez également exécuter `devinit init -f <path to .devinit.json>` à partir du terminal intégré de Visual Studio une fois connecté à votre codeSpace.

## <a name="examples"></a>Exemples

Dans les deux exemples ci-dessous, le `.devinit.json` se trouve dans la racine du référentiel à côté de `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>Avec un .devcontainer.jssur le fichier

Dans cet exemple, le `.devcontainer.json` fichier ci-dessous est placé dans la racine référentiel en regard du `.devinit.json` fichier. Les fichiers peuvent également être placés dans un `.devcontainer` répertoire.

```json
{
  "postCreateCommand": "devinit init"
}
```

Lorsque `.devinit.json` se trouve dans un autre répertoire, l’indicateur-f peut être utilisé.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Vous trouverez d’autres exemples d’utilisation de devinit dans notre [documentation](sample-all-tool.md) et sur GitHub dans l' [exemple .net Core](https://github.com/microsoft/devinit-example-dotnet-core) et [Node.js](https://github.com/microsoft/devinit-example-nodejs) des exemples de référentiels.

### <a name="as-commands"></a>Comme commandes

Dans cet exemple, `.devcontainer.json` le fichier ci-dessous est placé dans la racine référentiel et `devinit run` est appelé directement à partir de la ligne de commande pour exécuter un outil individuel.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>À partir d’une invite de terminal

Lorsque le répertoire de travail actuel contient un `.devinit.json` fichier.

```console
devinit init
```

Lorsque `.devinit.json` se trouve dans un autre répertoire.

```console
devinit init -f path/to/.devinit.json
```
