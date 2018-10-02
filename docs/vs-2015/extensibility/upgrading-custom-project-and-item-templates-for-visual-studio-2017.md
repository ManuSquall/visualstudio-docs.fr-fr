---
title: Mise à niveau des modèles de projets et modèles d’élément pour Visual Studio « 15 » | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02c7b14051a41616ed1b98812d1f1b7762f7165e
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "47590900"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Mise à niveau des modèles de projets et modèles d’élément pour Visual Studio « 15 »
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Upgrading Custom Project et des modèles d’élément pour Visual Studio ](https://docs.microsoft.com/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017).  
  
À compter de Visual Studio « 15 » Preview 4, Visual Studio modifie la façon qu’il découvre les modèles de projet et d’élément qui ont été installés par un .vsix ou un fichier .msi. Si vous possédez des extensions qui utilisent des modèles d’élément ou de projet personnalisé, vous devez mettre à jour vos extensions. Cette rubrique explique la marche à suivre.  
  
 Cette modification affecte uniquement Visual Studio « 15 ». Il n’affecte pas les versions précédentes de Visual Studio.  
  
 Si vous souhaitez créer un modèle de projet ou un élément dans le cadre d’une extension VSIX, consultez [création personnalisée de projet et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Modèle d’analyse  
 Auparavant, **devenv /setup** ou **devenv /installvstemplates** analysé le disque local pour rechercher les modèles de projet et d’élément. À compter de Preview 4, l’analyse est effectuée uniquement pour l’emplacement au niveau de l’utilisateur (**%USERPROFILE%\Documents\\< version de Visual Studio\>\My Exported Templates\\**) qui est utilisé pour les modèles générés par le **fichier / exporter des modèles** commande.  
  
 Pour d’autres emplacements (non utilisateur), vous devez inclure un fichier manifest(.vstman) qui spécifie l’emplacement et autres caractéristiques du modèle. Le fichier .vstman est généré en même temps que le fichier .vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un .vsix, faire cela en recompilant de l’extension dans Visual Studio « 15 » Preview 2. Mais si vous utilisez un fichier .msi, vous devez apporter les modifications manuellement. Pour obtenir la liste de ce que vous devez faire pour que ces modifications, consultez **mises à niveau pour les Extensions installées avec une. MSI** plus loin dans cette rubrique.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une Extension VSIX avec un projet ou des modèles d’élément  
 Cette procédure explique comment faire en sorte de mise à jour de Visual Studio « 15 » Preview 2 votre extension VSIX existante.  
  
1.  Ouvrez la solution dans Visual Studio « 15 » Preview 2. Vous devrez mettre à niveau le code. Cliquez sur **OK**.  
  
2.  Une fois la mise à niveau terminée, vous devrez peut-être modifier la version de la cible d’installation. Dans le projet VSIX, ouvrez le fichier source.extension.vsixmanifest, puis sélectionnez le **cibles d’installation** onglet. Si le **plage de versions** champ est **[14.0]**, cliquez sur **modifier** et modifiez-le pour inclure Visual Studio « 15 ». Par exemple, vous pouvez la définir **[14.0,15.0]** pour installer l’extension pour Visual Studio 2015 ou Visual Studio « 15 », ou pour **[15.0]** pour l’installer dans Visual Studio « 15 ».  
  
3.  Recompilez le code.  
  
4.  Fermez Visual Studio.  
  
5.  Installer l’extension VSIX.  
  
6.  Vous pouvez tester la mise à jour en procédant comme suit :  
  
    1.  L’analyse de modification des fichiers sont activé par la clé de Registre suivante :  
  
         **reg ajouter hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Après avoir ajouté la clé, exécutez **devenv /installvstemplates**.  
  
    3.  Rouvrez Visual Studio. Vous devez rechercher votre modèle à l’emplacement prévu.  
  
    > [!NOTE]
    >  Les modèles de projet d’extensibilité de Visual Studio ne sont pas disponibles lors de la clé de Registre est présente. Vous devez supprimer la clé de Registre (et réexécutez **devenv /installvstemplates**) pour les utiliser.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement de Project and Item Templates  
  
-   Évitez d’utiliser des fichiers de modèle zippé. Compresser les fichiers doivent être décompressés afin de récupérer les ressources et le contenu de modèle, par conséquent, ils seront sont coûteuses à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer l’initialisation du modèle. Pour les extensions VSIX, les tâches de génération SDK décompresse automatiquement n’importe quel modèle zippé lors de la création du fichier VSIX.  
  
-   Évitez d’utiliser des entrées d’ID de package/de ressources pour le nom du modèle, la description, l’icône ou l’aperçu afin d’éviter les chargements d’assemblys de ressources inutiles lors de la découverte du modèle. Au lieu de cela, vous pouvez utiliser des manifestes localisées pour créer une entrée de modèle pour chacun des paramètres régionaux, qui utilise des propriétés ou des noms localisés.  
  
-   Si vous incluez des modèles en tant qu’éléments de fichier, génération de manifeste ne peut pas vous donner les résultats attendus. Dans ce cas, vous devrez ajouter un manifeste généré manuellement au projet VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modification des fichiers projet et des modèles d’élément  
 Nous allons montrer les points de différence entre la version de Visual Studio 2015 et la version de Visual Studio « 15 » des fichiers de modèle, afin que vous puissiez créer correctement les nouveaux fichiers.  
  
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
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 Les informations fournies par le  **\<TemplateData >** élément reste le même. Le  **\<VSTemplateContainer >** élément pointe vers le fichier .vstemplate pour le modèle associé  
  
 Pour plus d’informations sur les différents éléments du fichier .vstman, consultez [référence modèle Visual Studio Manifest schéma](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau pour les Extensions installées avec une. MSI  
 Certaines extensions basées sur MSI déploiement des modèles dans les emplacements des modèles courants tels que les éléments suivants :  
  
-   **\<Répertoire d’installation de Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**  
  
-   **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< projet/ItemTemplates >**  
  
 Si votre extension effectue un déploiement basé sur MSI, vous devez générer le manifeste de modèle manuellement et vous assurer qu’il est inclus dans le programme d’installation de l’extension. Vous devez comparer les exemples .vstman répertoriés ci-dessus et le [référence modèle Visual Studio Manifest schéma](../extensibility/visual-studio-template-manifest-schema-reference.md). Pour voir ce que vous devez inclure  
  
 Vous devez créer les manifestes distincts pour les modèles de projet et d’élément, et ils doivent pointer vers la racine modèle répertoire tel que spécifié ci-dessus. Vous devez créer un seul manifeste par extension et les paramètres régionaux.  
  
## <a name="troubleshooting-template-installation"></a>Résolution des problèmes d’Installation du modèle  
 Si vous rencontrez des problèmes de déploiement de vos modèles de projet ou un élément, vous pouvez activer la journalisation des Diagnostics.  
  
1.  Exécutez la commande suivante pour définir la clé de Registre pour activer la journalisation :  
  
     **reg ajouter HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Démarrez Visual Studio et lancer les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle. Le journal de modèle s’affiche désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. L’initialisation de chaque arborescence de modèle ajoute des entrées dans ce fichier journal.  
  
 Le fichier journal contient les colonnes suivantes :  
  
-   **FullPathToTemplate**, qui a les valeurs suivantes :  
  
    -   1 pour le déploiement basé sur les manifestes  
  
    -   0 pour le déploiement basé sur le disque  
  
-   **TemplateFileName**  
  
-   Autres propriétés de modèle

