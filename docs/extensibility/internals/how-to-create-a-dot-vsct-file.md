---
title: "Comment : cr&#233;er un. Fichier VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fichiers VSCT, création"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Comment : cr&#233;er un. Fichier VSCT
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il existe plusieurs façons de créer un fichier de configuration \(.vsct\) de Table de XML sur la commande de Visual Studio.  
  
-   Vous pouvez créer un nouveau VSPackage dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de Package.  
  
-   Vous pouvez utiliser le compilateur de configuration de table commande basé sur XML, Vsct.exe, pour générer un fichier à partir d'un fichier .ctc existant.  
  
-   Vous pouvez utiliser Vsct.exe pour générer un fichier .vsct à partir d'un fichier .cto existant.  
  
-   Vous pouvez créer manuellement un nouveau fichier .vsct.  
  
 Cette rubrique explique comment créer manuellement un nouveau fichier .vsct.  
  
### Pour créer manuellement un fichier .vsct  
  
1.  Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **fichier**.  
  
3.  Dans le **modèles** volet, cliquez sur **fichier XML** puis **Open**.  
  
4.  Sur le **affichage** menu, cliquez sur **fenêtre Propriétés** pour afficher les propriétés du fichier XML.  
  
5.  Dans le **propriétés** fenêtre, cliquez sur le bouton Parcourir \(...\) bouton de la propriété de schémas.  
  
6.  Dans la liste des schémas XSD, sélectionnez le schéma vsct.xsd. Si elle n'est pas dans la liste, cliquez sur **Ajouter** puis recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.  
  
7.  Dans le fichier XML, tapez `<CommandTable` et appuyez sur TAB. Fermer la balise en tapant `>`.  
  
     Cela crée un fichier de base .vsct.  
  
8.  Renseignez les éléments du fichier XML que vous souhaitez ajouter, selon le [VSCT schéma](../../extensibility/vsct-xml-schema-reference.md). Pour plus d'informations, consultez [Création. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## Compilation du code  
 Ajout d'un fichier .vsct simplement à un projet n'entraîne pas se compiler. Vous devez l'incorporer dans le processus de génération.  
  
### Pour ajouter un fichier .vsct pour la compilation du projet  
  
1.  Ouvrez votre fichier de projet dans l'éditeur. Si le projet est chargé, vous devez tout d'abord le décharger.  
  
2.  Ajouter un [ItemGroup, élément](../../msbuild/itemgroup-element-msbuild.md) qui contient un élément VSCTCompile, comme illustré dans l'exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L'élément ResourceName doit toujours être défini `Menus.ctmenu`.  
  
3.  Si votre projet contient un fichier .resx, ajoutez un élément EmbeddedResource qui contient un élément MergeWithCTO, comme illustré dans l'exemple suivant.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Cette balise doit être placé à l'intérieur de l'élément ItemGroup contenant des ressources incorporées.  
  
4.  Ouvrez le fichier de package, généralement appelé *nom\_projet*Package.cs ou *nom\_projet*Package.vb, dans l'éditeur.  
  
5.  Ajoutez un attribut ProvideMenuResource à la classe de package, comme illustré dans l'exemple suivant.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Valeur du premier paramètre doit correspondre à la valeur de l'attribut ResourceName que vous avez défini dans le fichier projet.  
  
## Voir aussi  
 [Création. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment : créer un fichier .Vsct à partir d’un fichier .Ctc existant](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Comment : créer un fichier .Vsct à partir d’un fichier .Cto existant](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [Référence de schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)