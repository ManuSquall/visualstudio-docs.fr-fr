---
title: Guide pratique pour substituer des paramètres dans un modèle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670659"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Comment : substituer des paramètres dans un modèle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez remplacer les paramètres d'un modèle, tels que les noms de classes et les espaces de noms, lors de la création d'un fichier basé sur ce modèle. Pour obtenir une liste exhaustive des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).

## <a name="procedure"></a>Procédure
 Vous pouvez remplacer des paramètres dans les fichiers d'un modèle chaque fois qu'un projet basé sur ce modèle est créé. Cette procédure explique comment créer un modèle qui remplace le nom d'un espace de noms par le nom du projet sécurisé quand un projet est créé avec le modèle.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Pour remplacer le nom de l'espace de noms par le nom du projet à l'aide d'un paramètre

1. Ajoutez le paramètre dans l'un ou plusieurs des fichiers de code du modèle. Par exemple :

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Les paramètres d’un modèle s’écrivent au format $*parameter*$.

2. Dans le fichier .vstemplate du modèle, localisez l'élément `ProjectItem` qui inclut ce fichier.

3. Définissez l'attribut `ReplaceParameters` à la valeur `true` pour l'élément `ProjectItem`. Par exemple :

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Voir aussi
 [Création de modèles de modèles de projet et d’élément paramètres de](../ide/creating-project-and-item-templates.md) [modèle](../ide/template-parameters.md) [Visual Studio référence du schéma de modèle](../extensibility/visual-studio-template-schema-reference.md) [ProjectItem, élément (modèles d’élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
