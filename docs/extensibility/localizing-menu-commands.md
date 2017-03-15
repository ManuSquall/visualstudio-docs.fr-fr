---
title: Localisation des commandes de Menu | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 869a1c878a591e6b755fc1311132e159d38ffe8f
ms.lasthandoff: 02/22/2017

---
# <a name="localizing-menu-commands"></a>Localisation des commandes de Menu
Vous pouvez fournir du texte localisé pour le menu et barre d’outils des commandes en créant des fichiers .vsct localisées et localisée des fichiers .resx pour votre package VS et mise à jour des fichiers projet incorporer les modifications.  
  
 Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localisation des noms de commande  
 Dans les packages VS, les commandes de menu et boutons de barre d’outils sont définis dans le fichier .vsct.  
  
1.  Dans **l’Explorateur de solutions**, modifier le nom du fichier .vsct *nom de fichier*.vsct à *filename*.en-US.vsct.  
  
2.  Effectuez une copie de *filename*.en-US.vsct pour chaque langue de localisée.  
  
     Nom de chaque copie *nom de fichier*.* Paramètres régionaux*.vsct, où *paramètres régionaux* est un nom de culture particulière. Pour obtenir la liste de valeurs de nom de culture, consultez [ID de paramètres régionaux assignés par Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Ces *nom de fichier*.* Paramètres régionaux*fichiers .vsct contient le texte de menu localisée pour votre package.  
  
3.  Ouvrez chaque *nom de fichier*.* Paramètres régionaux*fichier .vsct pour localiser le texte.  
  
    1.  Modifier la [ButtonText](../extensibility/buttontext-element.md) élément valeurs en fonction de la langue spécifique.  
  
    2.  Si vous utilisez les icônes localisées, modifier le [Bitmap](../extensibility/bitmap-element.md) pour qu’ils pointent vers les fichiers de la cible.  
  
     L’exemple suivant montre le texte du bouton en anglais et espagnol pour ouvrir une fenêtre d’outils Explorateur de l’arborescence de la famille d’une commande.  
  
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
  
## <a name="localizing-other-text-resources"></a>Localisation d’autres ressources de texte  
 Ressources texte autre que les noms de commande sont définies dans les fichiers de ressources (.resx).  
  
1.  Renommez VSPackage.resx VSPackage.en-us.resx.  
  
2.  Effectuez une copie du fichier VSPackage.en-us.resx pour chaque langue traduite.  
  
     Nom de chaque copie VSPackage. *Paramètres régionaux*.resx, où *paramètres régionaux* est un nom de culture particulière.  
  
3.  Renommez le fichier Resources.en-us.resx Resources.resx.  
  
4.  Effectuez une copie du fichier le fichier Resources.en-us.resx pour chaque langue traduite.  
  
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
 Vous devez modifier le fichier assemblyinfo.cs et le fichier de projet pour incorporer les ressources localisées.  
  
1.  À partir de la **propriétés** nœud **l’Explorateur de solutions**, ouvrez assemblyinfo.cs ou assemblyinfo.vb dans l’éditeur.  
  
2.  Ajoutez l’entrée suivante.  
  
    ```c#  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Ceci définit anglais (États-Unis) comme langue par défaut.  
  
3.  Décharger le projet.  
  
4.  Ouvrez le fichier projet dans l’éditeur.  
  
5.  Recherchez la `ItemGroup` élément contenant `EmbeddedResource` éléments.  
  
6.  Dans le `EmbeddedResource` élément qui appelle VSPackage.en-us.resx, remplacez le `ManifestResourceName` élément avec un `LogicalName` élément, la valeur `VSPackage.en-US.Resources`, comme suit.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Pour chaque langue localisée, copiez les `EmbeddedResource` élément pour VsPackage.en-US et définissez la **Include** attribut et **LogicalName** élément de la copie vers les paramètres régionaux cibles, comme indiqué dans l’exemple suivant.  
  
8.  À chaque localisée `VSCTCompile` élément, ajouter un `ResourceName` élément qui pointe vers `Menus.ctmenu`, comme illustré dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Enregistrez le fichier projet et recharger le projet.  
  
10. Générez le projet.  
  
     Cela crée un assembly principal et des assemblys de ressources pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, consultez [localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands et OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalisation et localisation](http://msdn.microsoft.com/Library/9a59696b-d89b-45bd-946d-c75da4732d02)
