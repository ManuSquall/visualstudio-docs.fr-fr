---
title: "Référence du schéma de manifeste de modèle Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 87f676ef30da7c667c4ce2b688520a49ed1931c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Référence de schéma de manifeste de modèle Visual Studio
Ce schéma décrit le format des fichiers de manifeste (.vstman) de modèle Visual Studio générés pour les modèles de projet ou un élément de Visual Studio et décrit l’emplacement et autres informations pertinentes relatives au modèle.  
  
 : Étant donné qu’élément distinct et les répertoires de modèle de projet, un manifeste doit avoir jamais une combinaison des modèles de projet et d’élément.  
  
> [!IMPORTANT]
>  Ce manifeste n’est disponible à partir de Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Élément de VSTemplateManifest  
 L’élément racine du manifeste.  
  
### <a name="attributes"></a>Attributs  
  
-   **Version**: une chaîne qui représente la version du manifeste de modèle. Obligatoire.  
  
-   **Paramètres régionaux**: une chaîne qui représente les paramètres régionaux ou les paramètres régionaux du manifeste de modèle. La valeur de paramètres régionaux s’applique à tous les modèles, vous devez utiliser un manifeste distinct pour chacun des paramètres régionaux. Facultatif.  
  
### <a name="child-elements"></a>Éléments enfants  
  
-   **VSTemplateContainer** facultatif.  
  
-   **VSTemplateDir** facultatif.  
  
### <a name="parent-element"></a>Parent, élément  
 Aucun.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Le conteneur du modèle de manifeste des éléments. Un manifeste est un conteneur de modèle pour chaque modèle, qu'il définit.  
  
### <a name="attributes"></a>Attributs  
 **VSTemplateType** : une valeur de chaîne qui spécifie le type du modèle (`"Project"`, `"Item"`, ou `"ProjectGroup"`). Obligatoire  
  
### <a name="child-elements"></a>Éléments enfants  
  
-   **RelativePathOnDisk**: le chemin d’accès relatif du fichier de modèle sur le disque. Cet emplacement définit également la position du modèle dans l’arborescence de modèle indiqué dans le **nouveau projet** ou **un nouvel élément** boîte de dialogue. Pour les modèles déployés en tant qu’un répertoire et les fichiers individuels, ce chemin d’accès fait référence au répertoire contenant les fichiers de modèle. Pour les modèles déployés en tant qu’un fichier .zip, ce chemin d’accès doit être le chemin d’accès au fichier .zip.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) élément qui décrit l’en-tête.  
  
### <a name="parent-element"></a>Parent, élément  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Décrit le répertoire où se trouve le modèle. Un manifeste peut contenir plusieurs **VSTemplateDir** entrées pour fournir le nom localisé et ordre pour les répertoires de tri pour contrôler leur aspect dans l’arborescence des catégories de modèle.  
  
 En raison de leur conception, **VSTemplateDir** entrées doivent apparaître uniquement dans les types de paramètres régionaux des manifestes spécifiés.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
-   **RelativePath**: le chemin d’accès du modèle. Il peut y avoir qu’une seule entrée par le chemin d’accès, pour la première condition précédente pour tous les manifestes.  
  
-   **LocalizedName**: A **NameDescriptionIcon** élément qui spécifie le nom localisé. Facultatif.  
  
-   **SortOrder** : chaîne qui spécifie l’ordre de tri. Facultatif.  
  
-   **ParentFolderOverrideName**: le nom du dossier parent de substituée. Facultatif. Cet élément a un **nom** attribut, qui est une valeur de chaîne qui spécifie le nom.  
  
### <a name="parent-element"></a>Parent, élément  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Spécifie le nom et la description, éventuellement pour les modèles localisés. Consultez **LocalizedName** ci-dessus.  
  
### <a name="attributes"></a>Attributs  
  
-   **Package**: une valeur de chaîne qui spécifie le package. Facultatif.  
  
-   **ID**: une valeur de chaîne qui spécifie l’ID. Facultatif.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-element"></a>Parent, élément  
 **LocalizedName**  
  
## <a name="examples"></a>Exemples  
 Voici un exemple d’un fichier de .vstman de modèle de projet.  
  
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
  
 Voici un exemple d’un fichier de modèle d’élément .vstman.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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