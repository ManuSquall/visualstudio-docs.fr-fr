---
title: Localisation des commandes de Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd5755f2b0bf8fe4379d503d952341f176c0b870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679266"
---
# <a name="localize-menu-commands"></a>Localiser des commandes de menu
Vous pouvez fournir un texte localisé pour les commandes de menu et barre d’outils en créant localisée *.vsct* fichiers et localisées *.resx* fichiers pour votre VSPackage et ensuite la mise à jour les fichiers projet pour incorporer le modifications.

 Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [packages VSIX localiser](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localiser des noms de commande
 Dans les VSPackages, les commandes de menu et boutons de barre d’outils sont définies dans le *.vsct* fichier.

1. Dans **l’Explorateur de solutions**, modifier le nom de la *.vsct* à partir de fichiers *filename.vsct* à *filename.en-US.vsct*.

2. Faites une copie de *filename.en-US.vsct* pour chaque langue localisée.

    Nommez chaque copie *filename. {} Paramètres régionaux} .vsct*, où *{Locale}* est un nom de culture particulière. Pour obtenir la liste de valeurs de nom de culture, consultez [ID de paramètres régionaux assignés par Microsoft](/windows/uwp/publish/supported-languages).

    Ces *nom de fichier. Locale.VSCT* fichiers contiendra le texte de menu localisée pour votre package.

3. Ouvrez chaque *nom de fichier. Locale.VSCT* fichier pour localiser le texte.

   1. Modifier le [ButtonText](../extensibility/buttontext-element.md) élément valeurs en fonction de la langue spécifique.

   2. Si vous souhaitez fournir des icônes localisées, modifier le [Bitmap](../extensibility/bitmap-element.md) pour qu’ils pointent vers les fichiers cible.

      L’exemple suivant montre l’anglais et espagnol texte du bouton pour ouvrir une fenêtre d’outil Explorateur de l’arborescence de la famille d’une commande.

      [*FamilyTree.en-US.vsct*]

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

## <a name="localize-other-text-resources"></a>Localiser les autres ressources de texte
 Ressources de texte autres que des noms de commande sont définies dans la ressource (*.resx*) les fichiers.

1.  Renommer *VSPackage.resx* à *VSPackage.en-us.resx*.

2.  Faites une copie de la *VSPackage.en-us.resx* langue localisée de fichier pour chacun.

     Nommez chaque copie *VSPackage. {} Paramètres régionaux} .resx*, où *{Locale}* est un nom de culture particulière.

3.  Renommer *Resources.resx* à *Resources.en-us.resx*.

4.  Faites une copie de la *Resources.en-us.resx* langue localisée de fichier pour chacun.

     Nommez chaque copie *ressources. {} Paramètres régionaux} .resx*, où *{Locale}* est un nom de culture particulière.

5.  Ouvrez chaque *.resx* fichier pour modifier la chaîne des valeurs en fonction de la langue et la culture. L’exemple suivant montre la définition de ressource localisée pour la barre de titre d’une fenêtre outil.

     [*Resources.en-us.resx*]

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

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporer des ressources localisées dans le projet
 Vous devez modifier le *assemblyinfo.cs* fichier et le fichier projet pour incorporer les ressources localisées.

1.  À partir de la **propriétés** nœud **l’Explorateur de solutions**, ouvrez *assemblyinfo.cs* ou *assemblyinfo.vb* dans l’éditeur.

2.  Ajoutez l’entrée suivante.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Cela définit anglais (États-Unis) comme langue par défaut.

3.  Décharger le projet.

4.  Ouvrez le fichier projet dans l’éditeur.

5.  Recherchez le `ItemGroup` élément contenant `EmbeddedResource` éléments.

6.  Dans le `EmbeddedResource` élément appelle *VSPackage.en-us.resx*, remplacez le `ManifestResourceName` élément avec un `LogicalName` élément, la valeur `VSPackage.en-US.Resources`, comme suit.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7.  Pour chaque langue localisée, copiez la `EmbeddedResource` élément pour `VsPackage.en-US`et définissez le **Include** attribut et **LogicalName** élément de la copie pour les paramètres régionaux cibles, comme indiqué dans le code suivant exemple.

8.  À chaque localisé `VSCTCompile` élément, ajoutez un `ResourceName` élément sur lequel pointe `Menus.ctmenu`, comme illustré dans l’exemple suivant.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

9. Enregistrez le fichier projet et recharger le projet.

10. Générez le projet.

     Cela crée un assembly principal et des assemblys de ressources pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, consultez [packages VSIX localiser](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Voir aussi
- [Étendre des menus et commandes](../extensibility/extending-menus-and-commands.md)
- [MenuCommands et OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Globaliser et localiser des applications](../ide/globalizing-and-localizing-applications.md)