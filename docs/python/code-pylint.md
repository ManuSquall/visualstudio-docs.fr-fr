---
title: Utilisation de PyLint dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>Utilisation de PyLint pour vérifier le code Python

[PyLint](https://www.pylint.org/), outil communément utilisé qui recherche les erreurs dans le code Python et favorise l’exactitude des modèles de codage Python, est intégré aux projets Python dans Visual Studio.

Pour l’utiliser, il vous suffit de cliquer avec le bouton droit sur un projet Python dans l’Explorateur de solutions et de sélectionner **Python > Run PyLint... (Exécuter Pylint)** :

![Commande PyLint dans le menu contextuel des projets Python](~/python/media/code-pylint-command.png)

L’utilisation de cette commande vous invite si nécessaire à installer PyLint dans votre environnement actif.

Les avertissements et erreurs PyLint s’affichent dans la fenêtre Liste d’erreurs :

![Liste d’erreurs PyLint](~/python/media/code-pylint-error-list.png)

Un double-clic sur une erreur vous dirige directement vers le code source à l’origine du problème.

> [!Tip]
> Pour obtenir une liste détaillée de tous les messages de sortie PyLint, consultez le [guide de référence des fonctionnalités PyLint](https://pylint.readthedocs.io/en/latest/reference_guide/features.html).

## <a name="setting-pylint-command-line-options"></a>Définition des options de ligne de commande PyLint

La section [Command line options](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) (Options de ligne de commande) de la documentation PyLint explique comment contrôler le comportement de PyLint par le biais d’un fichier de configuration `.pylintrc`. Vous pouvez placer ce type de fichier à la racine d’un projet Python dans Visual Studio, ou à un autre emplacement, selon la portée d’application souhaitée pour ces paramètres.

Par exemple, pour supprimer les avertissements « missing docstring » affichés sur l’image précédente avec un fichier `.pylintrc` dans un projet, procédez comme suit :

1. Sur la ligne de commande, accédez à la racine de votre projet (où vous trouverez votre fichier `.pyproj`) et exécutez la commande ci-après pour générer un fichier de configuration commenté :

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. Dans l’Explorateur de solutions Visual Studio, cliquez avec le bouton droit sur votre projet, sélectionnez **Ajouter > Élément existant...**, recherchez et sélectionnez le nouveau fichier `.pylintrc`, puis sélectionnez **Ajouter**.

1. Ouvrez le fichier pour modification. Vous y verrez différents paramètres que vous pourrez manipuler. Pour désactiver un avertissement, recherchez la section `[MESSAGES CONTROL]`, puis localisez le paramètre `disable` figurant dans cette section. Vous y verrez une longue chaîne de messages spécifiques, auxquels vous pouvez ajouter les avertissements de votre choix. Dans cet exemple, ajoutez `,missing-docstring` (y compris la virgule de délimitation).

1. Enregistrez le fichier `.pylintrc`, puis ré-exécutez PyLint pour vérifier que les avertissements sont désormais supprimés.
