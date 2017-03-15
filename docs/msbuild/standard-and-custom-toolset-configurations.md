---
title: "Standard and Custom Toolset Configurations | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, custom toolset configurations"
  - "MSBuild, msbuild.exe.config"
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Standard and Custom Toolset Configurations
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un ensemble d'outils MSBuild contient des références aux tâches, cibles, et outils que vous pouvez utiliser pour générer un projet d'application.  MSBuild inclut un ensemble d'outils standards, mais vous pouvez également créer des ensembles d'outils personnalisés.  Pour plus d'informations sur la spécification d'un ensemble d'outils, voir [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Configurations d'ensemble d'outils standard  
 MSBuild 12.0 inclut les ensembles d'outils standards suivants :  
  
|ToolsVersion|Chemin d'ensemble d'outils \(comme spécifié dans la propriété de génération MSBuildToolsPath ou de MSBuildBinPath\)|  
|------------------|-------------------------------------------------------------------------------------------------------------------------|  
|2.0|*Windows installation path*\\Microsoft.Net\\Framework\\v2.0.50727\\|  
|3.5|*Windows installation path*\\Microsoft.NET\\Framework\\v3.5\\|  
|4.0|*Windows installation path*\\Microsoft.NET\\Framework\\v4.0.30319\\|  
|12.0|*%ProgramFiles%*\\ MSBuild\\12.0\\bin|  
  
 La valeur `ToolsVersion` identifie l'Ensemble d'outils utilisé par un projet que Visual Studio génère.  Dans [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] la valeur par défaut est « 12.0 » \(indépendamment de la version spécifiée dans le fichier projet\), mais substituez cet attribut à l'aide du commutateur **\/toolsversion** à une invite de commandes.  Pour plus d'informations sur cet attribut et d'autres façons de spécifier `ToolsVersion`, consultez [Overriding ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).  
  
 Si `ToolsVersion` n'est pas spécifié, la clé de Registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\\<numéro de version\>\\DefaultToolsVersion définit `ToolsVersion`, qui est toujours 2.0.  
  
 Les clés de Registre suivantes spécifient le chemin d'installation de MSBuild.exe.  
  
|Clé de Registre|Nom de clé|Valeur de la clé de chaîne|  
|---------------------|----------------|--------------------------------|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\2.0\\|MSBuildToolsPath|Chemin d'installation .NET Framework 2.0|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\3.5\\|MSBuildToolsPath|Chemin d'installation .NET Framework 3.5|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\4.0\\|MSBuildToolsPath|Chemin d'installation .NET Framework 4|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\12.0\\|MSBuildToolsPath|Chemin d'installation MSBuild|  
  
### Sous\-ensembles d'outils  
 Si la clé de Registre dans la table précédente a une sous\-clé, MSBuild l'utilise pour déterminer le chemin d'accès d'un sous\-nœud ensemble d'outils peut substituer le chemin d'accès dans l'ensemble d'outils parent.  La sous\-clef suivante en est un exemple :  
  
 \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\12.0\\12.0  
  
 Si les propriétés sont définies dans l'ensemble d'outils de base et le sous\-nœud ensemble d'outils sélectionné, les définitions de propriété dans le sous\-nœud ensemble d'outils sont utilisées.  Par exemple, l'ensemble d'outils MSBuild 4.0 définit `SDK40ToolsPath` pour indiquer le Kit de développement logiciel 7.0A, mais l'ensemble d'outils 4.0\\11.0 MSBuild définit la même propriété pour indiquer le 8.0A SDK.  Si `VisualStudioVersion` est supprimé, `SDK40ToolsPath` indiquerait 7.0A, mais si `VisualStudioVersion` a la valeur 11.0, la propriété indiquerait à la place 8.0A.  
  
 La propriété de génération `VisualStudioVersion` indique si un sous ensemble d'outils est activé.  Par exemple, une valeur `VisualStudioVersion` « 12.0 » spécifie le sous ensemble d'outils 12.0 MSBuild.  Pour plus d’informations, voir la section Sous\-ensembles d'outils dans [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Nous vous recommandons d'éviter de modifier ces paramètres.  Néanmoins, ajoutez vos propres paramètres et configurez des définitions d'ensembles d'outils personnalisées sur l'ordinateur, comme décrit dans la section suivante.  
  
