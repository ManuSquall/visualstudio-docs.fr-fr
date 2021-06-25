---
title: Informations de référence sur le schéma du manifeste de modèle Visual Studio | Microsoft Docs
description: Cette référence de schéma décrit le format des fichiers manifeste de modèle Visual Studio qui sont générés pour les modèles de projet ou d’élément Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905382"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Référence de schéma du manifeste de modèle Visual Studio
Ce schéma décrit le format des fichiers manifeste de modèle Visual Studio (*. vstman*) qui sont générés pour les modèles de projet ou d’élément Visual Studio. Le schéma décrit également l’emplacement et d’autres informations pertinentes sur le modèle.

 : Étant donné qu’il y a des répertoires d’éléments et de modèles de projet distincts, un manifeste ne doit jamais avoir une combinaison de modèles d’élément et de projet.

> [!IMPORTANT]
> Ce manifeste est disponible à partir de Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Élément VSTemplateManifest
 Élément racine du manifeste.

### <a name="attributes"></a>Attributs

- **Version**: chaîne représentant la version du manifeste de modèle. Obligatoire.

- **Paramètres régionaux**: chaîne représentant les paramètres régionaux ou les paramètres régionaux du manifeste de modèle. La valeur des paramètres régionaux s’applique à tous les modèles. Vous devez utiliser un manifeste distinct pour chaque paramètre régional. Optionnel.

### <a name="child-elements"></a>Éléments enfants

- **VSTemplateContainer** Facultatif.

- **VSTemplateDir** Facultatif.

### <a name="parent-element"></a>Élément parent
 Aucun.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Conteneur des éléments du manifeste du modèle. Un manifeste possède un conteneur de modèle pour chaque modèle qu’il définit.

### <a name="attributes"></a>Attributs
 **VSTemplateType**: valeur de chaîne qui spécifie le type du modèle ( `"Project"` , `"Item"` ou `"ProjectGroup"` ). Obligatoire

### <a name="child-elements"></a>Éléments enfants

- **RelativePathOnDisk**: chemin d’accès relatif du fichier de modèle sur le disque. Cet emplacement définit également le placement du modèle dans l’arborescence du modèle affichée dans la boîte de dialogue **nouveau projet** ou **nouvel élément** . Pour les modèles déployés en tant que répertoire et fichiers individuels, ce chemin d’accès fait référence au répertoire contenant les fichiers de modèle. Pour les modèles déployés en tant que *.zip* fichier, ce chemin d’accès doit être le chemin d’accès au fichier *.zip* .

- * * VSTemplateHeader : élément [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) qui décrit l’en-tête.

### <a name="parent-element"></a>Élément parent
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Décrit le répertoire où se trouve le modèle. Un manifeste peut contenir plusieurs entrées **VSTemplateDir** pour fournir un nom localisé et un ordre de tri des répertoires afin de contrôler leur apparence dans l’arborescence des catégories de modèles.

 En raison de leur conception, les entrées **VSTemplateDir** ne doivent apparaître que dans les manifestes non locaux spécifiés.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

- **RelativePath**: chemin d’accès du modèle. Il ne peut y avoir qu’une seule entrée par chemin d’accès, donc la première est gagnante pour tous les manifestes.

- **LocalizedName**: élément **NameDescriptionIcon** qui spécifie le nom localisé. Optionnel.

- **SortOrder**: chaîne qui spécifie l’ordre de tri. Optionnel.

- **ParentFolderOverrideName**: nom substitué du dossier parent. Optionnel. Cet élément a un attribut **Name** , qui est une valeur de chaîne qui spécifie le nom.

### <a name="parent-element"></a>Élément parent
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Spécifie le nom et la description, éventuellement pour les modèles localisés. Consultez la section **LocalizedName** ci-dessus.

### <a name="attributes"></a>Attributs

- **Package**: valeur de chaîne qui spécifie le package. Optionnel.

- **ID**: valeur de chaîne qui spécifie l’ID. Optionnel.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-element"></a>Élément parent
 **LocalizedName**

## <a name="examples"></a>Exemples
 Le code suivant est un exemple de fichier de modèle de projet *. vstman* .

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

 Le code suivant est un exemple de fichier *. vstman* de modèle d’élément.

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
