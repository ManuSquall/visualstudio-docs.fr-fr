---
title: "Cr&#233;ation de mod&#232;les de projets et d&#39;&#233;l&#233;ments personnalis&#233;s dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles d'élément, à propos des modèles d'élément"
  - "modèles de projet (Visual Studio), à propos des modèles de projet"
  - "modèles (Visual Studio), à propos des modèles"
  - "modèles (Visual Studio), élément"
  - "modèles (Visual Studio), projets"
  - "modèles Visual Studio, à propos des modèles"
  - "modèles Visual Studio, élément"
  - "modèles Visual Studio, projet"
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Cr&#233;ation de mod&#232;les de projets et d&#39;&#233;l&#233;ments personnalis&#233;s dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les modèles de projet et d'élément [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu'ils peuvent utiliser pour leurs propres besoins.  
  
## Modèles Visual Studio  
 L'installation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments.  Les modèles d'application Windows Forms et de bibliothèque de classes [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], disponibles dans la boîte de dialogue **Nouveau projet**, sont des exemples de modèles de projet.  Les modèles d'élément installés sont disponibles dans la boîte de dialogue **Ajouter un nouvel élément** et incluent des éléments tels que des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style.  
  
 Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants.  Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut.  Les modèles d'élément peuvent être aussi simples qu'un unique fichier vide doté de l'extension de nom de fichier appropriée, ou aussi complexes qu'un élément à plusieurs fichiers contenant, par exemple, des fichiers de code source avec un code stub, des fichiers d'informations sur le concepteur et des ressources incorporées.  
  
 Outre les modèles installés présents dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, vous pouvez créer vos propres modèles ou télécharger et utiliser des modèles créés par la communauté.  Pour plus d'informations, consultez [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md).  
  
## Contenu d'un modèle  
 Tous les modèles de projet et d'élément, qu'ils soient installés avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus.  Tous les modèles contiennent les éléments suivants :  
  
-   Les fichiers à créer lors de l'utilisation du modèle.  Ce sont les fichiers de code source, les ressources incorporées, les fichiers projet, etc.  
  
-   Un fichier .vstemplate.  Ce fichier contient les métadonnées qui fournissent à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] les informations nécessaires pour afficher le modèle dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, ainsi que pour créer un projet ou un élément à partir du modèle.  Pour plus d'informations sur les fichiers .vstemplate, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
 Lorsque ces fichiers sont compressés dans un fichier .zip et placés dans le dossier approprié, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] les affiche automatiquement.  Les modèles de projet s'affichent dans la section **Mes modèles** de la boîte de dialogue **Nouveau projet** et les modèles d'élément s'affichent dans la boîte de dialogue **Ajouter un nouvel élément**.  Pour plus d'informations sur les dossiers de modèles, consultez [Comment : localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Starter Kits  
 Les Starter Kits sont des modèles améliorés qui peuvent être partagés avec d'autres membres de la communauté.  Un Starter Kit inclut, parmi d'autres ressources, des exemples de code compilables et une documentation pour aider les utilisateurs à découvrir de nouveaux outils et techniques de programmation tout en générant des applications utiles et réelles.  Le contenu et les procédures de base sont identiques, qu'il s'agisse de Starter Kits ou de modèles.  Pour plus d'informations, consultez [Comment : créer des Starter Kits](../ide/how-to-create-starter-kits.md).  
  
## Voir aussi  
 [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md)   
 [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [Comment : créer des Starter Kits](../ide/how-to-create-starter-kits.md)