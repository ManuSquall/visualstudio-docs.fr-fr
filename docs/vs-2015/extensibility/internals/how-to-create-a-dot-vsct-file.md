---
title: 'Comment : créer un. Fichier vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158354"
---
# <a name="how-to-create-a-vsct-file"></a>Guide pratique pour créer un fichier .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe plusieurs façons de créer un fichier de configuration de table de commandes Visual Studio (. vsct) basé sur XML.  
  
- Vous pouvez créer un nouveau VSPackage dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modèle de package.  
  
- Vous pouvez utiliser le compilateur de configuration de table de commandes basé sur XML, Vsct.exe, pour générer un fichier à partir d’un fichier. CTC existant.  
  
- Vous pouvez utiliser Vsct.exe pour générer un fichier. vsct à partir d’un fichier. directeur de la génération.  
  
- Vous pouvez créer manuellement un nouveau fichier. vsct.  
  
  Cette rubrique explique comment créer manuellement un nouveau fichier. vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier. vsct  
  
1. Démarrez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Fichier**.  
  
3. Dans le volet **modèles** , cliquez sur **fichier XML** , puis sur **ouvrir**.  
  
4. Dans le menu **affichage** , cliquez sur **fenêtre Propriétés** pour afficher les propriétés du fichier XML.  
  
5. Dans la fenêtre **Propriétés** , cliquez sur le bouton Parcourir (...) de la propriété schémas.  
  
6. Dans la liste des schémas XSD, sélectionnez le schéma vsct. xsd. S’il ne figure pas dans la liste, cliquez sur **Ajouter** , puis recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.  
  
7. Dans le fichier XML, tapez, `<CommandTable` puis appuyez sur la touche Tab. Fermez la balise en tapant `>` .  
  
     Cela crée un fichier. vsct de base.  
  
8. Renseignez les éléments du fichier XML que vous souhaitez ajouter, en fonction du [schéma vsct](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, consultez [création. Fichiers vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Le simple ajout d’un fichier. vsct à un projet ne provoque pas sa compilation. Vous devez l’incorporer dans le processus de génération.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier. vsct à la compilation de projet  
  
1. Ouvrez votre fichier projet dans l’éditeur. Si le projet est chargé, vous devez d’abord le décharger.  
  
2. Ajoutez un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) qui contient un élément VSCTCompile, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L’élément ResourceName doit toujours avoir la valeur `Menus.ctmenu` .  
  
3. Si votre projet contient un fichier. resx, ajoutez un élément EmbeddedResource qui contient un élément MergeWithCTO, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Ce balisage doit se trouver à l’intérieur de l’élément ItemGroup qui contient des ressources incorporées.  
  
4. Ouvrez le fichier de package, généralement nommé *ProjectName*package.cs ou *ProjectName*package. vb, dans l’éditeur.  
  
5. Ajoutez un attribut ProvideMenuResource à la classe package, comme illustré dans l’exemple suivant.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     La première valeur de paramètre doit correspondre à la valeur de l’attribut ResourceName que vous avez défini dans le fichier projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Création. Fichiers vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Table de commandes Visual Studio (. Fichiers vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment : créer un. Fichier vsct à partir d’un existant. Fichier CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Comment : créer un. Fichier vsct à partir d’un existant. Fichier de directeur technique](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
