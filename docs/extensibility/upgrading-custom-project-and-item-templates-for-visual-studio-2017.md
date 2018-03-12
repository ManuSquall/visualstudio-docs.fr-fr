---
title: "La mise à niveau de projet personnalisés et les modèles d’élément pour Visual Studio 2017 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c0843c8bfb899dc23bcb1ce31eb3f8b9eaffd54
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>La mise à niveau de projet personnalisés et les modèles d’élément pour Visual Studio 2017

À partir de Visual Studio 2017, Visual Studio détecte les modèles de projet et d’élément qui ont été installés par un .vsix ou un fichier .msi d’une manière différente pour les versions précédentes de Visual Studio. Si vous possédez des extensions qui utilisent des modèles d’élément ou de projet personnalisé, vous devez mettre à jour vos extensions. Cette rubrique explique ce que vous devez faire.

Cette modification affecte uniquement de Visual Studio 2017. Il n’affecte pas les versions précédentes de Visual Studio.

Si vous souhaitez créer un modèle de projet ou un élément dans le cadre d’une extension VSIX, consultez [de création de projets et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Modèle d’analyse

Dans les versions précédentes de Visual Studio, **devenv /setup** ou **devenv /installvstemplates** analysé le disque local pour rechercher des modèles de projet et d’élément. À partir de Visual Studio 2017, l’analyse est effectuée uniquement pour l’emplacement au niveau de l’utilisateur. L’emplacement de niveau utilisateur par défaut est **%USERPROFILE%\Documents\\< version de Visual Studio\>\Templates\\**. Cet emplacement est utilisé pour les modèles générés par le **projet** > **exporter les modèles...**  commande, si le **importer automatiquement le modèle dans Visual Studio** option est sélectionnée dans l’Assistant.

Pour d’autres emplacements (non-utilisateur), vous devez inclure un fichier manifest(.vstman) qui spécifie l’emplacement et autres caractéristiques du modèle. Le fichier .vstman est généré en même temps que le fichier .vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un .vsix, vous pouvez pour cela en recompilant l’extension dans Visual Studio 2017. Mais si vous utilisez un fichier .msi, vous devez apporter les modifications manuellement. Pour obtenir la liste de ce que vous devez faire pour apporter ces modifications, consultez **mises à niveau des Extensions installées avec une. MSI** plus loin dans cette rubrique.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une Extension VSIX avec le projet ou des modèles d’élément  

1.  Ouvrez la solution dans Visual Studio 2017. Vous devrez mettre à niveau le code. Cliquez sur **OK**.  
  
2.  Une fois la mise à niveau terminée, vous devrez peut-être modifier la version de la cible de l’installation. Dans le projet VSIX, ouvrez le fichier source.extension.vsixmanifest, puis sélectionnez le **cibles d’installation** onglet. Si le **la plage de versions** champ est **[14.0]**, cliquez sur **modifier** et modifiez-le pour inclure de Visual Studio 2017. Par exemple, vous pouvez la définir **[14.0,15.0]** pour installer l’extension pour Visual Studio 2015 ou Visual Studio 2017, ou pour **[15.0]** pour l’installer à simplement de Visual Studio 2017.  
  
3.  Recompiler le code.  
  
4.  Fermez Visual Studio.  
  
5.  Installer l’extension VSIX.  
  
6.  Vous pouvez tester la mise à jour en procédant comme suit :  
  
    1.  Le fichier de l’analyse des modifications est activé par la clé de Registre suivante :  
  
         **reg ajouter hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Après avoir ajouté la clé, exécutez **devenv /installvstemplates**.  
  
    3.  Rouvrez Visual Studio. Vous devez rechercher votre modèle à l’emplacement prévu.  
  
    > [!NOTE]
    >  Les modèles de projet d’extensibilité Visual Studio ne sont pas disponibles lors de la clé de Registre est présente. Vous devez supprimer la clé de Registre (et réexécutez **devenv /installvstemplates**) pour pouvoir les utiliser.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement de modèles de projet et élément  
  
-   Évitez d’utiliser des fichiers de modèle compressé. Compressé de fichiers doivent être décompressés afin de récupérer les ressources et le contenu de modèle, par conséquent, elles seront costlier à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer l’initialisation de modèle. Pour les extensions VSIX, les tâches de génération de kit de développement logiciel seront automatiquement décompressez n’importe quel modèle compressé lors de la création du fichier VSIX.  
  
-   Évitez d’utiliser des entrées d’ID de package/de ressources pour le nom du modèle, la description, l’icône ou l’aperçu afin d’éviter les chargements d’assemblys de ressources inutiles lors de la découverte du modèle. Au lieu de cela, vous pouvez utiliser manifestes localisées pour créer une entrée de modèle pour chacun des paramètres régionaux, qui utilise des propriétés ou des noms localisés.  
  
-   Si vous incluez des modèles en tant qu’éléments de fichier, la génération du manifeste peut vous donne pas les résultats attendus. Dans ce cas, vous devez ajouter un manifeste généré manuellement au projet VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modifications des fichiers dans les modèles de projet et élément  
Nous montrent les points de différence entre les versions de Visual Studio 2017 des fichiers de modèle, Visual Studio 2015 qui vous pouvez de créer correctement les nouveaux fichiers.  
  
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
  
 Voici le fichier .vstman (vous pouvez le trouver dans le répertoire de manifeste du projet VSIX) qui résultent de la reconstruction du projet VSIX :  
  
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
  
 Voici le fichier .vstman (vous pouvez le trouver dans le répertoire de manifeste du projet VSIX) qui résultent de la reconstruction du projet VSIX :  
  
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
  
 Pour plus d’informations sur les différents éléments du fichier .vstman, consultez [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau pour les Extensions installées avec une. MSI

Certaines extensions de fichier MSI déploiement des modèles à l’emplacement des modèles courants tels que les éléments suivants :

- **\<Répertoire d’installation de Visual Studio > \Common7\IDE\\< ProjectTemplates/éléments personnalisés >**

- **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< projet/éléments personnalisés >**

Si votre extension effectue un déploiement MSI, vous avez besoin générer le manifeste de modèle manuellement et vous assurer qu’il est inclus dans le programme d’installation de l’extension. Comparez les exemples .vstman répertoriés ci-dessus et le [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

Vous devez créer des manifestes séparés pour les modèles de projet et d’élément, et ils doivent pointer vers la racine modèle active comme indiqué ci-dessus. Créez un manifeste par extension et les paramètres régionaux.

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes de détection de modèle](troubleshooting-template-discovery.md)  
[Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)