---
title: 'Procédure : Supprimer les avertissements du compilateur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 994b29fb4592d55a04389896ee9db8848dceda67
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695385"
---
# <a name="how-to-suppress-compiler-warnings"></a>Procédure : Supprimer les avertissements du compilateur

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez « nettoyer » un journal de génération en spécifiant un ou plusieurs types d’avertissements du compilateur que vous ne souhaitez pas inclure. Par exemple, vous pouvez utiliser cette technique pour passer en revue uniquement certaines des informations générées automatiquement quand vous affectez la valeur Diagnostic, Détaillé ou Normal au niveau de détail du journal de génération. Pour plus d’informations sur le niveau de détail, consultez [Guide pratique pour Afficher, enregistrer et configurer les fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Pour supprimer des avertissements spécifiques pour Visual C# ou F\#

1. Dans l’**Explorateur de solutions**, choisissez le projet dans lequel vous souhaitez supprimer les avertissements.

2. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.

3. Choisissez la page **Générer**.

4. Dans la zone **Supprimer les avertissements**, spécifiez les codes d’erreur des avertissements que vous souhaitez supprimer, séparés par des points-virgules, puis régénérez la solution.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Pour supprimer des avertissements spécifiques pour Visual C++

1. Dans l’**Explorateur de solutions**, choisissez le projet ou fichier source dans lequel vous souhaitez supprimer les avertissements.

2. Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.

3. Choisissez la catégorie **Propriétés de configuration**, la catégorie **C/C++**, puis la page **Avancé**.

4. Effectuez l’une des opérations suivantes :

    - Dans la zone **Désactivation des avertissements spécifiques**, spécifiez les codes d’erreur des avertissements que vous souhaitez supprimer, séparés par des points-virgules.

    - Dans la zone **Désactivation des avertissements spécifiques**, choisissez **Edition** pour afficher davantage d’options.

5. Choisissez le bouton **OK**, puis régénérez la solution.

## <a name="suppressing-warnings-for-visual-basic"></a>Suppression des avertissements pour Visual Basic

Vous pouvez masquer des avertissements spécifiques du compilateur pour Visual Basic en modifiant le fichier .vbproj du projet. Vous pouvez également utiliser la [Page Compiler, Concepteur de projets](../ide/reference/compile-page-project-designer-visual-basic.md) pour supprimer les avertissements par catégorie. Pour plus d’informations, consultez [Configuration d’avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Pour supprimer des avertissements spécifiques pour Visual Basic

1. Dans l’**Explorateur de solutions**, choisissez le projet dans lequel vous souhaitez supprimer les avertissements.

2. Dans la barre de menus, choisissez **Projet**, **Décharger le projet**.

3. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Modifier**_nom_projet_**.vbproj**.

    Le fichier projet s’ouvre dans l’éditeur de code.

4. Recherchez l’élément `<NoWarn></NoWarn>` dans la configuration de build avec laquelle vous générez.

    L’exemple suivant montre l’élément `<NoWarn></NoWarn>` en gras pour la configuration de build Debug sur une plateforme x86 :

   ```xml
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
       <PlatformTarget>x86</PlatformTarget>
       <DebugSymbols>true</DebugSymbols>
       <DebugType>full</DebugType>
       <Optimize>false</Optimize>
       <OutputPath>bin\Debug\</OutputPath>
       <DefineDebug>true</DefineDebug>
       <DefineTrace>true</DefineTrace>
       <ErrorReport>prompt</ErrorReport>
       <NoWarn></NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

5. Ajoutez un ou plusieurs numéros d’avertissement comme valeur de l’élément `<NoWarn>`. Si vous spécifiez plusieurs numéros d’avertissement, séparez-les par des virgules, comme illustré ci-dessous.

   ```xml
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

6. Enregistrez les modifications dans le fichier .vbproj.

7. Dans la barre de menus, choisissez **Projet**, **Recharger le projet**.

8. Dans la barre de menus, choisissez **Générer**, **Régénérer la solution**.

    La fenêtre **Sortie** n’affiche plus les avertissements que vous avez spécifiés.

   Pour plus d’informations, consultez [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Génération d’une application](../ide/walkthrough-building-an-application.md)
- [Guide pratique pour afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
