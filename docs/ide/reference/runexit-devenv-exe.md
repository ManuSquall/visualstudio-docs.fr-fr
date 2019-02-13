---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa010e72267dadfb1974f7ce8be3b6b9a3e1cff
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936393"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Compile et exécute la solution ou le projet spécifié, puis ferme l’environnement de développement intégré (IDE).

## <a name="syntax"></a>Syntaxe

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Chemin complet et nom d’un fichier solution.

- *ProjectName*

  Chemin complet et nom d’un fichier projet.

- `/Out` *OutputFilename*

  Optionnel. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes

Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active. Ce commutateur réduit l’environnement IDE pendant l’exécution du projet ou de la solution, et le ferme ensuite.

- Placez entre guillemets doubles les chaînes contenant des espaces.

- Les informations résumées, notamment les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/Out`.

## <a name="example"></a>Exemple

Cet exemple exécute la solution `MySolution` dans une fenêtre réduite de l’IDE en utilisant la configuration de déploiement active, puis ferme l’IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)