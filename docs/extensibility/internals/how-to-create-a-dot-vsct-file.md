---
title: 'Comment : créer un. Fichier vsct | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409097"
---
# <a name="how-to-create-a-vsct-file"></a>Comment : créer un fichier. vsct

Il existe plusieurs façons de créer un fichier de configuration de table de commandes Visual Studio ( *. vsct*) basé sur XML.

- Vous pouvez créer un nouveau VSPackage dans le modèle de package [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Vous pouvez utiliser le compilateur de configuration de table de commandes basé sur XML, *vsct. exe*, pour générer un fichier à partir d’un fichier *. CTC* existant.

- Vous pouvez utiliser *vsct. exe* pour générer un fichier *. vsct* à partir d’un fichier *. Directeur* de la génération.

- Vous pouvez créer manuellement un nouveau fichier *. vsct* .

  Cet article explique comment créer manuellement un nouveau fichier *. vsct* .

### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier. vsct

1. Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Fichier**.

3. Dans le volet **modèles** , cliquez sur **fichier XML** , puis sur **ouvrir**.

4. Dans le menu **affichage** , cliquez sur **Propriétés** pour afficher les propriétés du fichier XML.

5. Dans la fenêtre **Propriétés** , cliquez sur le bouton **Parcourir** de la propriété **schémas** .

6. Dans la liste des schémas XSD, sélectionnez le schéma *vsct. xsd* . S’il ne figure pas dans la liste, cliquez sur **Ajouter** , puis recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.

7. Dans le fichier XML, tapez *< CommandTable* , puis appuyez sur la touche **Tab**. Fermez la balise en tapant *>* .

    Cette action crée un fichier *. vsct* de base.

8. Renseignez les éléments du fichier XML que vous souhaitez ajouter, en fonction de la [référence de schéma XML vsct](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, consultez [création de fichiers. vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Comment : créer un fichier. vsct à partir d’un fichier. CTC existant

Vous pouvez créer un fichier *. vsct* XML à partir d’un fichier source de table de commandes *. CTC* existant. Ainsi, vous pouvez tirer parti du nouveau format du compilateur (VSTC) de table de commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] XML.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Pour créer un fichier .vsct à partir d’un fichier .ctc

1. Obtenez une copie du langage Perl.

2. Obtenez une copie du script perl *ConvertCTCToVSCT.pl*, généralement situé dans le *\<chemin d’installation du kit de développement logiciel Visual Studio > dossier \VisualStudioIntegration\Tools\bin* .

3. Obtenez une copie du fichier source *. CTC* que vous souhaitez convertir.

4. Placez les fichiers dans le même répertoire.

5. Dans la fenêtre d’invite de commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], accédez au répertoire.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    où *PkgCmd. CTC* est le nom du fichier *. CTC* et *PkgCmd. vsct* est le nom du fichier *. vsct* que vous souhaitez créer.

    Cette action crée un fichier source de table de commandes XML *. vsct* . Vous pouvez compiler le fichier à l’aide de *vsct. exe*, le compilateur vsct, comme vous le feriez pour tout autre fichier *. vsct* .

   > [!NOTE]
   > Vous pouvez améliorer la lisibilité du fichier *. vsct* en reformatant les commentaires XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Comment : créer un fichier. vsct à partir d’un fichier. directeur de la configuration

Vous pouvez créer un fichier *. vsct* XML à partir d’un fichier *. directeur technique* existant. Cela vous permet de tirer parti du nouveau format de compilateur de la table de commande. Ce processus fonctionne même si le fichier *. Directeur* de la compilation a été compilé à partir d’un fichier *. CTC* . Vous pouvez modifier et compiler le fichier *. vsct* dans un autre fichier. directeur technique.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Pour créer un fichier .vsct à partir d’un fichier .cto

1. Obtenez des copies du fichier *. Directeur* et du fichier *. ctsym* correspondant.

2. Placez les fichiers dans le même répertoire que le compilateur *vsct. exe* .

3. À l’invite de commandes Visual Studio, accédez au répertoire qui contient les fichiers *. Directeur* et. *ctsym* .

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     où \<ctofilename\> est le nom du fichier *. directeur technique* , \<vsctfilename\> est le nom du fichier *. vsct* que vous souhaitez créer, et \<symfilename\> est le nom du fichier *. ctsym* .

     Ce processus crée un fichier de compilateur de table de commandes XML *. vsct* . Vous pouvez modifier et compiler le fichier avec *vsct. exe*, le compilateur vsct, comme vous le feriez pour tout autre fichier *. vsct* .

## <a name="compile-the-code"></a>Compiler le code
 Le simple ajout d’un fichier *. vsct* à un projet ne provoque pas sa compilation. Vous devez l’incorporer dans le processus de génération.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier. vsct à la compilation de projet

1. Ouvrez votre fichier projet dans l’éditeur. Si le projet est chargé, vous devez d’abord le décharger.

2. Ajoutez un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) contenant un élément `VSCTCompile`, comme indiqué dans l’exemple suivant.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     L’élément `ResourceName` doit toujours être défini sur `Menus.ctmenu`.

3. Si votre projet contient un fichier *. resx* , ajoutez un élément `EmbeddedResource` qui contient un élément `MergeWithCTO`, comme indiqué dans l’exemple suivant :

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Ce balisage doit se trouver à l’intérieur de l’élément `ItemGroup` qui contient des ressources incorporées.

4. Ouvrez le fichier de package, généralement nommé *\<projectname\>package.cs* ou *\<ProjectName\>package. vb*, dans l’éditeur.

5. Ajoutez un attribut `ProvideMenuResource` à la classe package, comme indiqué dans l’exemple suivant.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     La première valeur de paramètre doit correspondre à la valeur de l’attribut `ResourceName` que vous avez défini dans le fichier projet.

## <a name="see-also"></a>Voir aussi
- [Fichiers Author. vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)