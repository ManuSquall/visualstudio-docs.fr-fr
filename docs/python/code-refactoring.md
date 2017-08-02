---
title: Refactorisation de code Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ebcb29-72d1-4958-9a63-8984c03d5c22
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
ms.openlocfilehash: ea69604524010ab794a4de0e85aea1e5fd680ac4
ms.lasthandoff: 04/10/2017

---

# <a name="refactoring-python-code"></a>Refactorisation de code Python

Visual Studio fournit plusieurs commandes pour transformer et nettoyer automatiquement votre code source Python :

- [Renommer](#rename) modifie le nom d’une variable, d’une méthode ou d’une classe sélectionnée
- [Extraire la méthode](#extract-method) crée une nouvelle méthode à partir du code sélectionné
- [Ajouter à l’importation](#add-import) fournit une balise intelligente pour ajouter une importation manquante
- [Supprimer les importations inutilisées](#remove-imports) supprime les importations inutilisées

<a name="rename-variable"</a>
## <a name="rename"></a>Renommer

1. Cliquez avec le bouton droit sur le l’identificateur que vous souhaitez renommer et sélectionnez **Renommer**, ou placez le point d’insertion dans cet identificateur et sélectionnez la commande de menu **Modifier > Refactoriser > Renommer...** ou sur F2.
1. Dans la boîte de dialogue **Renommer** qui s’affiche, entrez le nouveau nom de l’identificateur et sélectionnez **OK** :

  ![Renommer l’invite pour le nouveau nom d’identificateur](~/python/media/code-refactor-rename-1.png)

1. Dans la boîte de dialogue suivante, sélectionnez les fichiers et les instances de votre code auxquels appliquer le changement de nom. Sélectionnez n’importe quelle instance pour afficher un aperçu de la modification spécifique :

  ![Renommer la boîte de dialogue pour sélectionner l’endroit ou appliquer les modifications](~/python/media/code-refactor-rename-2.png)

1. Sélectionnez **Appliquer** pour modifier vos fichiers de code source. Il s’agit d’une action annulable.

## <a name="extract-method"></a>Extraire la méthode

1. Sélectionnez les lignes de code ou l’expression à extraire vers une méthode distincte.
1. Sélectionnez la commande de menu **Modifier > Refactoriser > Extraire la méthode...** ou tapez Ctrl + R et M.
1. Dans la boîte de dialogue qui s’affiche, entrez un nouveau nom de méthode, indiquez vers où l’extraire, puis sélectionnez toutes les variables de fermeture. Les variables qui ne sont pas sélectionnées pour la fermeture sont transformées en arguments de méthode :

  ![Boîte de dialogue Extraire la méthode](~/python/media/code-refactor-extract-method-1.png)

1. Sélectionnez **OK** pour modifier le code en conséquence :

  ![Effet lié à l’extraction d’une méthode](~/python/media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Ajouter à l’importation

Quand vous placez le point d’insertion sur un identificateur qui ne dispose pas d’informations de type, Visual Studio fournit une balise intelligente (l’icône d’ampoule à gauche du code), dont les commandes ajoutent l’instruction `import` ou `from ... import` nécessaire :

![Balise intelligente d’Ajouter l’importation](~/python/media/code-refactor-add-import-1.png)

Les saisies semi-automatique de `import` sont proposées pour les packages de niveau supérieur et les modules du projet actuel et la bibliothèque standard. Les saisies semi-automatique de `from ... import` sont proposées pour sous-modules et les packages secondaires ainsi que pour les membres de module. Cela comprend des fonctions, des classes ou des données exportées. Sélectionnez une des options pour ajouter l’instruction en haut du fichier après les autres importations, ou dans une instruction `from ... import` existante si le même module est déjà importé.

![Résultat de l’ajout d’une importation](~/python/media/code-refactor-add-import-2.png)

Visual Studio tente de filtrer les membres qui ne sont pas réellement définis dans un module, tels que les modules importés dans un autre module, mais qui ne sont pas des enfants du module à l’origine de l’importation. Par exemple, de nombreux modules utilisent `import sys` plutôt que `from xyz import sys`. Par conséquent, vous ne voyez pas de saisie semi-automatique pour l’importation de `sys` à partir d’autres modules, même s’il manque aux modules un membre `__all__` qui exclut `sys`.

De même, Visual Studio filtre les fonctions importées à partir d’autres modules ou de l’espace de noms intégré. Par exemple, si un module importe la fonction `settrace` à partir du module `sys`, vous pouvez théoriquement l’importer à partir de ce module. Toutefois, il est préférable d’utiliser directement `import settrace from sys` pour que Visual Studio propose spécifiquement cette instruction.

Enfin, si un élément doit être exclu en raison des règles ci-dessus, mais qu’il a d’autres valeurs qui peuvent être incluses (parce qu’une valeur a été affectée au nom dans le module, par exemple), Visual Studio exclut l’importation. Cela suppose que la valeur ne doit pas être exportée parce qu’elle est définie dans un autre module, et que, par conséquent, l’affectation supplémentaire est susceptible d’être une valeur factice qui n’est pas non plus exportée.

<a name="remove-imports"</a>
## <a name="remove-unused-imports"></a>Supprimer les importations inutilisées

Lors de l’écriture de code, il est facile de vous retrouver avec des instructions `import` concernant des modules qui ne sont pas utilisées du tout. Visual Studio analyse votre code et détermine automatiquement si une instruction `import` est nécessaire en regardant si les noms importés sont utilisés dans le cadre ci-dessous, où l’instruction s’exécute.

Cliquez avec le bouton droit n’importe où dans l’éditeur, puis sélectionnez **Remove Imports** (Supprimer les importations), qui vous propose des suppressions à partir de **toutes les portées** ou uniquement de la **portée actuelle** :

![Menu Supprimer les importations](~/python/media/code-refactor-remove-imports-1.png)

Ensuite, Visual Studio modifie le code en conséquence :

![Effet lié à la suppression des importations](~/python/media/code-refactor-remove-imports-2.png)

Notez que Visual Studio ne tient pas compte du flux de contrôle. L’utilisation d’un nom avant une instruction `import` sera traitée comme si le nom avait été utilisé. Visual Studio ignore également toutes les importations `from __future__`, ainsi que les importations effectuées au sein d’une définition de classe, ou à partir d’instructions `from ... import *`.
