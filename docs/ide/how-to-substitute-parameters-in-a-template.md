---
title: "Comment&#160;: substituer des param&#232;tres dans un mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres de modèles, substituer"
  - "modèles Visual Studio, utiliser des paramètres"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: substituer des param&#232;tres dans un mod&#232;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez remplacer les paramètres d'un modèle, tels que les noms de classes et les espaces de noms, lors de la création d'un fichier basé sur ce modèle.  Pour avoir une liste exhaustive des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
## Procédure  
 Vous pouvez remplacer des paramètres dans les fichiers d'un modèle chaque fois qu'un projet basé sur ce modèle est créé.  Cette procédure explique comment créer un modèle qui remplace le nom d'un espace de noms par le nom du projet sécurisé quand un projet est créé avec le modèle.  
  
#### Pour remplacer le nom de l'espace de noms par le nom du projet à l'aide d'un paramètre  
  
1.  Ajoutez le paramètre dans l'un ou plusieurs des fichiers de code du modèle.  Exemple :  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Les paramètres d'un modèle s'écrivent selon le format $*parameter*$.  
  
2.  Dans le fichier .vstemplate du modèle, localisez l'élément `ProjectItem` qui inclut ce fichier.  
  
3.  Définissez l'attribut `ReplaceParameters` à la valeur `true` pour l'élément `ProjectItem`.  Exemple :  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem, élément \(modèles d'élément Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)