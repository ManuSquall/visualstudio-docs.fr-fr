---
title: Localisation des commandes de menu | Microsoft Docs
ms.date: 10/08/2019
ms.topic: how-to
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
ms.openlocfilehash: 1c1c158fd689cbcae18fec5d3306e6d6fadb169f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904550"
---
# <a name="localize-menu-commands"></a>Localiser les commandes de menu

Vous pouvez fournir un texte localisé pour les commandes de menu et de barre d’outils en créant des fichiers *. vsct* localisés et des fichiers *. resx* localisés pour votre VSPackage, puis en mettant à jour les fichiers projet pour incorporer les modifications.

Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [localiser des packages VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localiser les noms de commande

Dans les VSPackages, les commandes de menu et les boutons de barre d’outils sont définis dans le fichier *. vsct* .

1. Dans **Explorateur de solutions**, remplacez le nom du fichier *. vsct* par *filename. vsct* par *filename. en-US. vsct*.

2. Effectuez une copie du *fichier. en-US. vsct* pour chaque langue localisée.

    Nommez chaque *nom de fichier de copie. { Locale}. vsct*, où *{locale}* est un nom de culture particulier. Pour obtenir la liste des valeurs de nom de culture, consultez [ID de paramètres régionaux attribués par Microsoft](/windows/uwp/publish/supported-languages).

    Ce *nom de fichier. Paramètres régionaux.* les fichiers vsct contiendront le texte de menu localisé pour votre package.

3. Ouvrez chaque *nom de fichier. Fichier locale. vsct* pour localiser le texte.

   1. Modifiez les valeurs de l’élément [ButtonText](../extensibility/buttontext-element.md) en fonction de la langue en question.

   2. Si vous fournissez des icônes localisées, modifiez les valeurs de la [bitmap](../extensibility/bitmap-element.md) pour qu’elles pointent vers les fichiers cibles.

      L’exemple suivant montre le texte du bouton anglais et espagnol pour une commande permettant d’ouvrir une fenêtre outil de l’Explorateur de l’arborescence de la famille.

      [*FamilyTree. en-US. vsct*]

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

    [*FamilyTree.es-es. vsct*]

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

## <a name="localize-other-text-resources"></a>Localiser d’autres ressources de texte

Les ressources de texte autres que les noms de commande sont définies dans des fichiers de ressources (*. resx*).

1. Renommez *VSPackage. resx* en *VSPackage. en-US. resx*.

2. Effectuez une copie du fichier *VSPackage. fr-US. resx* pour chaque langue localisée.

     Nommez chaque *VSPackage de copie. { Locale}. resx*, où *{locale}* est un nom de culture particulier.

3. Renommez *Resources. resx* en *Resources. en-US. resx*.

4. Effectuez une copie du fichier *Resources. en-US. resx* pour chaque langue localisée.

     Nommez chaque copie des *ressources. { Locale}. resx*, où *{locale}* est un nom de culture particulier.

5. Ouvrez chaque fichier *. resx* pour modifier les valeurs de chaîne en fonction de la langue et de la culture en question. L’exemple suivant montre la définition de ressource localisée pour la barre de titre d’une fenêtre outil.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporer des ressources localisées dans le projet

Vous devez modifier le fichier *AssemblyInfo.cs* et le fichier projet pour incorporer les ressources localisées.

1. À partir du nœud **Propriétés** dans **Explorateur de solutions**, ouvrez *AssemblyInfo.cs* ou *AssemblyInfo. vb* dans l’éditeur.

2. Ajoutez l’entrée suivante.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Cela définit l’anglais (États-Unis) comme langue par défaut.

3. Déchargez le projet.

4. Ouvrez le fichier projet dans l’éditeur.

5. Dans l' `Project` élément racine, ajoutez un `PropertyGroup` élément avec un `UICulture` élément qui correspond à votre langue par défaut.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Cela définit l’anglais (États-Unis) comme culture d’interface utilisateur par défaut pour les contrôles Windows Presentation Foundation (WPF).

6. Localisez l' `ItemGroup` élément qui contient des `EmbeddedResource` éléments.

7. Dans l' `EmbeddedResource` élément qui appelle *VSPackage. en-US. resx*, remplacez l' `ManifestResourceName` élément par un `LogicalName` élément qui a la valeur `VSPackage.en-US.Resources` , comme suit :

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Pour chaque langue localisée, copiez l' `EmbeddedResource` élément pour `VsPackage.en-US` et définissez l’attribut **include** et l’élément **LogicalName** de la copie sur les paramètres régionaux cibles.

9. Pour chaque élément localisé `VSCTCompile` , ajoutez un `ResourceName` élément qui pointe vers `Menus.ctmenu` , comme illustré dans l’exemple suivant :

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Enregistrez le fichier projet et rechargez le projet.

11. Créez le projet.

     Cela crée un assembly principal et des assemblys de ressource pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, consultez [localiser des packages VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Voir aussi

- [Étendre des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [Globaliser et localiser des applications](../ide/globalizing-and-localizing-applications.md)
