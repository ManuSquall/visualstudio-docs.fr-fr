---
title: "Mod&#232;le de projet VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "déployer des packages"
  - "publier une extension"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Mod&#232;le de projet VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le modèle de projet VSIX pour encapsuler une ou plusieurs extensions de Visual Studio dans un projet VSIX et puis publier le package sur le [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web.  
  
 Déploiement VSIX prend en charge les VSPackages, assemblys, MEF composants, modèles de projet, les modèles d'élément, des contrôles de boîte à outils et types d'extension personnalisée.  
  
> [!NOTE]
>  Pour utiliser des projets VSIX, vous devez installer le Kit de développement Visual Studio. Pour plus d'informations sur le Kit de développement Visual Studio, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Où trouver le modèle de projet VSIX  
 Le modèle de projet VSIX est disponible dans le **Nouveau projet** boîte de dialogue. Développez le **Visual Basic** nœud ou **Visual C\#** nœud, puis choisissez **extensibilité**.  
  
> [!TIP]
>  Vous devez vous assurer que .NET Framework 4.5 ou une version ultérieure est spécifié dans la liste déroulante en haut de la **Nouveau projet** boîte de dialogue.  
  
## Utilisation du modèle de projet VSIX  
 Le modèle de projet VSIX a deux utilisations principales :  
  
-   Pour déployer des modèles de projet, les modèles d'élément et d'autres extensions qui n'ont pas déjà la prise en charge de l'extension VSIX.  
  
-   Pour inclure les sorties de plusieurs extensions dans le package de déploiement.  
  
 Vous n'avez pas à utiliser le modèle de projet VSIX pour déployer des packages VS ou autres types d'extensions qui ont déjà VSIX prennent en charge.  
  
## Empaquetage d'une Extension dans un projet VSIX vide  
 Vous pouvez empaqueter une extension existante ou une extension qui ne dispose pas encore VSIX prend en charge, en l'intégrant à un projet VSIX vide. L'extension à encapsuler doit être d'un type qui est pris en charge par le [schéma VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### Pour empaqueter une extension à l'aide d'un projet VSIX  
  
1.  Générer les projets qui constituent votre extension.  
  
2.  Créez un projet VSIX à l'aide de la **projet VSIX** modèle.  
  
     Source.extension.vsixmanifest s'ouvre dans **Concepteur de manifeste**.  
  
3.  Sur le **actifs** choisir le **nouveau** bouton.  
  
     Le **Ajouter un nouveau composant** boîte de dialogue s'affiche.  
  
4.  Dans le **Type** choisissez le type d'extension à ajouter.  
  
5.  Pour ajouter un élément d'extension ou le contenu qui est inclus dans la solution actuelle \(par exemple, un modèle d'élément ou un assembly compilé\), procédez comme suit :  
  
    1.  Dans le **Source** sélectionnez **un projet dans la solution actuelle**.  
  
    2.  Dans le **projet** sélectionnez le nom de l'extension.  
  
    3.  Dans le **Embed dans ce dossier** entrez le nom d'un dossier dans lequel incorporer l'élément, puis choisissez le **OK** bouton.  
  
6.  Pour ajouter une extension ou un élément de contenu qui n'est pas inclus dans la solution actuelle, procédez comme suit :  
  
    1.  Dans le **Source** zone de liste, choisissez **fichier sur le système de fichiers**.  
  
    2.  Dans le **chemin d'accès** champ, entrez le chemin d'accès complet au fichier d'extension compilé ou compressés ou utilisez le **Parcourir** bouton pour rechercher le fichier.  
  
    3.  Dans le **Embed dans ce dossier** entrez le nom d'un dossier dans lequel incorporer l'élément, puis choisissez le **OK** bouton.  
  
7.  Si vous souhaitez que votre package pour inclure des extensions supplémentaires, ajoutez\-les de la même manière.  
  
8.  Générez la solution.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un fichier .vsix contenant un fichier manifeste VSIX, un fichier \[Content\_Types\] .xml et toutes les ressources de l'extension que vous avez ajouté au projet.  
  
## Voir aussi  
 [Référence du schéma 2.0 Extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)