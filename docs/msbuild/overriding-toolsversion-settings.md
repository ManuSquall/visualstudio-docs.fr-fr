---
title: Substitution des paramètres ToolsVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e58756dc1786f3c15fddc57399b59711d92074a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005369"
---
# <a name="override-toolsversion-settings"></a>Écraser les paramètres ToolsVersion
Vous pouvez changer l’Ensemble d’outils pour les projets et solutions de trois manières :  
  
1.  Avec le commutateur `-ToolsVersion` (ou `-tv` en abrégé) lors de la génération du projet ou de la solution en ligne de commande.  
  
2.  En définissant le paramètre `ToolsVersion` sur la tâche MSBuild.  
  
3.  En définissant la propriété `$(ProjectToolsVersion)` sur un projet dans une solution. Cela vous permet de générer un projet dans une solution avec une version de l’Ensemble d’outils qui diffère de celle des autres projets.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Écraser les paramètres ToolsVersion de projets et de solutions sur des générations en ligne de commande  
 Bien que les projets Visual Studio soient généralement générés avec la version ToolsVersion spécifiée dans le fichier projet, vous pouvez utiliser le commutateur `-ToolsVersion` (ou `-tv`) sur la ligne de commande pour substituer cette valeur et générer tous les projets et leurs dépendances projet-à-projet avec un autre Ensemble d’outils. Par exemple :  
  
```cmd  
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug  
```  
  
 Dans cet exemple, tous les projets sont générés à l’aide de ToolsVersion 12.0. (Voir cependant la section [Ordre de priorité](#order-of-precedence) plus loin dans cette rubrique.)  
  
 Quand vous utilisez le commutateur `-tv` sur la ligne de commande, vous pouvez éventuellement utiliser la propriété `$(ProjectToolsVersion)` dans des projets pour les générer avec une autre valeur de ToolsVersion que les autres projets dans la solution.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Écraser les paramètres ToolsVersion avec le paramètre ToolsVersion de la tâche MSBuild  
 La tâche MSBuild est le moyen principal par lequel un projet peut en générer un autre. Pour permettre à la tâche MSBuild de générer un projet avec des paramètres ToolsVersion différents de ceux spécifiés dans le projet, un paramètre de tâche facultatif nommé `ToolsVersion` est disponible. L’exemple suivant illustre comment utiliser ce paramètre :  
  
1.  Créez un fichier nommé *projectA.proj* et contenant le code suivant :  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Créez un autre fichier nommé *projectB.proj* et contenant le code suivant :  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  À l’invite de commandes, tapez la commande suivante :  
  
    ```cmd  
    msbuild projectA.proj -t:go -toolsversion:3.5  
    ```  
  
4.  La sortie suivante apparaît. Pour `projectA`, le paramètre `-toolsversion:3.5` de la ligne de commande remplace le paramètre `ToolsVersion=12.0` dans la balise `Project`.  
  
     `ProjectB` est appelé par une tâche dans `projectA`. Cette tâche a `ToolsVersion=2.0`, qui remplace les autres paramètres `ToolsVersion` pour `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Ordre de priorité  
 L’ordre de priorité, du plus élevé au plus bas, utilisé pour déterminer `ToolsVersion` est le suivant :  
  
1.  L’attribut `ToolsVersion` sur la tâche MSBuild utilisé pour générer le projet, le cas échéant.  
  
2.  Le commutateur `-toolsversion` (ou `-tv`) utilisé dans la commande msbuild.exe, le cas échéant.  
  
3.  Si la variable d’environnement `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` est définie, utiliser le paramètre `ToolsVersion` actuel.  
  
4.  Si la variable d’environnement `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` est définie et que la valeur de `ToolsVersion` définie dans le fichier projet est supérieure à la valeur actuelle de `ToolsVersion`, utiliser la valeur actuelle de `ToolsVersion`.  
  
5.  Si la variable d’environnement `MSBUILDLEGACYDEFAULTTOOLSVERSION` est définie, ou si `ToolsVersion` n’est pas défini, l’ordre de priorité est le suivant :  
  
    1.  L’attribut `ToolsVersion` de l’élément [Project](../msbuild/project-element-msbuild.md) du fichier projet. Si cet attribut n’existe pas, il est supposé être égal à la version actuelle.  
  
    2.  La version des outils par défaut dans le fichier *MSBuild.exe.config*.  
  
    3.  La version des outils par défaut dans le Registre. Pour plus d’informations, voir [Configurations standard et personnalisées des ensembles d’outils](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Si la variable d’environnement `MSBUILDLEGACYDEFAULTTOOLSVERSION` n’est pas définie, l’ordre de priorité est le suivant :  
  
    1.  Si la variable d’environnement `MSBUILDDEFAULTTOOLSVERSION` est définie sur une `ToolsVersion` qui existe, elle est utilisée.  
  
    2.  Si `DefaultOverrideToolsVersion` est défini dans *MSBuild.exe.config*, il est utilisé.  
  
    3.  Si `DefaultOverrideToolsVersion` est défini dans le Registre, il est utilisé.  
  
    4.  Sinon, utilisez la valeur actuelle de `ToolsVersion`.  
  
## <a name="see-also"></a>Voir aussi  
 [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)   
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Configurations standard et personnalisées des ensembles d’outils](../msbuild/standard-and-custom-toolset-configurations.md)