---
title: devinit et GitHub Codespaces
description: Découvrez comment personnaliser un codeSpace pour Visual Studio à l’aide de devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b42ce84bcb2a336e37d0ffafb2bab6c2dba9ba9d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852208"
---
# <a name="devinit-and-github-codespaces"></a>devinit et GitHub Codespaces

devinit est un excellent compliment pour [GitHub Codespaces](https://github.com/features/codespaces) et devinit peut être utilisé pour obtenir une installation codeSpace afin que les contributeurs puissent générer, exécuter et déboguer immédiatement.

Pour une intégration à GitHub Codespaces, `devinit` doit être appelé à partir du `postCreateCommand` défini dans un `.devcontainer.json` fichier placé dans la racine référentiel. La ou les chaînes dans `postCreateCommand` sont exécutées dans l’interpréteur de commandes par défaut, une fois que le référentiel est cloné dans le codeSpace. Pour plus d’informations sur `postCreateCommand` , consultez la documentation sur la [personnalisation](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)de GitHub Codespaces. Pour ajouter la `devinit` commande, vous pouvez ajouter `devinit init` à la, `postCreateCommand` comme indiqué dans les exemples ci-dessous.

Vous pouvez également exécuter `devinit init -f <path to .devinit.json>` à partir du terminal intégré de Visual Studio une fois connecté à votre codeSpace.

## <a name="examples"></a>Exemples

### <a name="with-a-devinitjson-file"></a>Avec un .devinit.jssur le fichier
Dans cet exemple, le _.devcontainer.jsdans_ le fichier ci-dessous est placé dans la racine référentiel avec le _.devinit.jssur_ le fichier. Les fichiers peuvent également être placés dans un répertoire _. devcontainer_ .

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>Comme commandes
Dans cet exemple _.devcontainer.js_ le fichier ci-dessous est placé dans la racine référentiel et `devinit run` est appelé par programme pour exécuter un outil  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>À partir d’une invite de terminal

Lorsque le répertoire de travail actuel contient un _.devinit.jssur_ le fichier.

```batch
> devinit init
```

Lorsque le _.devinit.jssur_ se trouve dans un autre répertoire.

```batch
> devinit init -f path/to/.devinit.json
```
