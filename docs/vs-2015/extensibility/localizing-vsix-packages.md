---
title: Localisation de Packages VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2392f77ef3b78176dd33defd012b828d7a918b5b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947556"
---
# <a name="localizing-vsix-packages"></a>Localisation de packages VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez localiser un package VSIX en créant un fichier Extension.vsixlangpack pour chaque langue cible et en les plaçant dans le dossier approprié. Lorsqu’un package localisé est installé, le nom localisé de l’extension s’affiche avec une description localisée. Si vous fournissez un fichier de licence localisée ou une URL qui pointe vers les informations localisées, ils sont également affichés.  
  
 Si le contenu de votre package VSIX inclut un VSPackage qui ajoute les commandes de menu ou de toute autre interface utilisateur, consultez [localisation des commandes de Menu](../extensibility/localizing-menu-commands.md) pour plus d’informations sur la localisation des nouveaux éléments d’interface utilisateur.  
  
## <a name="directory-structure"></a>Structure de répertoires  
 Lorsqu’un utilisateur installe une extension, **Extensions et mises à jour** vérifie le niveau supérieur du package VSIX un dossier dont le nom correspond aux paramètres régionaux de Visual Studio de l’ordinateur cible. Si **Extensions et mises à jour** trouve un .vsixlangpack le fichier dans le dossier, il remplace les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le fichier .vsixmanifest. Ces valeurs sont affichées lors de l’extension est en cours d’installation. L’exemple suivant montre la structure de répertoires d’un package VSIX est localisée en espagnol (es-ES) et Français (fr-FR).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types].xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Les modèles de projet VSIX pris en charge dans le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] générer un manifeste VSIX et nommez-le source.extension.vsixmanifest. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans Extension.VsixManifest dans le package VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Le fichier Extension.vsixlangpack  
 Le fichier Extension.vsixlangpack suit le [schéma du module linguistique VSIX](../extensibility/vsx-language-pack-schema-reference.md). Ce schéma comporte un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) élément racine et ces quatre éléments enfants : [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), et [licence](../extensibility/license-element-vsix-language-pack-schema.md). Ces éléments enfants correspondent à la `Name`, `Description`, `MoreInfoURL`, et `License` éléments enfants de le `Identifier` élément du fichier Extension.vsixmanifest.  
  
 Lorsque vous créez un fichier vsixlangpack, vous devez définir le `Include in Vsix` propriété `true`. Sinon, le texte d’installation localisé sera ignoré.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Pour définir l’inclure dans Vsix propriété  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le fichier Extension.vsixlangpack, puis cliquez sur **propriétés**.  
  
2.  Dans la grille des propriétés, cliquez sur **inclure dans Vsix**et définissez sa valeur sur `true`.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant affiche les parties pertinentes d’un fichier Extension.vsixmanifest, ainsi que le fichier Extension.vsixlangpack correspondant pour l’espagnol. Les valeurs à partir du pack de langue remplacent les valeurs à partir du manifeste si les paramètres régionaux de Visual Studio de l’ordinateur cible sont configuré en espagnol.  
  
### <a name="code"></a>Code  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSIXLanguagePack, élément](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modèle de projet VSIX](../extensibility/vsix-project-template.md)
