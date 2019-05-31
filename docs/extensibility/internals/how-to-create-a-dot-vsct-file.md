---
title: 'Procédure : Créer un. Fichier VSCT | Microsoft Docs'
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
ms.openlocfilehash: 95b085975a86db248517751fde7bd88c8bc2e35e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328759"
---
# <a name="how-to-create-a-vsct-file"></a>Procédure : Créer un fichier .vsct

Il existe plusieurs façons de créer une configuration de table de commande basé sur XML Visual Studio ( *.vsct*) fichier.

- Vous pouvez créer un nouveau VSPackage s’affiche dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de package.

- Vous pouvez utiliser le compilateur de configuration de table de commande basé sur XML, *Vsct.exe*, pour générer un fichier à partir d’un existant *.ctc* fichier.

- Vous pouvez utiliser *Vsct.exe* pour générer un *.vsct* fichier depuis une *.cto* fichier.

- Vous pouvez créer manuellement un nouveau *.vsct* fichier.

  Cet article explique comment créer manuellement un nouveau *.vsct* fichier.

### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier .vsct

1. Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Sur le **fichier** menu, pointez sur **New**, puis cliquez sur **fichier**.

3. Dans le **modèles** volet, cliquez sur **fichier XML** puis cliquez sur **Open**.

4. Sur le **vue** menu, cliquez sur **propriétés** pour afficher les propriétés du fichier XML.

5. Dans le **propriétés** fenêtre, cliquez sur le **Parcourir** bouton sur le **schémas** propriété.

6. Dans la liste des schémas XSD, sélectionnez le *vsct.xsd* schéma. Si elle n’est pas dans la liste, cliquez sur **ajouter** , puis recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.

7. Dans le fichier XML, tapez *< CommandTable* , puis appuyez sur **onglet**. Fermer la balise en tapant *>* .

    Cette action crée un base *.vsct* fichier.

8. Renseignez les éléments du fichier XML que vous souhaitez ajouter, selon le [référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, consultez [créer des fichiers .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procédure : Créer un fichier .vsct à partir d’un fichier .ctc existant

Vous pouvez créer une base de XML *.vsct* fichier à partir d’une table existante de la commande *.ctc* fichier source. Ainsi, vous pouvez tirer parti du nouveau format du compilateur (VSTC) de table de commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] XML.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Pour créer un fichier .vsct à partir d’un fichier .ctc

1. Obtenez une copie du langage Perl.

2. Obtenir une copie du script Perl *ConvertCTCToVSCT.pl*, généralement situé dans le  *\<chemin d’installation de Visual Studio SDK > \VisualStudioIntegration\Tools\bin* dossier.

3. Obtenir une copie de la *.ctc* fichier source que vous souhaitez convertir.

4. Placez les fichiers dans le même répertoire.

5. Dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fenêtre d’invite de commandes, accédez au répertoire.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    où *PkgCmd.ctc* est le nom de la *.ctc* fichier et *PkgCmd.vsct* est le nom de la *.vsct* fichier que vous souhaitez créer.

    Cette action crée un nouveau *.vsct* fichier de source de table de commande XML. Vous pouvez compiler le fichier à l’aide de *Vsct.exe*, le compilateur VSCT, comme vous le feriez pour n’importe quel autre *.vsct* fichier.

   > [!NOTE]
   > Vous pouvez améliorer la lisibilité de la *.vsct* fichier en reformatant les commentaires XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procédure : Créer un fichier .vsct à partir d’un fichier .cto existant

Vous pouvez créer une base de XML *.vsct* fichier à partir d’un fichier binaire existant *.cto* fichier. Cela vous permet de tirer parti du nouveau format de compilateur de la table de commande. Ce processus fonctionne même si le *.cto* fichier a été compilé à partir d’un *.ctc* fichier. Vous pouvez modifier et compiler le *.vsct* fichier dans un autre fichier .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Pour créer un fichier .vsct à partir d’un fichier .cto

1. Obtenir des copies de la *.cto* fichier et son *.ctsym* fichier.

2. Placez les fichiers dans le même répertoire que le *vsct.exe* compilateur.

3. À l’invite de commandes Visual Studio, accédez au répertoire qui contient le *.cto* et *.ctsym* fichiers.

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     où \<ctofilename\> est le nom de la *.cto* fichier, \<vsctfilename\> est le nom de la *.vsct* fichier que vous souhaitez créer et \<symfilename\> est le nom de la *.ctsym* fichier.

     Ce processus crée un nouveau *.vsct* fichier du compilateur de table de commande XML. Vous pouvez modifier et compiler le fichier avec *vsct.exe*, le compilateur vsct, comme vous le feriez pour n’importe quel autre *.vsct* fichier.

## <a name="compile-the-code"></a>Compiler le code
 Simplement en ajoutant un *.vsct* fichier à un projet n’entraîne pas se compiler. Vous devez l’incorporer dans le processus de génération.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier .vsct à la compilation du projet

1. Ouvrez votre fichier projet dans l’éditeur. Si le projet est chargé, vous devez tout d’abord le décharger.

2. Ajouter un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) qui contient un `VSCTCompile` élément, comme indiqué dans l’exemple suivant.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Le `ResourceName` élément doit toujours être défini sur `Menus.ctmenu`.

3. Si votre projet contient un *.resx* , ajoutez un `EmbeddedResource` élément contenant un `MergeWithCTO` élément, comme indiqué dans l’exemple suivant :

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Ce balisage doit passer à l’intérieur du `ItemGroup` élément qui contient des ressources incorporées.

4. Ouvrez le fichier de package, généralement nommé  *\<nom_projet\>Package.cs* ou  *\<nom_projet\>Package.vb*, dans l’éditeur.

5. Ajouter un `ProvideMenuResource` d’attribut à la classe de package, comme illustré dans l’exemple suivant.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     La première valeur du paramètre doit correspondre à la valeur de la `ResourceName` attribut vous défini dans le fichier projet.

## <a name="see-also"></a>Voir aussi
- [Fichiers .vsct auteur](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)