## Définitions d'ensemble d'outils personnalisées  
 Lorsqu'un ensemble d'outils standard ne répond pas à vos spécifications de génération, vous pouvez créer un ensemble d'outils personnalisé.  Par exemple, vous pouvez avoir un scénario de laboratoire de version dans lequel vous devez avoir un système séparé pour générer des projets [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  En utilisant un ensemble d'outils personnalisé, assignez des valeurs personnalisées à l'attribut `ToolsVersion` lorsque vous créez des projets ou exécutez MSBuild.exe.  Ainsi, utilisez également la propriété `$(MSBuildToolsPath)` pour importer des fichiers .targets à partir de ce répertoire, et définissez vos propres propriétés d'ensembles d'outils personnalisées qui peuvent être utilisées pour tout projet qui utilise cet ensemble d'outils.  
  
 Spécifiez un ensemble d'outils personnalisé dans le fichier de configuration pour MSBuild.exe \(ou pour l'outil personnalisé hôte du moteur MSBuild si c'est ce que vous utilisez\).  Par exemple, le fichier de configuration pour MSBuild.exe pourrait inclure la définition d'ensemble d'outils suivante si vous souhaitez substituer le comportement par défaut ToolsVersion 12,0.  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` doit également être défini dans le fichier de configuration, comme suit.  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Pour être lu correctement, `<configSections>` doit être la première sous\-section dans la section `<configuration>`.  
  
 `ToolsetConfigurationSection` est une section de configuration personnalisée qui peut être utilisée par tout hôte MSBuild pour la configuration personnalisée.  Si vous utilisez un ensemble d'outils personnalisé, un hôte ne doit rien faire pour initialiser le moteur de génération, excepté fournir les entrées de fichier de configuration.  En définissant des entrées dans le Registre, spécifiez des ensembles d'outils d'ordinateur qui s'appliquent à MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]et tous les hôtes de MSBuild.  
  
> [!NOTE]
>  Si un fichier de configuration définit des paramètres pour un `ToolsVersion` qui a déjà été défini dans le Registre, les deux définitions ne sont pas fusionnées.  La définition du fichier de configuration a priorité et les paramètres dans le Registre pour ce `ToolsVersion` sont ignorés.  
  
 Les propriétés suivantes sont spécifiques à la valeur de `ToolsVersion` utilisée dans les projets :  
  
-   **$ \(MSBuildBinPath\)** \- MSBuildBinPath a la valeur `ToolsPath` qui est spécifiée dans le Registre ou le fichier de configuration dans lequel est défini `ToolsVersion`.  Le paramètre `$(MSBuildToolsPath)` dans le Registre ou le fichier de configuration spécifie l'emplacement de tâches clefs et des objectifs.  Dans le fichier projet, cela mappe à la propriété $\(MSBuildBinPath\) et également à la propriété $\(MSBuildToolsPath\).  
  
-   `$(MSBuildToolsPath)` est une propriété réservée qui est fournie par la propriété MSBuildToolsPath spécifiée dans le fichier de configuration. \(Cette propriété se substitue à `$(MSBuildBinPath)`.  Toutefois, `$(MSBuildBinPath)` est retenu pour la compatibilité.\) Un ensemble d'outils personnalisé doit définir `$(MSBuildToolsPath)` ou `$(MSBuildBinPath)` mais pas les deux, sauf s'ils ont tous les deux la même valeur.  
  
 Vous pouvez également ajouter des propriétés personnalisées spécifiques au ToolsVersion au fichier de configuration en utilisant la même syntaxe que celle utilisée pour ajouter la propriété MSBuildToolsPath.  Pour rendre ces propriétés personnalisées disponibles pour le fichier projet, utilisez le même nom que la valeur spécifiée dans le fichier de configuration.  Vous pouvez définir des ensembles d'outils mais pas des sous ensembles d'outils dans le fichier de configuration.  
  
## Voir aussi  
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)