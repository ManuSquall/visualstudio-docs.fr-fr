---
title: "Mise à niveau de projet personnalisés et les modèles d’élément pour Visual Studio « 15 » | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
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
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>La mise à niveau de projet personnalisés et les modèles d’élément pour Visual Studio 2017
À partir de Visual Studio 2017, Visual Studio modifie la façon qu’elle découvre des modèles de projet et d’élément qui ont été installées par un fichier .vsix ou un fichier .msi. Si vous possédez des extensions qui utilisent des modèles d’élément ou de projet personnalisé, vous devez mettre à jour vos extensions. Cette rubrique explique la marche à suivre.  
  
 Cette modification affecte uniquement de Visual Studio 2017. Il n’affecte pas les versions antérieures de Visual Studio.  
  
 Si vous souhaitez créer un modèle de projet ou un élément dans le cadre d’une extension VSIX, consultez [création personnalisée de projet et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Modèle d’analyse  
 Auparavant, **devenv /setup** ou **devenv /installvstemplates** analyse le disque local pour rechercher des modèles de projet et d’élément. À compter de la version préliminaire 4, l’analyse est effectuée uniquement pour l’emplacement au niveau utilisateur (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) qui est utilisé pour les modèles générés par le **de fichiers / Export modèles** commande.  
  
 Pour d’autres emplacements (non-utilisateur), vous devez inclure un fichier manifest(.vstman) qui spécifie l’emplacement et autres caractéristiques du modèle. Le fichier .vstman est généré avec le fichier .vstemplate utilisé pour les modèles. Si vous installez votre extension à l’aide d’un fichier .vsix, procéder à l’extension de Visual Studio 2017 la recompilation. Mais si vous utilisez un fichier .msi, vous devez apporter les modifications manuellement. Pour obtenir la liste de ce que vous devez faire pour rendre ces modifications, consultez **mises à niveau des Extensions installées avec un. MSI** plus loin dans cette rubrique.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Comment mettre à jour une Extension VSIX avec le projet ou les modèles d’élément  
 Cette procédure explique comment procéder pour que Visual Studio 2017
1.  Ouvrez la solution dans Visual Studio 2017. Vous devrez mettre à niveau le code. Cliquez sur **OK**.  
  
2.  Après que la mise à niveau terminée, vous devrez peut-être modifier la version de la cible de l’installation. Dans le projet VSIX, ouvrez le fichier source.extension.vsixmanifest et sélectionnez le **cibles d’installation** onglet. Si le **plage de versions** champ est **[14.0]**, cliquez sur **modifier** et modifiez-le pour inclure Visual Studio 2017. Par exemple, vous pouvez la définir **[14.0,15.0]** pour installer l’extension Visual Studio 2015 ou Visual Studio 2017, ou de **[15.0]** pour l’installer à simplement de Visual Studio 2017.  
  
3.  Recompiler le code.  
  
4.  Fermez Visual Studio.  
  
5.  Installer l’extension VSIX.  
  
6.  Vous pouvez tester la mise à jour en effectuant les opérations suivantes :  
  
    1.  Le fichier de l’analyse des modifications est activé par la clé de Registre suivante :  
  
         **reg ajouter hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Après avoir ajouté la clé, exécutez **devenv /installvstemplates**.  
  
    3.  Rouvrez Visual Studio. Vous devez rechercher votre modèle à l’emplacement prévu.  
  
    > [!NOTE]
    >  Les modèles de projet d’extensibilité de Visual Studio ne sont pas disponibles lorsque la clé de Registre est présente. Vous devez supprimer la clé de Registre (et réexécutez **devenv /installvstemplates**) pour les utiliser.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Autres recommandations pour le déploiement de projet et modèles d’élément  
  
-   Évitez d’utiliser des fichiers de modèle zippé. Compressée des fichiers doivent être décompressés afin de récupérer les ressources et le contenu de modèle, par conséquent, elles seront costlier à utiliser. Au lieu de cela, vous devez déployer des modèles de projet et d’élément en tant que fichiers individuels sous leur propre répertoire pour accélérer le processus d’initialisation de modèle. Pour les extensions VSIX, les tâches de génération SDK décompresse automatiquement n’importe quel modèle zippé lors de la création du fichier VSIX.  
  
-   Évitez d’utiliser des entrées d’ID de package/de ressources pour le nom du modèle, la description, l’icône ou l’aperçu afin d’éviter les chargements d’assemblys de ressources inutiles lors de la découverte du modèle. Au lieu de cela, vous pouvez utiliser localisées manifestes pour créer une entrée de modèle pour chacun des paramètres régionaux, qui utilise des propriétés ou des noms localisés.  
  
-   Si vous incluez des modèles en tant qu’éléments de fichier, la génération de manifestes ne peut pas vous donner les résultats attendus. Dans ce cas, vous devez ajouter un manifeste généré manuellement au projet VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modifications du fichier de projet et modèles d’élément  
 Nous vous montrerons les points de différence entre la version de Visual Studio 2015 et la version de Visual Studio « 15 » des fichiers de modèle, afin que vous pouvez créer les nouveaux fichiers correctement.  
  
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
  
 Les informations fournies par le [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) élément reste le même. Le ** \<VSTemplateContainer >** élément pointe vers le fichier .vstemplate du modèle associé.  
  
 Voici le fichier .vstemplate élément par défaut créé par Visual Studio 2015 :  
  
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
  
 Les informations fournies par le ** \<TemplateData >** élément reste le même. Le ** \<VSTemplateContainer >** élément pointe vers le fichier .vstemplate du modèle associé  
  
 Pour plus d’informations sur les différents éléments du fichier .vstman, consultez [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Mises à niveau des Extensions installées avec un. MSI  
 Certaines extensions de fichier MSI déploiement des modèles sur des emplacements de modèles courants tels que les éléments suivants :  
  
-   **\<Répertoire d’installation de Visual Studio > \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 Si votre extension effectue un déploiement MSI, vous devez générer le manifeste de modèle manuellement et assurez-vous qu’il est inclus dans l’installation de l’extension. Vous devez comparer les exemples .vstman répertoriées ci-dessus et [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md). Pour voir ce que vous devez inclure  
  
 Vous devez créer des manifestes séparés pour les modèles de projet et d’élément, et ils doivent pointer vers la racine modèle active comme indiqué ci-dessus. Vous devez créer un manifeste par extension et les paramètres régionaux.  
  
## <a name="troubleshooting-template-installation"></a>Résolution des problèmes d’Installation d’un modèle  
 Si vous rencontrez des problèmes de déploiement de vos modèles de projet ou un élément, vous pouvez activer la journalisation des Diagnostics.  
  
1.  Exécutez la commande suivante pour définir la clé de Registre pour activer la journalisation :  
  
     **reg ajouter HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Démarrez Visual Studio et lancez les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle. Le journal de modèle s’affiche désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. L’initialisation chaque arborescence du modèle ajoute des entrées dans ce fichier journal.  
  
 Le fichier journal contient les colonnes suivantes :  
  
-   **FullPathToTemplate**, qui a les valeurs suivantes :  
  
    -   1 pour le manifeste de déploiement  
  
    -   0 pour le déploiement sur disque  
  
-   **TemplateFileName**  
  
-   Autres propriétés de modèle
