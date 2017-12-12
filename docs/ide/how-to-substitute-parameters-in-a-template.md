---
title: "Guide pratique pour substituer des paramètres dans un modèle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e13e704502443c371021c515c7a9578497f829
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Guide pratique pour substituer des paramètres dans un modèle
Vous pouvez remplacer les paramètres d'un modèle, tels que les noms de classes et les espaces de noms, lors de la création d'un fichier basé sur ce modèle. Pour obtenir une liste exhaustive des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procédure  
 Vous pouvez remplacer des paramètres dans les fichiers d'un modèle chaque fois qu'un projet basé sur ce modèle est créé. Cette procédure explique comment créer un modèle qui remplace le nom d'un espace de noms par le nom du projet sécurisé quand un projet est créé avec le modèle.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Pour remplacer le nom de l'espace de noms par le nom du projet à l'aide d'un paramètre  
  
1.  Ajoutez le paramètre dans l'un ou plusieurs des fichiers de code du modèle. Exemple :  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Les paramètres d’un modèle s’écrivent au format $*parameter*$.  
  
2.  Dans le fichier .vstemplate du modèle, localisez l'élément `ProjectItem` qui inclut ce fichier.  
  
3.  Définissez l'attribut `ReplaceParameters` à la valeur `true` pour l'élément `ProjectItem`. Exemple :  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Élément ProjectItem (modèles d'élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)