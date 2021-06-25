---
title: Mettre à niveau des modèles de projet et d’élément personnalisés pour Visual Studio 2017
titleSuffix: ''
description: Découvrez comment mettre à jour votre modèle de projet et d’élément personnalisé à partir de versions précédentes du kit de développement logiciel (SDK) Visual Studio pour les utiliser avec Visual Studio 2017 et versions ultérieures.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903058"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Mettre à niveau un Modèles de projet et d’élément pour Visual Studio personnalisé 2017

À compter de Visual Studio 2017, Visual Studio Découvre les modèles de projet et d’élément qui ont été installés par un. VSIX ou un .msi d’une manière différente des versions précédentes de Visual Studio. Si vous possédez des extensions qui utilisent des modèles de projet ou d’élément personnalisés, vous devez mettre à jour vos extensions. Cet article explique ce que vous devez faire.

Cette modification affecte uniquement Visual Studio 2017. Elle n’affecte pas les versions précédentes de Visual Studio.

Si vous souhaitez créer un modèle de projet ou d’élément dans le cadre d’une extension VSIX, consultez [création de modèles de projet et d’élément personnalisés](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Analyse de modèle

Dans les versions précédentes de Visual Studio, **devenv/setup** ou **devenv/installvstemplates** a analysé le disque local pour trouver des modèles de projet et d’élément. À compter de Visual Studio 2017, l’analyse est effectuée uniquement pour l’emplacement au niveau de l’utilisateur. L’emplacement par défaut au niveau de l’utilisateur est **%USERPROFILE%\Documents \\<Visual Studio version \> \Templates \\**. Cet emplacement est utilisé pour les modèles générés par la commande exporter des modèles de **projet**  >  **.** .. si l’option **importer automatiquement le modèle dans Visual Studio** est sélectionnée dans l’Assistant.

Pour les autres emplacements (non-utilisateur), vous devez inclure un fichier manifeste (. vstman) qui spécifie l’emplacement et d’autres caractéristiques du modèle. Le fichier. vstman est généré avec le fichier. vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un. vsix, vous pouvez le faire en recompilant l’extension dans Visual Studio 2017. Toutefois, si vous utilisez un .msi, vous devez apporter les modifications manuellement. Pour obtenir une liste de ce que vous devez faire pour apporter ces modifications, consultez  **mises à niveau pour les extensions installées avec un .MSI** plus loin dans cette page.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une extension VSIX avec des modèles de projet ou d’élément

1. Ouvrez la solution dans Visual Studio 2017. Vous serez invité à mettre à niveau le code. Cliquez sur **OK**.

2. Une fois la mise à niveau terminée, vous devrez peut-être modifier la version de la cible d’installation. Dans le projet VSIX, ouvrez le fichier source. extension. vsixmanifest et sélectionnez l’onglet **installer les cibles** . Si le champ **plage de versions** est **[14,0]**, cliquez sur **modifier** et modifiez-le pour inclure Visual Studio 2017. Par exemple, vous pouvez lui affecter la valeur **[14.0, 15]** pour installer l’extension sur visual studio 2015 ou visual studio 2017, ou sur **[15,0]** pour l’installer dans Visual Studio 2017 uniquement.

3. Recompilez le code.

4. Fermez Visual Studio.

5. Installez le VSIX.

6. Vous pouvez tester la mise à jour en procédant comme suit :

    1. La modification de l’analyse des fichiers est activée par la clé de Registre suivante :

         **Reg Add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/Reg : 32**

    2. Après avoir ajouté la clé, exécutez **devenv/installvstemplates**.

    3. Rouvrez Visual Studio. Vous devez trouver votre modèle à l’emplacement attendu.

    > [!NOTE]
    > Les modèles de projet d’extensibilité Visual Studio ne sont pas disponibles lorsque la clé de Registre est présente. Vous devez supprimer la clé de Registre (et réexécuter **devenv/installvstemplates**) pour les utiliser.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement de modèles de projet et d’élément

- Évitez d’utiliser des fichiers de modèle Zippés. Les fichiers de modèle Zippés doivent être décompressés pour pouvoir récupérer des ressources et du contenu, de sorte qu’ils seront sont coûteuses à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer l’initialisation du modèle. Pour les extensions VSIX, les tâches de génération du kit de développement logiciel décompressent automatiquement tout modèle compressé lors de la création du fichier VSIX.

- Évitez d’utiliser des entrées d’ID de package/ressource pour le nom du modèle, la description, l’icône ou l’aperçu afin d’éviter des chargements d’assembly de ressources inutiles pendant la découverte du modèle. Au lieu de cela, vous pouvez utiliser des manifestes localisés pour créer une entrée de modèle pour chaque paramètre régional, qui utilise des noms localisés ou des propriétés.

- Si vous incluez des modèles en tant qu’éléments de fichier, la génération de manifeste peut ne pas vous fournir les résultats attendus. Dans ce cas, vous devrez ajouter un manifeste généré manuellement au projet VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Modifications de fichiers dans les modèles de projet et d’élément
Nous présentons les points de différence entre les versions Visual Studio 2015 et Visual Studio 2017 des fichiers modèles, afin que vous puissiez créer correctement les nouveaux fichiers.

 Voici le fichier Project. vstemplate par défaut créé par Visual Studio 2015 :

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Voici le fichier. vstman (vous pouvez le trouver dans le répertoire du manifeste du projet VSIX) qui résulte de la reconstruction du projet VSIX :

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Les informations fournies par l’élément [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) restent les mêmes. L' **\<VSTemplateContainer>** élément pointe vers le fichier. vstemplate pour le modèle associé.

 Voici le fichier Item. vstemplate par défaut créé par Visual Studio 2015 :

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Voici le fichier. vstman (vous pouvez le trouver dans le répertoire du manifeste du projet VSIX) qui résulte de la reconstruction du projet VSIX :

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

 Les informations fournies par l' **\<TemplateData>** élément restent les mêmes. L' **\<VSTemplateContainer>** élément pointe vers le fichier. vstemplate pour le modèle associé.

 Pour plus d’informations sur les différents éléments du fichier. vstman, consultez [Référence du schéma du manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau pour les extensions installées avec un .MSI

Certaines extensions MSI déploient des modèles dans des emplacements de modèles communs, tels que les répertoires suivants :

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/éléments personnalisés\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<projet/éléments personnalisés\>**

Si votre extension effectue un déploiement basé sur MSI, vous devez générer manuellement le manifeste de modèle et vous assurer qu’il est inclus dans le programme d’installation de l’extension. Comparez les exemples. vstman listés ci-dessus et la [référence de schéma du manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Créez des manifestes distincts pour les modèles de projet et d’élément, et ils doivent pointer vers le répertoire de modèle racine comme indiqué ci-dessus. Créez un manifeste par extension et par paramètres régionaux.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de découverte de modèles](troubleshooting-template-discovery.md)
- [Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)
