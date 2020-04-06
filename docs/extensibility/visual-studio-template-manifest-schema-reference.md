---
title: Visual Studio Template Manifeste Schema Référence (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697987"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Référence de schéma manifeste de modèle de studio visuel
Ce schéma décrit le format des fichiers manifestes du modèle Visual Studio (*.vstman)* qui sont générés pour le projet visual Studio ou les modèles d’objets. Le schéma décrit également l’emplacement et d’autres informations pertinentes sur le modèle.

 : Étant donné qu’il existe des répertoires distincts d’éléments et de modèles de projets, un manifeste ne devrait jamais avoir un mélange d’éléments et de modèles de projet.

> [!IMPORTANT]
> Ce manifeste est disponible à partir de Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>ÉLÉMENT VSTemplateManifest
 L’élément racine du manifeste.

### <a name="attributes"></a>Attributs

- **Version**: Une chaîne représentant la version du manifeste du modèle. Obligatoire.

- **Local**: Une chaîne représentant le lieu ou les lieux du modèle manifeste. La valeur locale s’applique à tous les modèles. Vous devez utiliser un manifeste séparé pour chaque lieu. facultatif.

### <a name="child-elements"></a>Éléments enfants

- **VSTemplateContainer** Optionnel.

- **VSTemplateDir** Optionnel.

### <a name="parent-element"></a>Élément parent
 Aucun.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Le conteneur des éléments manifestes du modèle. Un manifeste a un conteneur de modèle pour chaque modèle qu’il définit.

### <a name="attributes"></a>Attributs
 **VSTemplateType**: Une valeur de chaîne qui spécifie le type de modèle (`"Project"`, `"Item"`, ou `"ProjectGroup"`). Obligatoire

### <a name="child-elements"></a>Éléments enfants

- **RelativePathOnDisk**: Le chemin relatif du fichier modèle sur disque. Cet emplacement définit également le placement du modèle dans l’arbre modèle indiqué dans le **nouveau projet** ou le dialogue **nouvel objet.** Pour les modèles déployés comme répertoire et fichiers individuels, ce chemin se réfère à l’annuaire contenant les fichiers de modèle. Pour les modèles déployés comme un fichier *.zip,* ce chemin doit être le chemin vers le fichier *.zip.*

- -VSTemplateHeader: Un élément [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) qui décrit l’en-tête.

### <a name="parent-element"></a>Élément parent
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Décrit le répertoire où se trouve le modèle. Un manifeste peut contenir plusieurs entrées **VSTemplateDir** pour fournir le nom localisé et trier la commande pour les répertoires pour contrôler leur apparence dans l’arbre de catégorie de modèle.

 En raison de leur conception, les entrées **VSTemplateDir** ne doivent apparaître que dans des manifestes non locaux spécifiés.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

- **RelativePath**: Le chemin du modèle. Il ne peut y avoir qu’une seule entrée par chemin, de sorte que la première va gagner pour tous les manifestes.

- **LocalizedName**: Un élément **NameDescriptionIcon** qui spécifie le nom localisé. facultatif.

- **SortOrder**: Une chaîne qui spécifie l’ordre de tri. facultatif.

- **ParentFolderOverrideName**: Le nom prédilité du dossier parent. facultatif. Cet élément a un attribut **de nom,** qui est une valeur de chaîne qui spécifie le nom.

### <a name="parent-element"></a>Élément parent
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NomDescriptionIcon
 Spécifie le nom et la description, éventuellement pour les modèles localisés. Voir **LocalizedName** ci-dessus.

### <a name="attributes"></a>Attributs

- **Forfait**: Une valeur de chaîne qui spécifie le paquet. facultatif.

- **ID**: Une valeur de chaîne qui spécifie l’ID. facultatif.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-element"></a>Élément parent
 **LocalizedName (en)**

## <a name="examples"></a>Exemples
 Le code suivant est un exemple d’un modèle de projet *.vstman* fichier.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Le code suivant est un exemple d’un fichier *.vstman* de modèle d’élément.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
