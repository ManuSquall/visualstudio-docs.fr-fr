---
title: Mettre à niveau des modèles de projet et d’élément personnalisés pour Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 39dbe74c8f59171461cca04fc9015782e21fe9da
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261802"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Mise à niveau de projet personnalisés et les modèles d’élément pour Visual Studio 2017

À partir de Visual Studio 2017, Visual Studio détecte les modèles de projet et d’élément qui ont été installés par un .vsix ou un fichier .msi d’une façon différente aux versions précédentes de Visual Studio. Si vous possédez des extensions qui utilisent des modèles d’élément ou de projet personnalisé, vous devez mettre à jour vos extensions. Cet article explique la marche à suivre.

Cette modification affecte uniquement Visual Studio 2017. Il n’affecte pas les versions précédentes de Visual Studio.

Si vous souhaitez créer un modèle de projet ou un élément dans le cadre d’une extension VSIX, consultez [création personnalisée de projet et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Modèle d’analyse

Dans les versions précédentes de Visual Studio, **devenv /setup** ou **devenv /installvstemplates** analysé le disque local pour rechercher les modèles de projet et d’élément. À partir de Visual Studio 2017, l’analyse est effectuée uniquement pour l’emplacement au niveau de l’utilisateur. L’emplacement de niveau utilisateur par défaut est **%USERPROFILE%\Documents\\< version de Visual Studio\>\Templates\\** . Cet emplacement est utilisé pour les modèles générés par le **projet** > **exporter les modèles...**  commande, si le **importer automatiquement le modèle dans Visual Studio** option est sélectionnée dans l’Assistant.

Pour d’autres emplacements (non utilisateur), vous devez inclure un fichier manifest(.vstman) qui spécifie l’emplacement et autres caractéristiques du modèle. Le fichier .vstman est généré en même temps que le fichier .vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un .vsix, faire cela en recompilant de l’extension dans Visual Studio 2017. Mais si vous utilisez un fichier .msi, vous devez apporter les modifications manuellement. Pour obtenir la liste de ce que vous devez faire pour que ces modifications, consultez **mises à niveau pour les Extensions installées avec une. MSI** par la suite de cette page.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une Extension VSIX avec un projet ou des modèles d’élément

1. Ouvrez la solution dans Visual Studio 2017. Vous devrez mettre à niveau le code. Cliquez sur **OK**.

2. Une fois la mise à niveau terminée, vous devrez peut-être modifier la version de la cible d’installation. Dans le projet VSIX, ouvrez le fichier source.extension.vsixmanifest, puis sélectionnez le **cibles d’installation** onglet. Si le **plage de versions** champ est **[14.0]** , cliquez sur **modifier** et modifiez-le pour inclure Visual Studio 2017. Par exemple, vous pouvez la définir **[14.0,15.0]** pour installer l’extension pour Visual Studio 2015 ou Visual Studio 2017, ou pour **[15.0]** pour l’installer dans Visual Studio 2017 uniquement.

3. Recompilez le code.

4. Fermez Visual Studio.

5. Installer l’extension VSIX.

6. Vous pouvez tester la mise à jour en procédant comme suit :

    1. L’analyse de modification des fichiers sont activé par la clé de Registre suivante :

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Après avoir ajouté la clé, exécutez **devenv /installvstemplates**.

    3. Rouvrez Visual Studio. Vous devez rechercher votre modèle à l’emplacement prévu.

    > [!NOTE]
    > Les modèles de projet d’extensibilité de Visual Studio ne sont pas disponibles lors de la clé de Registre est présente. Vous devez supprimer la clé de Registre (et réexécutez **devenv /installvstemplates**) pour les utiliser.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement de Project and Item Templates

- Évitez d’utiliser des fichiers de modèle zippé. Compresser les fichiers doivent être décompressés afin de récupérer les ressources et le contenu de modèle, par conséquent, ils seront sont coûteuses à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer l’initialisation du modèle. Pour les extensions VSIX, les tâches de génération SDK décompresse automatiquement n’importe quel modèle zippé lors de la création du fichier VSIX.

- Évitez d’utiliser des entrées d’ID de package/de ressources pour le nom du modèle, la description, l’icône ou afficher un aperçu afin d’éviter les chargements d’assemblys de ressources inutiles lors de la découverte du modèle. Au lieu de cela, vous pouvez utiliser des manifestes localisées pour créer une entrée de modèle pour chacun des paramètres régionaux, qui utilise des propriétés ou des noms localisés.

- Si vous incluez des modèles en tant qu’éléments de fichier, génération de manifeste ne peut pas vous donner les résultats attendus. Dans ce cas, vous devrez ajouter un manifeste généré manuellement au projet VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Modification des fichiers projet et des modèles d’élément
Nous montrons les points de différence entre le Visual Studio 2015 et Visual Studio 2017 versions des fichiers de modèle, afin que vous puissiez créer correctement les nouveaux fichiers.

 Voici le fichier .vstemplate de projet par défaut créé par Visual Studio 2015 :

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

 Voici le fichier .vstman (vous pouvez le trouver dans le répertoire de manifeste du projet VSIX) résultant de la reconstruction du projet VSIX :

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

 Les informations fournies par le [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) élément reste le même. Le  **\<VSTemplateContainer >** élément pointe vers le fichier .vstemplate pour le modèle associé.

 Voici le fichier .vstemplate d’élément par défaut créé par Visual Studio 2015 :

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

 Voici le fichier .vstman (vous pouvez le trouver dans le répertoire de manifeste du projet VSIX) résultant de la reconstruction du projet VSIX :

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

 Les informations fournies par le  **\<TemplateData >** élément reste le même. Le  **\<VSTemplateContainer >** élément pointe vers le fichier .vstemplate pour le modèle associé

 Pour plus d’informations sur les différents éléments du fichier .vstman, consultez [référence modèle Visual Studio Manifest schéma](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau pour les Extensions installées avec une. MSI

Certaines extensions basées sur MSI déploiement des modèles dans les emplacements des modèles courants tels que les répertoires suivants :

- **\<Répertoire d’installation de Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**

- **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< projet/ItemTemplates >**

Si votre extension effectue un déploiement basé sur MSI, vous devez générer le manifeste de modèle manuellement et vous assurer qu’il est inclus dans le programme d’installation de l’extension. Comparer les exemples .vstman répertoriés ci-dessus et le [référence modèle Visual Studio Manifest schéma](../extensibility/visual-studio-template-manifest-schema-reference.md).

Créez des manifestes séparés pour les modèles de projet et d’élément, et ils doivent pointer vers la racine modèle répertoire tel que spécifié ci-dessus. Créez un manifeste par extension et les paramètres régionaux.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de découverte de modèles](troubleshooting-template-discovery.md)
- [Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)
