---
title: Ajouter des paramètres de nom à des modèles de projet et d’élément
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591409"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Guide pratique pour substituer des paramètres dans un modèle

Les paramètres de modèle vous permettent de remplacer des identificateurs, comme des noms de classes et des espaces de noms, pendant la création d’un fichier à partir d’un modèle. Vous pouvez ajouter des paramètres de modèle à des modèles existants ou créer vos propres modèles avec des paramètres de modèle.

Les paramètres d’un modèle s’écrivent au format $*parameter*$. Pour obtenir la liste complète des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).

La section suivante vous montre comment modifier un modèle pour remplacer le nom d’un espace de noms par le « nom du projet sécurisé ».

## <a name="example---namespace-name"></a>Exemple : nom d’espace de noms

1. Ajoutez le paramètre dans l'un ou plusieurs des fichiers de code du modèle. Par exemple :

    ```csharp
    namespace $safeprojectname$
    ```

1. Dans le fichier *.vstemplate* du modèle, localisez l’élément `ProjectItem` qui inclut ce fichier.

1. Affectez à l’attribut `ReplaceParameters` la valeur `true` pour l’élément `ProjectItem` :

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem, élément (modèles d’élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
