---
title: Localisation des commandes de menu (fr) Microsoft Docs
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702946"
---
# <a name="localize-menu-commands"></a>Localiser les commandes de menu

Vous pouvez fournir du texte localisé pour les commandes de menu et de barre d’outils en créant des fichiers *.vsct* localisés et des fichiers *.resx localisés* pour votre VSPackage, puis en mettant à jour les fichiers du projet pour intégrer les modifications.

Pour plus d’informations sur la façon de localiser l’expérience d’installation, voir [Les forfaits LOCALize VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localiser les noms de commande

Dans VSPackages, les commandes de menu et les boutons de barre d’outils sont définis dans le fichier *.vsct.*

1. Dans **Solution Explorer**, changer le nom du fichier *.vsct* de *filename.vsct* à *filename.en-US.vsct*.

2. Faites une copie de *filename.en-US.vsct* pour chaque langue localisée.

    Nommez chaque *nom de fichier de copie. Local.vsct*, où *'Local'* est un nom de culture particulier. Pour une liste des valeurs de nom de culture, voir [local IDs attribué par Microsoft](/windows/uwp/publish/supported-languages).

    Ces *noms de fichiers. Les fichiers Locale.vsct* contiendront le texte du menu localisé pour votre forfait.

3. Ouvrez chaque *nom de fichier. Fichier Local.vsct* pour localiser le texte.

   1. Modifier les valeurs de l’élément [ButtonText,](../extensibility/buttontext-element.md) le cas échéant pour la langue particulière.

   2. Si vous fournissez des icônes localisées, modifiez les valeurs [Bitmap](../extensibility/bitmap-element.md) pour pointer vers les fichiers cibles.

      L’exemple suivant montre le texte bouton anglais et espagnol pour une commande d’ouvrir une fenêtre d’outil Family Tree Explorer.

      [*FamilyTree.fr-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Localiser d’autres ressources textuelles

Les ressources textuelles autres que les noms de commande sont définies dans les fichiers ressources *(resx).*

1. Rebaptiser *VSPackage.resx* à *VSPackage.fr-US.resx*.

2. Faites une copie du fichier *VSPackage.en-US.resx* pour chaque langue localisée.

     Nommez chaque copie *VSPackage. Local.resx*, où *'Local'* est un nom de culture particulier.

3. Rebaptiser *Resources.resx* à *Resources.fr-US.resx*.

4. Faites une copie du fichier *Resources.en-US.resx* pour chaque langue localisée.

     Nommez chaque exemplaire *Ressources. Local.resx*, où *'Local'* est un nom de culture particulier.

5. Ouvrez chaque fichier *.resx* pour modifier les valeurs de chaîne, le cas échéant pour la langue et la culture particulières. L’exemple suivant montre la définition de ressources localisée pour la barre de titre d’une fenêtre d’outils.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Intégrer des ressources localisées dans le projet

Vous devez modifier le *fichier assemblyinfo.cs* et le fichier du projet pour intégrer les ressources localisées.

1. Du nœud **Propriétés** dans **Solution Explorer**, ouvrir *assemblyinfo.cs* ou *assemblyinfo.vb* dans l’éditeur.

2. Ajouter l’entrée suivante.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Cela définit l’anglais américain comme langue par défaut.

3. Déchargez le projet.

4. Ouvrez le dossier de projet dans l’éditeur.

5. Dans l’élément racine, `Project` ajoutez un `PropertyGroup` élément avec un `UICulture` élément qui correspond à votre langage par défaut.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Cela définit l’anglais américain comme la culture par défaut de l’interface utilisateur pour Windows Presentation Foundation (WPF) contrôles.

6. Localisez l’élément `ItemGroup` qui contient des `EmbeddedResource` éléments.

7. Dans `EmbeddedResource` l’élément qui appelle *VSPackage.en-US.resx*, remplacer l’élément `ManifestResourceName` par un `LogicalName` élément qui est configuré à `VSPackage.en-US.Resources`, comme suit:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Pour chaque langue `EmbeddedResource` localisée, `VsPackage.en-US`copiez l’élément pour , et définissez **l’attribut inclus** et **l’élément LogicalName** de la copie sur le local cible.

9. À chaque `VSCTCompile` élément localisé, `ResourceName` ajoutez un `Menus.ctmenu`élément qui indique , comme le montre l’exemple suivant :

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Enregistrer le dossier du projet et recharger le projet.

11. Créez le projet.

     Cela crée un assemblage principal, et des assemblages de ressources pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, voir [Les forfaits LOCALize VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Voir aussi

- [Étendre les menus et les commandes](../extensibility/extending-menus-and-commands.md)
- [Mondialiser et localiser les applications](../ide/globalizing-and-localizing-applications.md)
