---
title: Localisation des packages VSIX | Microsoft Docs
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
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839514"
---
# <a name="localizing-vsix-packages"></a>Localisation de packages VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez localiser un package VSIX en créant un fichier extension. vsixlangpack pour chaque langue cible, puis en les plaçant dans le dossier approprié. Lors de l’installation d’un package localisé, le nom localisé de l’extension s’affiche avec une description localisée. Si vous fournissez un fichier de licence localisé, ou une URL qui pointe vers des informations localisées, elles sont également affichées.  
  
 Si le contenu de votre package VSIX inclut un VSPackage qui ajoute des commandes de menu ou une autre interface utilisateur, consultez [localisation des commandes de menu](../extensibility/localizing-menu-commands.md) pour plus d’informations sur la localisation des nouveaux éléments d’interface utilisateur.  
  
## <a name="directory-structure"></a>Structure de répertoires  
 Lorsqu’un utilisateur installe une extension, les **extensions et les mises à jour** vérifient le niveau supérieur du package VSIX pour un dossier dont le nom correspond aux paramètres régionaux de Visual Studio de l’ordinateur cible. Si les **extensions et les mises à jour** recherchent un fichier. vsixlangpack dans le dossier, elles remplacent les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le fichier. vsixmanifest. Ces valeurs s’affichent lors de l’installation de l’extension. L’exemple suivant illustre la structure de répertoires d’un package VSIX localisé en espagnol (es-ES) et en français (fr-FR).  
  
 MyExtension.dll  
  
 Extension. vsixmanifest  
  
 [Content_Types]. Xml  
  
 es-ES  
  
 Extension. vsixlangpack  
  
 fr-FR  
  
 Extension. vsixlangpack  
  
> [!NOTE]
> Les modèles de projet pris en charge par VSIX dans [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] génèrent un manifeste VSIX et le nomment source. extension. vsixmanifest. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans l’extension. VsixManifest dans le package VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Fichier extension. vsixlangpack  
 Le fichier extension. vsixlangpack suit le [schéma du module linguistique VSIX](../extensibility/vsx-language-pack-schema-reference.md). Ce schéma possède un élément racine [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) et ces quatre éléments enfants : [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)et [License](../extensibility/license-element-vsix-language-pack-schema.md). Ces éléments enfants correspondent aux `Name` `Description` éléments enfants,, `MoreInfoURL` et `License` de l' `Identifier` élément du fichier extension. vsixmanifest.  
  
 Lorsque vous créez un fichier vsixlangpack, vous devez affecter à la propriété la valeur `Include in Vsix` `true` . Dans le cas contraire, le texte d’installation localisé sera ignoré.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Pour définir la propriété Include dans VSIX  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier extension. vsixlangpack, puis cliquez sur **Propriétés**.  
  
2. Dans la grille des propriétés, cliquez sur **inclure dans VSIX**et affectez-lui la valeur `true` .  
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre des parties pertinentes d’un fichier extension. vsixmanifest, ainsi que le fichier extension. vsixlangpack correspondant pour l’espagnol. Les valeurs du module linguistique remplacent les valeurs du manifeste si les paramètres régionaux Visual Studio de l’ordinateur cible sont définis sur espagnol.  
  
### <a name="code"></a>Code  
 [Extension. vsixmanifest]  
  
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
  
 [Extension. vsixlangpack]  
  
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
 [Élément de la linguistique VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modèle de projet VSIX](../extensibility/vsix-project-template.md)
