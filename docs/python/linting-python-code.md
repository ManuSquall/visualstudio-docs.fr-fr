---
title: Utiliser PyLint pour vérifier le code Python
description: Guide pratique pour utiliser PyLint dans Visual Studio pour vérifier les problèmes de code Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 7cf3e17ac70816afbd8ab67db8f407a2a982b279
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174690"
---
# <a name="using-pylint-to-check-python-code"></a>Utilisation de PyLint pour vérifier le code Python

[PyLint](https://www.pylint.org/), outil communément utilisé qui recherche les erreurs dans le code Python et favorise l’exactitude des modèles de codage Python, est intégré aux projets Python dans Visual Studio.

Pour l’utiliser, il vous suffit de cliquer avec le bouton droit sur un projet Python dans l’Explorateur de solutions et de sélectionner **Python > Run PyLint... (Exécuter Pylint)**  :

![Commande PyLint dans le menu contextuel des projets Python](media/code-pylint-command.png)

L’utilisation de cette commande vous invite si nécessaire à installer PyLint dans votre environnement actif.

Les avertissements et erreurs PyLint s’affichent dans la fenêtre Liste d’erreurs :

![Liste d’erreurs PyLint](media/code-pylint-error-list.png)

Un double-clic sur une erreur vous dirige directement vers le code source à l’origine du problème.

> [!Tip]
> Pour obtenir une liste détaillée de tous les messages de sortie PyLint, consultez le [guide de référence des fonctionnalités PyLint](https://pylint.readthedocs.io/en/latest/technical_reference/features.html).

## <a name="setting-pylint-command-line-options"></a>Définition des options de ligne de commande PyLint

La section [Command line options](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) (Options de ligne de commande) de la documentation PyLint explique comment contrôler le comportement de PyLint par le biais d’un fichier de configuration `.pylintrc`. Vous pouvez placer ce type de fichier à la racine d’un projet Python dans Visual Studio, ou à un autre emplacement, selon la portée d’application souhaitée pour ces paramètres (pour plus de détails, consultez les [options de ligne de commande](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)).

Par exemple, pour supprimer les avertissements « missing docstring » affichés sur l’image précédente avec un fichier `.pylintrc` dans un projet, effectuez les étapes suivantes :

1. Sur la ligne de commande, accédez à la racine de votre projet (qui contient votre fichier `.pyproj`) et exécutez la commande ci-après pour générer un fichier de configuration commenté :

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Dans l’Explorateur de solutions Visual Studio, cliquez avec le bouton droit sur votre projet, sélectionnez **Ajouter > Élément existant...**, recherchez et sélectionnez le nouveau fichier `.pylintrc`, puis sélectionnez **Ajouter**.

1. Ouvrez le fichier pour modification, qui contient différents paramètres que vous pouvez manipuler. Pour désactiver un avertissement, recherchez la section `[MESSAGES CONTROL]`, puis localisez le paramètre `disable` dans cette section. Vous y voyez une longue chaîne de messages spécifiques, auxquels vous pouvez ajouter les avertissements de votre choix. Dans cet exemple, ajoutez `,missing-docstring` (y compris la virgule de délimitation).

1. Enregistrez le fichier `.pylintrc`, puis réexécutez PyLint pour vérifier que les avertissements sont désormais supprimés.

> [!Tip]
> Pour utiliser un fichier `.pylintrc` à partir d’un partage réseau, créez une variable d’environnement nommée `PYLINTRC` avec la valeur du nom de fichier sur le partage réseau, en utilisant un chemin UNC ou une lettre de lecteur mappée. Par exemple, `PYLINTRC=\\myshare\python\.pylintrc`.
