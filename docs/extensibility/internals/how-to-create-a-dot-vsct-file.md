---
title: 'Comment: Créer un . Fichier Vsct (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708104"
---
# <a name="how-to-create-a-vsct-file"></a>Comment : Créer un fichier .vsct

Il existe plusieurs façons de créer un fichier de table de commande Visual Studio basé sur XML (*.vsct).*

- Vous pouvez créer un nouveau [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage dans le modèle de paquet.

- Vous pouvez utiliser le compilateur de configuration de table de commande basé sur XML, *Vsct.exe*, pour générer un fichier à partir d’un fichier *.ctc* existant.

- Vous pouvez utiliser *Vsct.exe* pour générer un fichier *.vsct* à partir d’un fichier *.cto* existant.

- Vous pouvez créer manuellement un nouveau fichier *.vsct.*

  Cet article explique comment créer manuellement un nouveau fichier *.vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier .vsct

1. Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Fichier**.

3. Dans le volet **Templates,** cliquez sur **le fichier XML,** puis cliquez sur **Open**.

4. Sur le menu **View,** cliquez sur **Propriétés** pour afficher les propriétés du fichier XML.

5. Dans la fenêtre **Propriétés,** cliquez sur le bouton **Parcourir** sur la propriété **Schemas.**

6. Dans la liste des schémas XSD, sélectionnez le schéma *vsct.xsd.* Si elle n’est pas dans la liste, cliquez sur **Ajouter** et ensuite trouver le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.

7. Dans le fichier XML, tapez *<CommandTable,* puis appuyez sur **Tab**. Fermez l’étiquette *>* en tapant .

    Cette action crée un fichier de base *.vsct.*

8. Remplissez les éléments du fichier XML que vous souhaitez ajouter, selon la [référence VSCT XML schéma](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, voir [Les fichiers Auteur .vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Comment : Créer un fichier .vsct à partir d’un fichier .ctc existant

Vous pouvez créer un fichier *.vsct* basé sur XML à partir d’un fichier source *.ctc* existant. Ainsi, vous pouvez tirer parti du nouveau format du compilateur (VSTC) de table de commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] XML.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Pour créer un fichier .vsct à partir d’un fichier .ctc

1. Obtenez une copie du langage Perl.

2. Obtenez une copie du script Perl *ConvertCTCToVSCT.pl*, généralement situé dans le * \<chemin d’installation Visual Studio SDK>-VisualStudioIntegration-Tools-bin* dossier.

3. Obtenez une copie du fichier source *.ctc* que vous souhaitez convertir.

4. Placez les fichiers dans le même répertoire.

5. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la fenêtre d’invite de commande, naviguez vers le répertoire.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    où *PkgCmd.ctc* est le nom du fichier *.ctc* et *PkgCmd.vsct* est le nom du fichier *.vsct* que vous voulez créer.

    Cette action crée un nouveau fichier source de table de commande *.vsct* XML. Vous pouvez compiler le fichier en utilisant *Vsct.exe*, le compilateur VSCT, comme vous le feriez n’importe quel autre fichier *.vsct.*

   > [!NOTE]
   > Vous pouvez améliorer la lisibilité du fichier *.vsct* en reformant les commentaires XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Comment : Créer un fichier .vsct à partir d’un fichier .cto existant

Vous pouvez créer un fichier *.vsct* basé sur XML à partir d’un fichier binaire *.cto* existant. Cela vous permet de tirer parti du nouveau format de compilateur de la table de commande. Ce processus fonctionne même si le fichier *.cto* a été compilé à partir d’un fichier *.ctc.* Vous pouvez modifier et compiler le fichier *.vsct* dans un autre fichier .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Pour créer un fichier .vsct à partir d’un fichier .cto

1. Obtenez des copies du fichier *.cto* et de son fichier *correspondant .ctsym.*

2. Placez les fichiers dans le même répertoire que le compilateur *vsct.exe.*

3. À l’invite de commande Visual Studio, allez à l’annuaire qui contient les fichiers *.cto* et *.ctsym.*

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     où \<\> ctofilename est le nom du fichier *.cto,* \<vsctfilename\> est le nom du fichier\> *.vsct* que vous voulez créer, et \<symfilename est le nom du fichier *.ctsym.*

     Ce processus crée un nouveau fichier de compilateur de table de commande *.vsct* XML. Vous pouvez modifier et compiler le fichier avec *vsct.exe*, le compilateur vsct, comme vous le feriez n’importe quel autre fichier *.vsct.*

## <a name="compile-the-code"></a>Compiler le code
 Le simple fait d’ajouter un fichier *.vsct* à un projet ne le fait pas compiler. Vous devez l’incorporer dans le processus de construction.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier .vsct à la compilation du projet

1. Ouvrez votre dossier de projet dans l’éditeur. Si le projet est chargé, vous devez le décharger en premier.

2. Ajoutez un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) qui contient un `VSCTCompile` élément, comme indiqué dans l’exemple suivant.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     L’élément `ResourceName` doit toujours `Menus.ctmenu`être réglé à .

3. Si votre projet contient un fichier *.resx,* ajoutez un `EmbeddedResource` élément qui contient un `MergeWithCTO` élément, comme indiqué dans l’exemple suivant :

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Cette majoration doit `ItemGroup` aller à l’intérieur de l’élément qui contient des ressources intégrées.

4. Ouvrez le fichier de paquet, généralement nommé * \<ProjectName\>Package.cs* ou * \<ProjectName\>Package.vb*, dans l’éditeur.

5. Ajoutez `ProvideMenuResource` un attribut à la classe de paquet, comme indiqué dans l’exemple suivant.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     La première valeur de paramètre `ResourceName` doit correspondre à la valeur de l’attribut que vous avez défini dans le fichier du projet.

## <a name="see-also"></a>Voir aussi
- [Auteur .vsct fichiers](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML référence schéma](../../extensibility/vsct-xml-schema-reference.md)
