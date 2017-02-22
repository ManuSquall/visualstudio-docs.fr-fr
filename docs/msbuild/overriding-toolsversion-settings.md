---
title: "Overriding ToolsVersion Settings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, overriding ToolsVersion setting"
  - "MSBuild, building solutions with"
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Overriding ToolsVersion Settings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier l'ensemble d'outils des projets et des solutions de trois façons différentes :  
  
1.  en utilisant le commutateur `/ToolsVersion` \(ou `/tv`, en abrégé\) lorsque vous générez le projet ou la solution depuis la ligne de commande  
  
2.  en définissant le paramètre `ToolsVersion` dans la tâche MSBuild.  
  
3.  en définissant la propriété `$(ProjectToolsVersion)` sur un projet dans une solution.  Cela vous permet de générer un projet dans une solution avec une version de l'ensemble d'outils qui diffère de celle des autres projets.  
  
## Substituer les paramètres ToolsVersion de Projets et solutions avec les générations de ligne de commande  
 Bien que les projets Visual Studio soient généralement générés avec l'attribut ToolsVersion spécifié dans le fichier projet, vous pouvez utiliser le commutateur `/ToolsVersion` \(ou `/tv`\) sur la ligne de commande pour remplacer cette valeur et générer tous les projets et les dépendances qui existent entre eux avec un autre ensemble d'outils.  Par exemple :  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 Dans cet exemple, tous les projets sont générés à l'aide de ToolsVersion 12.0. \(Toutefois, consultez la section « Ordre de priorité » présentée ultérieurement dans cette rubrique.\)  
  
 Lorsque vous utilisez le commutateur `/tv` dans la ligne de commande, vous pouvez utiliser la propriété `$(ProjectToolsVersion)` dans les projets individuels pour les générer avec une valeur ToolsVersion différente des autres projets de la solution.  
  
## Substitution du paramètre ToolsVersion à l'aide du paramètre ToolsVersion de la tâche MSBuild.  
 La tâche MSBuild est le moyen principal d'un projet pour en générer un autre.  Pour permettre à la tâche MSBuild de générer un projet avec un ToolsVersion différent de celui spécifié dans le projet, elle fournit un paramètre de tâche facultatif nommé `ToolsVersion`.  L'exemple suivant montre comment utiliser ce paramètre :  
  
1.  Créez un fichier nommé `projectA.proj` et qui contient le code suivant :  
  
    ```  
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
  
2.  Créez un autre fichier nommé `projectB.proj` et qui contient le code suivant :  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  Entrez la commande suivante à une invite de commandes :  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  La sortie suivante s'affiche.  Pour `projectA`, le paramètre `/toolsversion:3.5` sur la ligne de commande remplace le paramètre `ToolsVersion=12.0` dans la balise `Project`.  
  
     `ProjectB` est appelé par une tâche dans `projectA`.  Cette tâche contient `ToolsVersion=2.0`, qui remplace les autres paramètres `ToolsVersion` pour `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## Ordre de priorité  
 L'ordre de priorité \(du plus élevé au plus faible\) utilisé pour déterminer `ToolsVersion` est :  
  
1.  L'attribut `ToolsVersion` de la tâche MSBuild utilisée pour générer le projet, si existant.  
  
2.  Commutateur `/toolsversion` \(ou `/tv`\) utilisé dans la commande msbuild.exe, le cas échéant.  
  
3.  Si la variable d'environnement `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` est définie, utilisez le `ToolsVersion` actuel.  
  
4.  Si la variable d'environnement `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` est définie et que le `ToolsVersion` défini dans le fichier projet est supérieur au `ToolsVersion` actuel, utilisez le `ToolsVersion` actuel.  
  
5.  Si la variable d'environnement `MSBUILDLEGACYDEFAULTTOOLSVERSION` est définie, ou si `ToolsVersion` n'est pas défini, les étapes suivantes sont utilisées :  
  
    1.  Attribut `ToolsVersion` de l'élément [Project](../msbuild/project-element-msbuild.md) du fichier de projet.  Si cet attribut n'existe pas, il est considéré comme la version actuelle.  
  
    2.  La valeur par défaut dans le fichier MSBuild.exe.config.  
  
    3.  La version des outils par défaut dans le Registre.  Pour plus d'informations, consultez [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Si la variable d'environnement `MSBUILDLEGACYDEFAULTTOOLSVERSION` n'est pas définie, les étapes suivantes sont utilisées :  
  
    1.  Si la variable d'environnement `MSBUILDDEFAULTTOOLSVERSION` a la valeur d'un `ToolsVersion` existant, utilisez\-le.  
  
    2.  Si `DefaultOverrideToolsVersion` est défini dans MSBuild.exe.config, utilisez\-le.  
  
    3.  Si `DefaultOverrideToolsVersion` est défini dans le registre, utilisez\-le.  
  
    4.  Autrement, utilisez `ToolsVersion` en cours.  
  
## Voir aussi  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)