---
title: "Localisation de Packages VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "localiser un package"
  - "localiser une extension"
  - "déploiement localisé"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Localisation de Packages VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez localiser un package VSIX en créant un fichier Extension.vsixlangpack pour chaque langue cible et en les plaçant dans le dossier approprié. Lorsqu’un package localisé est installé, le nom localisé de l’extension est affiché avec une description localisée. Si vous fournissez un fichier de licence localisé, ou une URL qui pointe vers les informations localisées, ils sont également affichés.  
  
 Si votre package VSIX comprend un VSPackage qui ajoute des commandes de menu ou de toute autre interface utilisateur, consultez [Localisation des commandes de Menu](../extensibility/localizing-menu-commands.md) Pour plus d’informations sur la localisation des nouveaux éléments d’interface utilisateur.  
  
## Structure de répertoires  
 Lorsqu’un utilisateur installe une extension, **Extensions et mises à jour** vérifie le niveau supérieur du package VSIX un dossier dont le nom correspond aux paramètres régionaux Visual Studio de l’ordinateur cible. Si **Extensions et mises à jour** trouve une .vsixlangpack file dans le dossier, il remplace les valeurs localisées dans ce fichier par les valeurs correspondantes dans le fichier .vsixmanifest. Ces valeurs sont affichées lorsque l’extension est installée. L’exemple suivant montre la structure de répertoires d’un package VSIX localisé en espagnol \(es\-ES\) et en Français \(fr\-FR\).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\] .xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Les modèles de projet VSIX pris en charge dans les [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Générer un manifeste VSIX et nommez\-le source.extension.vsixmanifest. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans Extension.VsixManifest du package VSIX.  
  
## Le fichier Extension.vsixlangpack  
 Le fichier Extension.vsixlangpack suit le [schéma du module linguistique VSIX](../extensibility/vsx-language-pack-schema-reference.md). Ce schéma comporte un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) élément racine et les quatre éléments enfants : [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), et [licence](../extensibility/license-element-vsix-language-pack-schema.md). Ces éléments enfants correspondent à la `Name`, `Description`, `MoreInfoURL`, et `License` des éléments enfants de le `Identifier` élément du fichier Extension.vsixmanifest.  
  
 Lorsque vous créez un fichier vsixlangpack, vous devez définir le `Include in Vsix` propriété `true`. Dans le cas contraire, le texte d’installation localisé sera ignoré.  
  
#### Pour définir l’inclure dans Vsix propriété  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le fichier Extension.vsixlangpack, puis cliquez sur **propriétés**.  
  
2.  Dans la grille des propriétés, cliquez sur **inclure dans Vsix**, et définissez sa valeur sur `true`.  
  
## Exemple  
  
### Description  
 L’exemple suivant affiche les parties pertinentes d’un fichier Extension.vsixmanifest, ainsi que le fichier Extension.vsixlangpack correspondant pour l’espagnol. Les valeurs à partir du pack de langue remplacent les valeurs du manifeste si les paramètres régionaux de Visual Studio de l’ordinateur cible sont configuré en espagnol.  
  
### Code  
 \[Extension.vsixmanifest\]  
  
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
  
 \[Extension.vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## Voir aussi  
 [VSIXLanguagePack, élément](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modèle de projet VSIX](../extensibility/vsix-project-template.md)