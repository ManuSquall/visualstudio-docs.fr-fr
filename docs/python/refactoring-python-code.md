---
title: Refactoriser du code Python
description: Visual Studio permet de refactoriser facilement du code Python en renommant les identificateurs, en extrayant les méthodes, en ajoutant des importations et en supprimant les importations inutilisées.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 26a9fa2ee8673b3e8773484409ee680f14780d7a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859105"
---
# <a name="refactor-python-code"></a>Refactoriser du code Python

Visual Studio fournit plusieurs commandes pour transformer et nettoyer automatiquement votre code source Python :

- [Renommer](#rename) modifie le nom d’une variable, d’une méthode ou d’une classe sélectionnée
- [Extraire la méthode](#extract-method) crée une nouvelle méthode à partir du code sélectionné
- [Ajouter à l’importation](#add-import) fournit une balise intelligente pour ajouter une importation manquante
- [Supprimer les importations inutilisées](#remove-unused-imports) supprime les importations inutilisées

## <a name="rename"></a>Renommer

1. Cliquez avec le bouton droit sur l’identificateur à renommer, puis sélectionnez **Renommer**, ou placez le point d’insertion sur cet identificateur et sélectionnez la commande de menu **Modifier** > **Refactoriser** > **Renommer** (**F2**).
2. Dans la boîte de dialogue **Renommer** qui s’affiche, entrez le nouveau nom de l’identificateur et sélectionnez **OK** :

   ![Renommer l’invite pour le nouveau nom d’identificateur](media/code-refactor-rename-1.png)

3. Dans la boîte de dialogue suivante, sélectionnez les fichiers et les instances de votre code auxquels appliquer le changement de nom. Sélectionnez n’importe quelle instance pour afficher un aperçu de la modification spécifique :

   ![Renommer la boîte de dialogue pour sélectionner l’endroit ou appliquer les modifications](media/code-refactor-rename-2.png)

4. Sélectionnez **Appliquer** pour modifier vos fichiers de code source. (Cette action peut être annulée.)

## <a name="extract-method"></a>Extraire la méthode

1. Sélectionnez les lignes de code ou l’expression à extraire dans une méthode distincte.
2. Sélectionnez la commande de menu **Modifier** > **Refactoriser** > **Extraire la méthode**, ou tapez **Ctrl**+**R** > **M**.
3. Dans la boîte de dialogue qui s’affiche, entrez un nouveau nom de méthode, indiquez vers où l’extraire, puis sélectionnez toutes les variables de fermeture. Les variables qui ne sont pas sélectionnées pour la fermeture sont transformées en arguments de méthode :

   ![Boîte de dialogue Extraire la méthode](media/code-refactor-extract-method-1.png)

4. Sélectionnez **OK** pour modifier le code en conséquence :

   ![Effet lié à l’extraction d’une méthode](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Ajouter à l’importation

Quand vous placez le signe insertion sur un identificateur qui ne dispose pas d’informations de type, Visual Studio fournit une balise active (l’icône d’ampoule à gauche du code), dont les commandes ajoutent l’instruction `import` ou `from ... import` nécessaire :

![Balise intelligente d’Ajouter l’importation](media/code-refactor-add-import-1.png)

Visual Studio propose des saisies semi-automatiques `import` pour les packages de niveau supérieur et les modules du projet actuel et de la bibliothèque standard. Visual Studio offre également des saisies semi-automatiques `from ... import` pour les sous-modules et sous-packages ainsi que les membres de module. Les saisies semi-automatiques comprennent des fonctions, des classes ou des données exportées. Sélectionnez une des options pour ajouter l’instruction en haut du fichier après les autres importations, ou dans une instruction `from ... import` existante si le même module est déjà importé.

![Résultat de l’ajout d’une importation](media/code-refactor-add-import-2.png)

Visual Studio tente de filtrer les membres qui ne sont pas réellement définis dans un module, tels que les modules importés dans un autre module, mais qui ne sont pas des enfants du module à l’origine de l’importation. Par exemple, de nombreux modules utilisent `import sys` plutôt que `from xyz import sys`. Par conséquent, vous ne voyez pas de saisie semi-automatique pour l’importation de `sys` à partir d’autres modules, même s’il manque aux modules un membre `__all__` qui exclut `sys`.

De même, Visual Studio filtre les fonctions importées à partir d’autres modules ou de l’espace de noms intégré. Par exemple, si un module importe la fonction `settrace` à partir du module `sys`, vous pouvez théoriquement l’importer à partir de ce module. Toutefois, il est préférable d’utiliser directement `import settrace from sys` pour que Visual Studio propose spécifiquement cette instruction.

Enfin, si un élément doit normalement être exclu, mais qu’il a d’autres valeurs qui peuvent être incluses (parce qu’une valeur a été affectée au nom dans le module, par exemple), Visual Studio exclut l’importation. Ce comportement suppose que la valeur ne doit pas être exportée parce qu’elle est définie dans un autre module et que, par conséquent, l’affectation supplémentaire est susceptible d’être une valeur factice qui n’est pas non plus exportée.

## <a name="remove-unused-imports"></a>Supprimer les importations inutilisées

Lors de l’écriture de code, il est facile de vous retrouver avec des instructions `import` concernant des modules qui ne sont pas utilisées du tout. Visual Studio analyse votre code et détermine automatiquement si une instruction `import` est nécessaire en regardant si les noms importés sont utilisés dans le cadre ci-dessous, où l’instruction s’exécute.

Cliquez avec le bouton droit n’importe où dans l’éditeur, puis sélectionnez **Remove Imports** (Supprimer les importations), qui vous propose des suppressions à partir de **toutes les portées** ou uniquement de la **portée actuelle** :

![Menu Supprimer les importations](media/code-refactor-remove-imports-1.png)

Ensuite, Visual Studio modifie le code en conséquence :

![Effet lié à la suppression des importations](media/code-refactor-remove-imports-2.png)

Notez que Visual Studio ne tient pas compte du flux de contrôle. L’utilisation d’un nom avant une instruction `import` est traitée comme si le nom était utilisé. Visual Studio ignore également toutes les importations `from __future__`, ainsi que les importations effectuées au sein d’une définition de classe, ou à partir d’instructions `from ... import *`.
