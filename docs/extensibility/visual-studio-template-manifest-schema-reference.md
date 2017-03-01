---
title: "Référence du schéma de manifeste de modèle Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Référence de schéma de manifeste de modèle Visual Studio
Ce schéma décrit le format des fichiers manifeste (.vstman) des modèles Visual Studio généré pour les modèles de projet ou un élément de Visual Studio et décrit l’emplacement et autres informations pertinentes concernant le modèle.  
  
 : Étant donné qu’élément distinct et les répertoires de modèle de projet, un manifeste doit avoir jamais une combinaison des modèles de projet et d’élément.  
  
> [!IMPORTANT]
>  Ce manifeste est disponible à partir de Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Élément de VSTemplateManifest  
 L’élément racine du manifeste.  
  
### <a name="attributes"></a>Attributs  
  
-   **Version**: une chaîne représentant la version du manifeste de modèle. Obligatoire.  
  
-   **Paramètres régionaux**: chaîne représentant les paramètres régionaux ou paramètres régionaux du manifeste de modèle. La valeur des paramètres régionaux s’applique à tous les modèles, vous devez donc utiliser un manifeste distinct pour chaque paramètre régional. Facultatif.  
  
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
  
-   **RelativePathOnDisk**: le chemin d’accès relatif du fichier de modèle sur le disque. Cet emplacement définit également la position du modèle dans l’arborescence de modèle indiqué dans le **nouveau projet** ou **un nouvel élément** boîte de dialogue. Pour les modèles déployés comme un répertoire et les fichiers individuels, ce chemin d’accès fait référence au répertoire contenant les fichiers de modèle. Pour les modèles déployés en tant que fichier .zip, ce chemin d’accès doit être le chemin d’accès au fichier .zip.  
  
-   **VSTemplateHeader** : un [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) élément qui décrit l’en-tête.  
  
### <a name="parent-element"></a>Parent, élément  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Décrit le répertoire où se trouve le modèle. Un manifeste peut contenir plusieurs **VSTemplateDir** entrées pour fournir le nom localisé et l’ordre des répertoires de tri pour contrôler leur apparence dans l’arborescence de catégorie de modèle.  
  
 En raison de leur conception, **VSTemplateDir** entrées doivent apparaître uniquement dans les types de paramètres régionaux des manifestes spécifiés.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
-   **RelativePath**: le chemin d’accès du modèle. Il peut y avoir qu’une seule entrée par le chemin d’accès, donc l’emportera pour tous les manifestes.  
  
-   **LocalizedName**: un **NameDescriptionIcon** élément qui spécifie le nom localisé. Facultatif.  
  
-   **SortOrder** : chaîne qui spécifie l’ordre de tri. Facultatif.  
  
-   **ParentFolderOverrideName**: le nom du dossier parent substitué. Facultatif. Cet élément a un **nom** attribut, qui est une valeur de chaîne qui spécifie le nom.  
  
### <a name="parent-element"></a>Parent, élément  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Spécifie le nom et la description, éventuellement pour les modèles localisés. Consultez la page **LocalizedName** ci-dessus.  
  
### <a name="attributes"></a>Attributs  
  
-   **Package**: valeur de chaîne qui spécifie le package. Facultatif.  
  
-   **ID**: une valeur de chaîne qui spécifie le code. Facultatif.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-element"></a>Parent, élément  
 **LocalizedName**  
  
## <a name="examples"></a>Exemples  
 Voici un exemple de fichier de .vstman d’un modèle de projet.  
  
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
