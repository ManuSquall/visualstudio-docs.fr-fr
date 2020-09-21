---
title: Prise en main avec devinit
description: Guide de mise en route pour devinit.
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
ms.openlocfilehash: e0c6676b65637840a1b5878e06d6c5861c34e65d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809312"
---
# <a name="getting-started-with-devinit"></a>Prise en main avec devinit

## <a name="step-1-get-devinit"></a>Étape 1 : obtenir devinit

devinit est actuellement disponible uniquement dans le cadre de GitHub Codespaces lors de l’utilisation de Visual Studio et est accessible à partir du terminal intégré dans Visual Studio. À l’avenir, devinit sera disponible dans le cadre de Visual Studio.

## <a name="step-2-define-your-environment"></a>Étape 2 : définir votre environnement

L’étape la plus importante consiste à définir votre environnement « développeur » dans un [ _.devinit.jssur_ un fichier](devinit-json.md). Ce fichier sera utilisé par devinit pour créer votre environnement lors de l’exécution de `devinit init` .

Pour cette étape, réfléchissez aux instructions permettant à quelqu’un d’être opérationnel avec un référentiel de projet. Par exemple, le SQL doit-il être installé ? Une version spécifique de .NET Core ? suite. Ensuite, pour chacune de ces dépendances, recherchez un outil devinit correspondant dans la [liste des outils](devinit-tool-list.md)) et ajoutez-le au.devinit.jsdu référentiel _ sur_ le fichier.

## <a name="step-3-enjoy"></a>Étape 3 : Profitez-en !

Maintenant, toute personne doit effectuer une opération après le clonage de votre référentiel `devinit init` .

```batch
> devinit init
```

Si vous utilisez [GitHub Codespaces](https://github.com/features/codespaces), vous pouvez configurer `devinit init` pour qu’il s’exécute automatiquement lorsque le codeSpace est approvisionné. Pour en savoir plus, consultez la [documentation devinit et GitHub Codespaces](devinit-and-codespaces.md).
