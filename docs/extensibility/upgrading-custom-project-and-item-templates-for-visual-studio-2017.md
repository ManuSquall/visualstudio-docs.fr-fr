---
title: Mettre à niveau des modèles de projets et d’objets personnalisés pour Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698856"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Améliorer les modèles de projets et d’objets personnalisés pour Visual Studio 2017

À partir de Visual Studio 2017, Visual Studio découvre des modèles de projets et d’objets qui ont été installés par un .vsix ou un .msi d’une manière différente des versions précédentes de Visual Studio. Si vous possédez des extensions qui utilisent des modèles de projet ou d’éléments personnalisés, vous devez mettre à jour vos extensions. Cet article explique ce que vous devez faire.

Ce changement n’affecte que Visual Studio 2017. Il n’affecte pas les versions précédentes de Visual Studio.

Si vous souhaitez créer un modèle de projet ou d’élément dans le cadre d’une extension VSIX, consultez [Les modèles de projets et d’objets personnalisés](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Numérisation de modèle

Dans les versions précédentes de Visual Studio, **devenv/setup** ou **devenv/installvstemplates** numérisé le disque local pour trouver des modèles de projet et d’élément. À partir de Visual Studio 2017, la numérisation n’est effectuée que pour l’emplacement au niveau de l’utilisateur. L’emplacement par défaut au niveau de l’utilisateur est **%USERPROFILE% -Documents\\<version\>Visual Studio 'Templates\\**. Cet emplacement est utilisé pour les modèles générés par les**modèles d’exportation** **de projet** > ... commande, si **l’importation automatique du modèle dans l’option Visual Studio** est sélectionnée dans l’assistant.

Pour d’autres emplacements (non-utilisateurs), vous devez inclure un fichier manifeste (.vstman) qui spécifie l’emplacement et d’autres caractéristiques du modèle. Le fichier .vstman est généré avec le fichier .vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un .vsix, vous pouvez y parvenir en recompilant l’extension dans Visual Studio 2017. Mais si vous utilisez un .msi, vous devez faire les modifications manuellement. Pour une liste de ce que vous devez faire pour effectuer ces **modifications, voir Mises à niveau pour les extensions installées avec un . MSI** plus tard sur cette page.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une extension VSIX avec des modèles de projet ou d’article

1. Ouvrez la solution dans Visual Studio 2017. Il vous sera demandé de mettre à niveau le code. Cliquez sur **OK**.

2. Une fois la mise à niveau terminée, vous devrez peut-être modifier la version de la cible d’installation. Dans le cadre du projet VSIX, ouvrez le fichier source.extension.vsixmanifest et sélectionnez **l’onglet Cibles d’installation.** Si le champ **De gamme de version** est **[14.0]**, cliquez sur **Edit** et changez-le pour inclure Visual Studio 2017. Par exemple, vous pouvez le régler à **[14.0,15.0]** pour installer l’extension à Visual Studio 2015 ou Visual Studio 2017, ou à **[15.0]** pour l’installer à just Visual Studio 2017.

3. Recomposer le code.

4. Fermez Visual Studio.

5. Installer le VSIX.

6. Vous pouvez tester la mise à jour en faisant ce qui suit :

    1. Le changement de numérisation de fichiers est activé par la clé de registre suivante :

         **reg ajouter hklm-software-microsoft-visualstudio-15.0 -VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Après avoir ajouté la clé, exécutez **devenv /installvstemplates**.

    3. Rouvrir Visual Studio. Vous devez trouver votre modèle à l’emplacement prévu.

    > [!NOTE]
    > Les modèles de projet Visual Studio Extensibility ne sont pas disponibles lorsque la clé du registre est présente. Vous devez supprimer la clé de registre (et rejouer **devenv /installvstemplates**) pour les utiliser.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement des modèles de projets et d’objets

- Évitez d’utiliser des fichiers modèles zippés. Les fichiers de modèles zippés doivent être non compressés afin de récupérer les ressources et le contenu, de sorte qu’ils seront plus coûteux à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer l’initialisation du modèle. Pour les extensions VSIX, les tâches de construction SDK déziperont automatiquement n’importe quel modèle zippé tout en créant le fichier VSIX.

- Évitez d’utiliser des entrées d’identification de paquet/ressource pour le nom, la description, l’icône ou l’aperçu du modèle afin d’éviter les charges inutiles d’assemblage de ressources pendant la découverte du modèle. Au lieu de cela, vous pouvez utiliser des manifestes localisés pour créer une entrée de modèle pour chaque lieu, qui utilise des noms ou des propriétés localisés.

- Si vous y trouvez des modèles comme éléments de fichiers, la génération manifeste pourrait ne pas vous donner les résultats escomptés. Dans ce cas, vous devrez ajouter un manifeste généré manuellement au projet VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Modifications de fichiers dans les modèles de projets et d’éléments
Nous montrons les points de différence entre les versions Visual Studio 2015 et Visual Studio 2017 des fichiers de modèle, afin que vous puissiez créer les nouveaux fichiers correctement.

 Voici le fichier par défaut .vstemplate créé par Visual Studio 2015 :

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

 Voici le fichier .vstman (vous pouvez le trouver dans l’annuaire manifeste du projet VSIX) qui a résulté de la reconstruction du projet VSIX:

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

 Les informations fournies par l’élément [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) restent les mêmes. Le ** \<VSTemplateContainer>** élément indique le fichier .vstemplate pour le modèle associé.

 Voici le fichier .vstemplate par défaut créé par Visual Studio 2015 :

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

 Voici le fichier .vstman (vous pouvez le trouver dans l’annuaire manifeste du projet VSIX) qui a résulté de la reconstruction du projet VSIX:

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

 Les informations fournies par l’élément ** \<TemplateData>** restent les mêmes. Le ** \<vsTemplateContainer>** élément indique le fichier .vstemplate pour le modèle associé

 Pour plus d’informations sur les différents éléments du fichier .vstman, voir [Visual Studio Template Manifest Schema Référence](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau pour les extensions installées avec un . Msi

Certaines extensions basées sur MSI déploient des modèles à des emplacements de modèles communs tels que les répertoires suivants :

- **\<Répertoire d’installation Visual Studio>-Common7-IDE\\<ProjectTemplates/ItemTemplates\>**

- **\<Répertoire d’installation visual Studio>-Common7-IDE-Extensions\\<ExtensionName\> \\<Project/ItemTemplates\>**

Si votre extension effectue un déploiement basé sur MSI, vous devez générer le manifeste du modèle manuellement et vous assurer qu’il est inclus dans la configuration d’extension. Comparez les exemples .vstman énumérés ci-dessus et le [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

Créez des manifestes distincts pour les modèles de projets et d’éléments, et ils devraient indiquer le répertoire de modèle racine comme spécifié ci-dessus. Créez un manifeste par extension et local.

## <a name="see-also"></a>Voir aussi

- [Découverte de modèles de dépannage](troubleshooting-template-discovery.md)
- [Création de modèles de projets et d’objets personnalisés](creating-custom-project-and-item-templates.md)
