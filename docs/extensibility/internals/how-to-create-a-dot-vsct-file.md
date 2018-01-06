---
title: "Comment : créer un. Fichier VSCT | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b64d9b35030a18a6258de52ed0f12f9796044ba5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-vsct-file"></a>Comment : créer un. Fichier VSCT  
  
Il existe plusieurs façons de créer un fichier de configuration (.vsct) basé sur XML de Visual Studio Command Table.  
  
-   Vous pouvez créer un nouveau VSPackage s’affiche dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèle de Package.  
  
-   Vous pouvez utiliser le compilateur de configuration de table basé sur XML de commande, Vsct.exe, pour générer un fichier à partir d’un fichier .ctc existant.  
  
-   Vous pouvez utiliser Vsct.exe pour générer un fichier .vsct à partir d’un fichier .cto existant.  
  
-   Vous pouvez créer manuellement un nouveau fichier .vsct.  
  
 Cette rubrique explique comment créer manuellement un nouveau fichier .vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier .vsct  
  
1.  Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **fichier**.  
  
3.  Dans le **modèles** volet, cliquez sur **fichier XML** puis cliquez sur **ouvrir**.  
  
4.  Sur le **vue** menu, cliquez sur **fenêtre Propriétés** pour afficher les propriétés du fichier XML.  
  
5.  Dans le **propriétés** fenêtre, cliquez sur le bouton Parcourir (...) dans la propriété des schémas.  
  
6.  Dans la liste des schémas XSD, sélectionnez le schéma vsct.xsd. Si elle n’est pas dans la liste, cliquez sur **ajouter** et recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.  
  
7.  Dans le fichier XML, tapez `<CommandTable` et appuyez sur TAB. Fermer la balise en tapant `>`.  
  
     Cette opération crée un fichier .vsct de base.  
  
8.  Renseignez les éléments du fichier XML que vous souhaitez ajouter, selon le [VSCT schéma](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, consultez [création. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Comment : créer un fichier .Vsct à partir d’un fichier .Ctc existant  
  
Vous pouvez créer un fichier .vsct XML à partir d’un fichier source .ctc de table de commande existant. Ce faisant, vous pouvez tirer parti de la nouvelle basé sur XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] format de compilateur de table (VSTC) de commande.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Pour créer un fichier .vsct à partir d’un fichier .ctc  
  
1.  Obtenez une copie du langage Perl.  
  
2.  Obtenez une copie du script Perl ConvertCTCToVSCT.pl, généralement situé dans le  *\<chemin d’installation de Visual Studio SDK >*\VisualStudioIntegration\Tools\bin dossier.  
  
3.  Obtenez une copie du fichier source .ctc à convertir.  
  
4.  Placez les fichiers dans le même répertoire.  
  
5.  Dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fenêtre d’invite de commandes, accédez au répertoire.  
  
6.  Type  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     où PkgCmd.ctc est le nom du fichier .ctc et PkgCmd.vsct est le nom du fichier .vsct à créer.  
  
     Un nouveau fichier source de table de commande XML .vsct est ainsi créé. Vous pouvez compiler le fichier à l’aide de Vsct.exe, le compilateur VSCT, comme vous le feriez pour tout autre fichier .vsct.  
  
    > [!NOTE]
    >  Vous pouvez améliorer la lisibilité du fichier .vsct en reformatant les commentaires XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Comment : créer un fichier .Vsct à partir d’un fichier .Cto existant  
  
Vous pouvez créer un fichier .vsct XML à partir d’un fichier .cto binaire existant. Cela vous permet de tirer parti du nouveau format de compilateur de la table de commande. Ce processus fonctionne même si le fichier .cto a été compilé à partir d’un fichier .ctc. Vous pouvez modifier et compiler le fichier .vsct dans un autre fichier .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Pour créer un fichier .vsct à partir d’un fichier .cto  
  
1.  Obtenez des copies du fichier .cto et de son fichier .ctsym correspondant.  
  
2.  Placez les fichiers dans le même répertoire que le compilateur vsct.exe.  
  
3.  À l’invite de commandes Visual Studio, accédez au répertoire qui contient les fichiers .cto et .ctsym.  
  
4.  Tapez **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct -S***symfilename***.ctsym**.  
  
     `ctofilename`est le nom du fichier .cto, `vsctfilename` est le nom du fichier vsct que vous souhaitez créer, et `symfilename` est le nom du fichier .ctsym.  
  
     Ce processus crée un fichier de compilateur de la table de commande XML .vsct. Vous pouvez modifier et compiler le fichier avec vsct.exe, le compilateur vsct, comme vous le feriez pour tout autre fichier .vsct.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ajout d’un fichier .vsct simplement à un projet ne provoque pas compiler. Vous devez l’incorporer dans le processus de génération.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier .vsct à la compilation du projet  
  
1.  Ouvrez votre fichier projet dans l’éditeur. Si le projet est chargé, vous devez tout d’abord le décharger.  
  
2.  Ajouter un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) qui contient un élément VSCTCompile, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L’élément ResourceName doit toujours être défini `Menus.ctmenu`.  
  
3.  Si votre projet contient un fichier .resx, ajoutez un élément de EmbeddedResource qui contient un élément MergeWithCTO, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Cette balise doit être placé à l’intérieur de l’élément ItemGroup qui contient les ressources incorporées.  
  
4.  Ouvrez le fichier de package, généralement nommé *nom_projet*Package.cs ou *nom_projet*Package.vb, dans l’éditeur.  
  
5.  Ajoutez un attribut ProvideMenuResource à la classe de package, comme indiqué dans l’exemple suivant.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     La première valeur du paramètre doit correspondre à la valeur de l’attribut ResourceName que vous avez définies dans le fichier projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Création. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tableau de commandes de Visual Studio (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)