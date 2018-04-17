---
title: Localisation des commandes de Menu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4fd8f2b42464b31c71b2983dd3e5c66f4a03351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-menu-commands"></a>Localisation des commandes de Menu
Vous pouvez fournir un texte localisé pour le menu et barre d’outils commandes en créant des fichiers .vsct localisées et localisée des fichiers .resx pour votre VSPackage et mise à jour des fichiers projet incorporer les modifications.  
  
 Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localisation des noms de commande  
 Dans les VSPackages, les commandes de menu et boutons de barre d’outils sont définis dans le fichier .vsct.  
  
1.  Dans **l’Explorateur de solutions**, modifier le nom du fichier .vsct à partir de *nom de fichier*.vsct à *nom de fichier*.en-US.vsct.  
  
2.  Effectuer une copie de *nom de fichier*.en-US.vsct pour chaque langue de localisée.  
  
     Nom de chaque copie *nom de fichier*. *Paramètres régionaux*.vsct, où *paramètres régionaux* est un nom de culture particulière. Pour obtenir la liste de valeurs de nom de culture, consultez [ID de paramètres régionaux assignés par Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Ces *nom de fichier*. *Paramètres régionaux*fichiers .vsct contient le texte du menu localisés pour votre package.  
  
3.  Ouvrez chaque *nom de fichier*. *Paramètres régionaux*fichier .vsct pour localiser le texte.  
  
    1.  Modifier la [ButtonText](../extensibility/buttontext-element.md) élément des valeurs en fonction de la langue spécifique.  
  
    2.  Si vous utilisez les icônes localisées, modifiez le [Bitmap](../extensibility/bitmap-element.md) pour qu’ils pointent vers les fichiers de la cible.  
  
     L’exemple suivant montre l’anglais et espagnol texte du bouton pour ouvrir une fenêtre d’outil Explorateur de l’arborescence de la famille d’une commande.  
  
     [FamilyTree.en-US.vsct]  
  
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
  
     [FamilyTree.es-ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Localiser des autres ressources de texte  
 Ressources de texte en dehors des noms de commande sont définies dans les fichiers de ressources (.resx).  
  
1.  Renommez VSPackage.resx VSPackage.en-us.resx.  
  
2.  Effectuez une copie du fichier VSPackage.en-us.resx pour chaque langue localisée.  
  
     Nom de chaque copie VSPackage. *Paramètres régionaux*.resx, où *paramètres régionaux* est un nom de culture particulière.  
  
3.  Renommez le fichier Resources.en-us.resx Resources.resx.  
  
4.  Effectuez une copie du fichier le fichier Resources.en-us.resx pour chaque langue localisée.  
  
     Nom de chaque copie de ressources. *Paramètres régionaux*.resx, où *paramètres régionaux* est un nom de culture particulière.  
  
5.  Ouvrez chaque fichier .resx pour modifier les valeurs de chaîne en fonction de la langue et la culture. L’exemple suivant montre la définition de ressource localisée pour la barre de titre d’une fenêtre outil.  
  
     [Le fichier Resources.en-us.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporer des ressources localisées dans le projet  
 Vous devez modifier le fichier assemblyinfo.cs et le fichier projet pour incorporer les ressources localisées.  
  
1.  À partir de la **propriétés** nœud **l’Explorateur de solutions**, ouvrez assemblyinfo.cs ou assemblyinfo.vb dans l’éditeur.  
  
2.  Ajoutez l’entrée suivante.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Cette opération définit anglais comme langue par défaut.  
  
3.  Décharger le projet.  
  
4.  Ouvrez le fichier projet dans l’éditeur.  
  
5.  Recherchez le `ItemGroup` élément contenant `EmbeddedResource` éléments.  
  
6.  Dans le `EmbeddedResource` élément qui appelle VSPackage.en-us.resx, remplacez le `ManifestResourceName` élément avec un `LogicalName` élément, la valeur `VSPackage.en-US.Resources`, comme suit.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Pour chaque langue localisée, copiez la `EmbeddedResource` élément pour VsPackage.en-US et définissez la **Include** attribut et **LogicalName** élément de la copie vers les paramètres régionaux cibles, comme le montre l’exemple suivant exemple.  
  
8.  À chaque localisée `VSCTCompile` élément, ajouter un `ResourceName` élément vers lequel pointe `Menus.ctmenu`, comme illustré dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Enregistrez le fichier projet et recharger le projet.  
  
10. Générez le projet.  
  
     Cela crée un assembly principal et des assemblys de ressources pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands et OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)