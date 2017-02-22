---
title: "Comment&#160;: supprimer des avertissements du compilateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Comment&#160;: supprimer des avertissements du compilateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez declutter un journal de génération en spécifiant un ou plusieurs types d'avertissements du compilateur que vous ne voulez pas pour contenir.  Par exemple, vous pouvez utiliser cette technique d'en tester mais pas toutes les informations générées automatiquement lorsque vous définissez les commentaires du journal de génération à normal, détaillé, ou diagnostic.  Pour plus d'informations sur les commentaires, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### Pour supprimer des avertissements spécifiques à Visual C ou \(\#  
  
1.  Dans **Explorateur de solutions**, sélectionnez le projet dans lequel vous souhaitez supprimer les avertissements.  
  
2.  Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.  
  
3.  Sélectionnez la page **Build** .  
  
4.  Dans la zone **Supprimer les avertissements**, spécifiez les codes d'erreur des avertissements à supprimer, séparés par des points\-virgules, puis régénérez la solution.  
  
### Pour supprimer des avertissements spécifiques pour Visual C\+\+  
  
1.  Dans **Explorateur de solutions**, sélectionnez le projet ou le fichier source dans lequel vous souhaitez supprimer les avertissements.  
  
2.  Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.  
  
3.  Sélectionnez la catégorie **Propriétés de configuration**, sélectionnez la catégorie **C\/C\+\+**, puis sélectionnez la page **Avancé** .  
  
4.  Effectuez l'une des étapes suivantes :  
  
    -   Dans la zone **Désactivation des avertissements spécifiques**, spécifiez les codes d'erreur des avertissements à supprimer, séparés par un point\-virgule.  
  
    -   Dans la zone **Désactivation des avertissements spécifiques**, choisissez **Modifier** pour présenter plus d'options.  
  
5.  Choisissez le bouton **OK**, puis régénérez la solution.  
  
## Supprimer les avertissements pour Visual Basic  
 Vous pouvez masquer les avertissements du compilateur spécifiques pour Visual Basic en modifiant le fichier .vbproj pour le projet.  Vous pouvez également utiliser [Page de compilation, Concepteur de projets](../ide/reference/compile-page-project-designer-visual-basic.md) pour supprimer des avertissements par catégorie.  Pour plus d'informations, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### Pour supprimer des avertissements spécifiques pour Visual Basic  
  
1.  Dans **Explorateur de solutions**, sélectionnez le projet dans lequel vous souhaitez supprimer les avertissements.  
  
2.  Dans la barre de menus, sélectionnez **Projet**, **Décharger le projet**.  
  
3.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Modifier***Nomprojet***.vbproj**.  
  
     Le fichier projet est ouvert dans l'éditeur de code.  
  
4.  Localisez l'élément d' `<NoWarn></NoWarn>` dans la configuration de build avec laquelle vous générez.  
  
     L'exemple suivant illustre l'élément d' `<NoWarn></NoWarn>` en gras pour la configuration de build debug sur une plateforme x86 :  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Ajoutez un ou plusieurs numéros d'avertissement comme valeur de l'élément d' `<NoWarn>` .  Si vous spécifiez plusieurs numéros d'avertissement, séparez\-les par une virgule, comme le montre l'exemple suivant.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Enregistrez les modifications apportées au fichier .vbproj.  
  
7.  Dans la barre de menus, sélectionnez **Projet**, **Recharger le projet**.  
  
8.  Dans la barre de menus, sélectionnez **Build**, **Régénérer la solution**.  
  
     La fenêtre **Sortie** ne vous indique plus les avertissements ces avez spécifié.  
  
 Pour plus d'informations, consultez [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## Voir aussi  
 [Procédure pas à pas : génération d'une application](../ide/walkthrough-building-an-application.md)   
 [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)