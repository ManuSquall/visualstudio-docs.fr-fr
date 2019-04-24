---
title: 'Procédure : Créer un. Fichier VSCT | Microsoft Docs'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056937"
---
# <a name="how-to-create-a-vsct-file"></a>Procédure : Créer un fichier .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe plusieurs façons de créer un fichier de configuration (.vsct) basé sur XML Visual Studio Command Table.  
  
- Vous pouvez créer un nouveau VSPackage s’affiche dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modèle de Package.  
  
- Vous pouvez utiliser le compilateur de configuration de table commande basé sur XML, Vsct.exe, pour générer un fichier à partir d’un fichier .ctc existant.  
  
- Vous pouvez utiliser Vsct.exe pour générer un fichier .vsct à partir d’un fichier .cto existant.  
  
- Vous pouvez créer manuellement un nouveau fichier .vsct.  
  
  Cette rubrique explique comment créer manuellement un nouveau fichier .vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Pour créer manuellement un nouveau fichier .vsct  
  
1. Démarrez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. Sur le **fichier** menu, pointez sur **New**, puis cliquez sur **fichier**.  
  
3. Dans le **modèles** volet, cliquez sur **fichier XML** puis cliquez sur **Open**.  
  
4. Sur le **vue** menu, cliquez sur **fenêtre Propriétés** pour afficher les propriétés du fichier XML.  
  
5. Dans le **propriétés** fenêtre, cliquez sur le bouton Parcourir (...) dans la propriété Schemas.  
  
6. Dans la liste des schémas XSD, sélectionnez le schéma vsct.xsd. Si elle n’est pas dans la liste, cliquez sur **ajouter** , puis recherchez le fichier sur un lecteur local. Cliquez sur **OK** lorsque vous avez terminé.  
  
7. Dans le fichier XML, tapez `<CommandTable` puis appuyez sur TAB. Fermer la balise en tapant `>`.  
  
     Cette opération crée un fichier .vsct de base.  
  
8. Renseignez les éléments du fichier XML que vous souhaitez ajouter, selon le [VSCT schéma](../../extensibility/vsct-xml-schema-reference.md). Pour plus d’informations, consultez [Authoring. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Simplement en ajoutant un fichier .vsct à un projet ne provoque pas se compiler. Vous devez l’incorporer dans le processus de génération.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Pour ajouter un fichier .vsct à la compilation du projet  
  
1. Ouvrez votre fichier projet dans l’éditeur. Si le projet est chargé, vous devez tout d’abord le décharger.  
  
2. Ajouter un [élément ItemGroup](../../msbuild/itemgroup-element-msbuild.md) qui contient un élément VSCTCompile, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L’élément ResourceName doit toujours être défini `Menus.ctmenu`.  
  
3. Si votre projet contient un fichier .resx, ajoutez un élément EmbeddedResource qui contient un élément MergeWithCTO, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Ce balisage doit être placé à l’intérieur de l’élément ItemGroup qui contient des ressources incorporées.  
  
4. Ouvrez le fichier de package, généralement nommé *nom_projet*Package.cs ou *nom_projet*Package.vb, dans l’éditeur.  
  
5. Ajoutez un attribut ProvideMenuResource à la classe de package, comme illustré dans l’exemple suivant.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     La première valeur du paramètre doit correspondre à la valeur de l’attribut ResourceName que vous défini dans le fichier projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Création. Fichiers VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Guide pratique pour Créer un. Fichier VSCT d’un existant. Fichiers CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Guide pratique pour Créer un. Fichier VSCT d’un existant. Fichier de directeur technique](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
