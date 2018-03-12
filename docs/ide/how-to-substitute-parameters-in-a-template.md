---
title: "Ajouter des paramètres de nom à des modèles de projet et d’élément dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Guide pratique pour substituer des paramètres dans un modèle

Les paramètres de modèle vous permettent de remplacer des identificateurs, comme des noms de classes et des espaces de noms, pendant la création d’un fichier à partir d’un modèle. Vous pouvez ajouter des paramètres de modèle à des modèles existants ou créer vos propres modèles avec des paramètres de modèle.

Les paramètres d’un modèle s’écrivent au format $*parameter*$. Pour obtenir la liste complète des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).

La section suivante vous montre comment modifier un modèle pour remplacer le nom d’un espace de noms par le « nom du projet sécurisé ».

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Pour utiliser un paramètre pour remplacer le nom de l’espace de noms

1. Ajoutez le paramètre dans l'un ou plusieurs des fichiers de code du modèle. Exemple :

    ```csharp
    namespace $safeprojectname$
    ```

1. Dans le fichier .vstemplate du modèle, localisez l'élément `ProjectItem` qui inclut ce fichier.

1. Affectez à l’attribut `ReplaceParameters` la valeur `true` pour l’élément `ProjectItem` :

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Voir aussi

[Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)  
[Paramètres de modèle](../ide/template-parameters.md)  
[Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Élément ProjectItem (modèles d'élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)