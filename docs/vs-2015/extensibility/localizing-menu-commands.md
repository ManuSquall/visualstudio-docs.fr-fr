---
title: Localisation des commandes de menu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686132"
---
# <a name="localizing-menu-commands"></a>Localisation des commandes de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir un texte localisé pour les commandes de menu et de barre d’outils en créant des fichiers. vsct localisés et des fichiers. resx localisés pour votre VSPackage, puis en mettant à jour les fichiers projet pour incorporer les modifications.  
  
 Pour plus d’informations sur la localisation de l’expérience d’installation, consultez [Localizing VSIX packages](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localisation des noms de commandes  
 Dans les VSPackages, les commandes de menu et les boutons de barre d’outils sont définis dans le fichier. vsct.  
  
1. Dans **Explorateur de solutions**, remplacez le nom du fichier. vsct par *filename*. vsct par *filename*. en-US. vsct.  
  
2. Effectuez une copie du *fichier*. en-US. vsct pour chaque langue localisée.  
  
    Nommez chaque *nom de fichier*de copie. *Locale*. vsct, où les *paramètres régionaux* sont un nom de culture particulier. Pour obtenir la liste des valeurs de nom de culture, consultez [ID de paramètres régionaux attribués par Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Ce *nom de fichier*. *Paramètres régionaux*. les fichiers vsct contiendront le texte de menu localisé pour votre package.  
  
3. Ouvrez chaque *nom de fichier*. Fichier *locale*. vsct pour localiser le texte.  
  
   1. Modifiez les valeurs de l’élément [ButtonText](../extensibility/buttontext-element.md) en fonction de la langue en question.  
  
   2. Si vous fournissez des icônes localisées, modifiez les valeurs de la [bitmap](../extensibility/bitmap-element.md) pour qu’elles pointent vers les fichiers cibles.  
  
      L’exemple suivant montre le texte du bouton anglais et espagnol pour une commande permettant d’ouvrir une fenêtre outil de l’Explorateur de l’arborescence de la famille.  
  
      [FamilyTree. en-US. vsct]  
  
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
  
    [FamilyTree.es-ES. vsct]  
  
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
 Les ressources de texte autres que les noms de commande sont définies dans des fichiers de ressources (. resx).  
  
1. Renommez VSPackage. resx en VSPackage. en-US. resx.  
  
2. Effectuez une copie du fichier VSPackage. fr-US. resx pour chaque langue localisée.  
  
     Nommez chaque VSPackage de copie. *Locale*. resx, où les *paramètres régionaux* sont un nom de culture particulier.  
  
3. Renommez Resources. resx en Resources. en-US. resx.  
  
4. Effectuez une copie du fichier Resources. en-US. resx pour chaque langue localisée.  
  
     Nommez chaque copie des ressources. *Locale*. resx, où les *paramètres régionaux* sont un nom de culture particulier.  
  
5. Ouvrez chaque fichier. resx pour modifier les valeurs de chaîne en fonction de la langue et de la culture en question. L’exemple suivant montre la définition de ressource localisée pour la barre de titre d’une fenêtre outil.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Intégration de ressources localisées dans le projet  
 Vous devez modifier le fichier assemblyinfo.cs et le fichier projet pour incorporer les ressources localisées.  
  
1. À partir du nœud **Propriétés** dans **Explorateur de solutions**, ouvrez AssemblyInfo.cs ou AssemblyInfo. vb dans l’éditeur.  
  
2. Ajoutez l’entrée suivante.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Cela définit l’anglais (États-Unis) comme langue par défaut.  
  
3. Déchargez le projet.  
  
4. Ouvrez le fichier projet dans l’éditeur.  
  
5. Localisez l' `ItemGroup` élément qui contient des `EmbeddedResource` éléments.  
  
6. Dans l' `EmbeddedResource` élément qui appelle VSPackage. en-US. resx, remplacez l' `ManifestResourceName` élément par un `LogicalName` élément, avec la valeur `VSPackage.en-US.Resources` , comme suit.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Pour chaque langue localisée, copiez l'  `EmbeddedResource` élément pour VSPackage. en-US, puis définissez les éléments **include** et **LogicalName** de la copie sur les paramètres régionaux cibles, comme indiqué dans l’exemple suivant.  
  
8. Pour chaque élément localisé `VSCTCompile` , ajoutez un `ResourceName` élément qui pointe vers `Menus.ctmenu` , comme illustré dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Enregistrez le fichier projet et rechargez le projet.  
  
10. Créez le projet.  
  
     Cela crée un assembly principal et des assemblys de ressource pour chaque langue. Pour plus d’informations sur la localisation du processus de déploiement, consultez [localisation des packages VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands et OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalisation et localisation](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
