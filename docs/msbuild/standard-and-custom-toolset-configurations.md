---
title: Configurations standard et personnalisée de l’ensemble d’outils | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 855bd7af4372f5216abab3d6ddd45ec8f7809baa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="standard-and-custom-toolset-configurations"></a>Configurations standard et personnalisée de l'ensemble d'outils
Un ensemble d’outils MSBuild contient des références à des tâches, des cibles et des outils que vous pouvez utiliser pour générer un projet d’application. MSBuild inclut un ensemble d’outils standard, mais vous pouvez également créer des ensembles d’outils personnalisés. Pour plus d’informations sur la façon de spécifier un ensemble d’outils, consultez [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>Configurations standard d’ensembles d’outils  
 MSBuild 15.0 inclut les ensembles d’outils standard suivants :  
  
|ToolsVersion|Chemin de l’ensemble d’outils (tel que spécifié dans la propriété de build MSBuildToolsPath ou MSBuildBinPath)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Chemin d’installation de Windows*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Chemin d’installation de Windows*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Chemin d’installation de Windows*\Microsoft.NET\Framework\v4.0.30319\|  
|15.0|*Dossier d’installation de Visual Studio*\MSBuild\15.0\bin|  
  
 La valeur de `ToolsVersion` détermine l’ensemble d’outils utilisé par un projet généré par Visual Studio. Dans Visual Studio 2017, la valeur par défaut est « 15.0 » (quelle que soit la version spécifiée dans le fichier projet), mais vous pouvez remplacer cet attribut avec le commutateur **/toolsversion** à une invite de commandes. Pour plus d’informations sur cet attribut et sur d’autres façons de spécifier `ToolsVersion`, consultez [Substitution des paramètres ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Visual Studio 2017 n’utilise pas une clé de Registre pour le chemin à MSBuild. Pour les versions de MSBuild antérieures à 15.0 qui sont installées avec Visual Studio 2017, les clés de Registre suivantes spécifient le chemin d’installation de MSBuild.exe.  
  
|Clé de Registre|Nom de clé|Valeur de clé de type chaîne|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Chemin d’installation du .NET Framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Chemin d’installation du .NET Framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Chemin d’installation du .NET Framework 4|  
  
### <a name="sub-toolsets"></a>Sous-ensembles d'outils  
 Si la clé de Registre du tableau précédent a une sous-clé, MSBuild l’utilise pour déterminer le chemin d’un sous-ensemble d’outils qui remplace le chemin dans l’ensemble d’outils parent. Voici un exemple de sous-clé :  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Si des propriétés sont définies à la fois dans l’ensemble d’outils de base et dans le sous-ensemble d’outils sélectionné, les définitions de propriétés dans le sous-ensemble d’outils sont utilisées. Par exemple, l’ensemble d’outils MSBuild 4.0 définit `SDK40ToolsPath` comme pointant vers le SDK 7.0A, mais l’ensemble d’outils MSBuild 4.0\11.0 définit la même propriété comme pointant vers le SDK 8.0A. Si `VisualStudioVersion` n’est pas défini, `SDK40ToolsPath` pointe vers 7.0A, mais si `VisualStudioVersion` est défini comme pointant vers 11.0, la propriété pointe alors vers 8.0A.  
  
 La propriété de build `VisualStudioVersion` indique si un sous-ensemble d’outils devient actif. Par exemple, la valeur « 12.0 » pour `VisualStudioVersion` spécifie le sous-ensemble d’outils MSBuild 12.0. Pour plus d’informations, consultez la section Sous-ensembles d’outils de [Ensemble d’outils MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Nous vous recommandons de ne pas modifier ces paramètres. Vous pouvez néanmoins ajouter vos propres paramètres et spécifier des définitions d’ensembles d’outils personnalisés à l’échelle de l’ordinateur, comme décrit dans la section suivante.  
  
## <a name="custom-toolset-definitions"></a>Définitions d’ensembles d’outils personnalisés  
 Quand un ensemble d’outils standard ne répond pas à vos spécifications pour la génération, vous pouvez créer un ensemble d’outils personnalisé. Par exemple, vous pouvez avoir un scénario de laboratoire de génération dans lequel vous devez disposer d’un système distinct pour la génération de projets [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Avec un ensemble d’outils personnalisé, vous pouvez affecter des valeurs personnalisées à l’attribut `ToolsVersion` quand vous créez des projets ou que vous exécutez MSBuild.exe. Ce faisant, vous pouvez également utiliser la propriété `$(MSBuildToolsPath)` pour importer des fichiers .targets à partir de ce répertoire, ainsi que définir vos propres propriétés de l’ensemble d’outils personnalisé qui peuvent être utilisées pour un projet utilisant cet ensemble d’outils.  
  
 Spécifiez un ensemble d’outils personnalisé dans le fichier de configuration pour MSBuild.exe (ou pour l’outil personnalisé qui héberge le moteur MSBuild si c’est ce que vous utilisez). Par exemple, le fichier de configuration pour MSBuild.exe peut inclure la définition d’ensemble d’outils suivante si vous voulez remplacer le comportement par défaut de ToolsVersion 15.0.  
  
```xml  
<msbuildToolsets default="15.0">  
   <toolset toolsVersion="15.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` doit également être défini comme suit dans le fichier de configuration.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=15.1.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Pour que la lecture se fasse correctement, `<configSections>` doit être la première sous-section de la section `<configuration>`.  
  
 `ToolsetConfigurationSection` est une section de configuration personnalisée qui peut être utilisée par n’importe quel hôte MSBuild pour une configuration personnalisée. Si vous utilisez un ensemble d’outils personnalisé, un hôte n’a rien à faire pour initialiser le moteur de génération, sauf fournir les entrées du fichier de configuration. En définissant des entrées dans le Registre, vous pouvez spécifier des ensembles d’outils à l’échelle de l’ordinateur, qui s’appliquent à MSBuild.exe, à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et à tous les hôtes de MSBuild.  
  
> [!NOTE]
>  Si un fichier de configuration définit des paramètres pour une `ToolsVersion` qui a déjà été définie dans le Registre, les deux définitions ne sont pas fusionnées. La définition du fichier de configuration a priorité et les paramètres du Registre pour cette `ToolsVersion` sont ignorés.  
  
 Les propriétés suivantes sont spécifiques à la valeur de `ToolsVersion` qui est utilisée dans les projets :  
  
-   **$(MSBuildBinPath)** est défini sur la valeur de `ToolsPath` qui est spécifiée dans le Registre ou dans le fichier de configuration où `ToolsVersion` est définie. Le paramètre `$(MSBuildToolsPath)` dans le Registre ou dans le fichier de configuration spécifie l’emplacement des tâches et des cibles principales. Dans le fichier projet, ceci correspond à la propriété $(MSBuildBinPath) et à la propriété $(MSBuildToolsPath).  
  
-   `$(MSBuildToolsPath)` est une propriété réservée qui est fournie par la propriété MSBuildToolsPath spécifiée dans le fichier de configuration. (Cette propriété remplace `$(MSBuildBinPath)`. Cependant, `$(MSBuildBinPath)` est conservé pour des raisons de compatibilité.) Un ensemble d’outils personnalisé doit définir `$(MSBuildToolsPath)` ou `$(MSBuildBinPath)`, mais pas les deux, sauf si tous les deux ont la même valeur.  
  
 Vous pouvez également ajouter des propriétés personnalisées spécifiques à ToolsVersion au fichier de configuration, en utilisant la même syntaxe que celle utilisée pour ajouter la propriété MSBuildToolsPath. Pour rendre ces propriétés personnalisées disponibles pour le fichier projet, utilisez le même nom que celui de la valeur spécifiée dans le fichier de configuration. Dans le fichier de configuration, vous pouvez définir des ensembles d’outils, mais pas des sous-ensembles d’outils.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)