---
title: Localisation des commandes de Menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686132"
---
# <a name="localizing-menu-commands"></a>Localisation des commandes de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir un texte localisé pour le menu et barre d’outils, commandes en créant des fichiers .vsct localisée et localisées des fichiers .resx pour votre VSPackage et ensuite mise à jour les fichiers projet incorporer les modifications.  
  
 Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localisation des noms de commande  
 Dans les VSPackages, les commandes de menu et boutons de barre d’outils sont définis dans le fichier .vsct.  
  
1. Dans **l’Explorateur de solutions**, modifier le nom du fichier .vsct à partir de *filename*.vsct à *filename*.en-US.vsct.  
  
2. Faites une copie de *filename*.en-US.vsct pour chacun de langue localisée.  
  
    Nommez chaque copie *filename*. *Paramètres régionaux*.vsct, où *paramètres régionaux* est un nom de culture particulière. Pour obtenir la liste de valeurs de nom de culture, consultez [ID de paramètres régionaux assignés par Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Ces *filename*. *Paramètres régionaux*fichiers .vsct contiendra le texte de menu localisée pour votre package.  
  
3. Ouvrez chaque *filename*. *Paramètres régionaux*fichier .vsct pour localiser le texte.  
  
   1. Modifier le [ButtonText](../extensibility/buttontext-element.md) élément valeurs en fonction de la langue spécifique.  
  
   2. Si vous souhaitez fournir des icônes localisées, modifier le [Bitmap](../extensibility/bitmap-element.md) pour qu’ils pointent vers les fichiers cible.  
  
      L’exemple suivant montre l’anglais et espagnol texte du bouton pour ouvrir une fenêtre d’outil Explorateur de l’arborescence de la famille d’une commande.  
  
      [FamilyTree.en US.vsct]  
  
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
 Ressources de texte autres que des noms de commande sont définies dans les fichiers de ressources (.resx).  
  
1. Renommez VSPackage.resx VSPackage.en-us.resx.  
  
2. Effectuez une copie du fichier VSPackage.en-us.resx pour chaque langue localisée.  
  
     Nom de chaque copie VSPackage. *Paramètres régionaux*.resx, où *paramètres régionaux* est un nom de culture particulière.  
  
3. Renommez le fichier Resources.en-us.resx Resources.resx.  
  
4. Effectuez une copie du fichier Resources.en-us.resx pour chaque langue localisée.  
  
     Nom de chaque copie de ressources. *Paramètres régionaux*.resx, où *paramètres régionaux* est un nom de culture particulière.  
  
5. Ouvrez chaque fichier .resx pour modifier les valeurs de chaîne en fonction de la langue et la culture. L’exemple suivant montre la définition de ressource localisée pour la barre de titre d’une fenêtre outil.  
  
     [Resources.en-us.resx]  
  
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
  
1. À partir de la **propriétés** nœud **l’Explorateur de solutions**, ouvrez assemblyinfo.cs ou assemblyinfo.vb dans l’éditeur.  
  
2. Ajoutez l’entrée suivante.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Cela définit anglais (États-Unis) comme langue par défaut.  
  
3. Décharger le projet.  
  
4. Ouvrez le fichier projet dans l’éditeur.  
  
5. Recherchez le `ItemGroup` élément contenant `EmbeddedResource` éléments.  
  
6. Dans le `EmbeddedResource` élément qui appelle VSPackage.en-us.resx, remplacez le `ManifestResourceName` élément avec un `LogicalName` élément, la valeur `VSPackage.en-US.Resources`, comme suit.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Pour chaque langue localisée, copiez la `EmbeddedResource` élément pour VsPackage.en-US et définissez le **Include** attribut et **LogicalName** élément de la copie pour les paramètres régionaux cibles, comme indiqué dans le code suivant exemple.  
  
8. À chaque localisé `VSCTCompile` élément, ajoutez un `ResourceName` élément sur lequel pointe `Menus.ctmenu`, comme illustré dans l’exemple suivant.  
  
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
 [MenuCommands et OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalisation et localisation](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
