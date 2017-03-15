---
title: "Commandes doivent &#234;tre ex&#233;cut&#233;s apr&#232;s l&#39;Installation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes de post-installation"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Commandes doivent &#234;tre ex&#233;cut&#233;s apr&#232;s l&#39;Installation
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si vous déployez votre extension via un fichier .msi, vous devez exécuter `devenv /setup` dans le cadre de votre installation afin de découvrir vos extensions Visual Studio.  
  
> [!NOTE]
>  Les informations contenues dans cette rubrique s'applique à la recherche de DevEnv avec Visual Studio 2008 et versions antérieures. Pour plus d'informations sur la découverte DevEnv avec les versions ultérieures de Visual Studio, consultez [Détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).  
  
## Recherche de devenv.exe  
 Vous pouvez rechercher de chaque version devenv.exe Registre valeurs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écrivant des programmes d'installation, à l'aide de la RegLocator Table et AppSearch Table pour stocker les valeurs de Registre en tant que propriétés. Pour plus d'informations, consultez [Détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).  
  
### Lignes de la table RegLocator pour localiser devenv.exe à partir de différentes versions de Visual Studio  
  
|Signature\_|Racine|Clé|Nom|Type|  
|-----------------|------------|---------|---------|----------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### Lignes de la table pour les lignes correspondantes de la table RegLocator AppSearch  
  
|Propriété|Signature\_|  
|---------------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 Par exemple, le programme d'installation de Visual Studio écrit la valeur de Registre de **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** comme **C:\\VS2008\\Common7\\IDE\\devenv.exe**, un chemin d'accès complet au fichier exécutable du programme d'installation doit s'exécuter.  
  
 **Remarque** parce que la colonne de Type de RegLocator est 2, il n'est pas nécessaire de spécifier des informations de version supplémentaires dans la Table de la Signature.  
  
## Devenv.exe en cours d'exécution  
 Après l'action standard s'exécute le programme d'installation AppSearch, chaque propriété de la table AppSearch a la valeur pointant vers le fichier devenv.exe pour la version correspondante de Visual Studio. Si une des valeurs de Registre spécifiés ne sont pas présente, car cette version de Visual Studio n'est pas installée, la propriété spécifiée a la valeur null.  
  
 Windows Installer prend en charge un fichier exécutable vers lequel pointe une propriété par une action personnalisée tapez 50. L'action personnalisée doit inclure les options d'exécution dans le script, msidbCustomActionTypeInScript \(1024\) et msidbCustomActionTypeCommit \(512\), pour vous assurer que le VSPackage a bien été installé avant son intégration dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, consultez CustomAction Options de Table et Custom Action dans le Script d'exécution.  
  
 Actions personnalisées de type 50 spécifient la propriété contenant l'exécutable en tant que la valeur de la colonne Source et les arguments de ligne de commande dans la colonne cible.  
  
### Lignes du tableau CustomAction exécutez devenv.exe  
  
|Action|Type|Source|une cible|  
|------------|----------|------------|---------------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/Setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/Setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/Setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/Setup|  
  
 Actions personnalisées doivent être créées dans la table InstallExecuteSequence à planifier leur exécution lors de l'installation. La propriété correspondante dans chaque ligne de la colonne Condition permet d'éviter que l'action personnalisée en cours d'exécution si cette version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n'est pas installé sur le système.  
  
> [!NOTE]
>  `Null` pour évaluent les propriétés `False` lorsqu'il est utilisé dans les conditions.  
  
 La valeur de la colonne de séquence pour chaque action personnalisée dépend d'autres valeurs de séquence dans votre package Windows Installer. Valeurs de séquence doivent être telles que les actions personnalisées devenv.exe identification près possible immédiatement avant l'action standard InstallFinalize.  
  
### Table InstallExecuteSequence pour planifier les actions personnalisées devenv.exe  
  
|Action|Condition|Séquence|  
|------------|---------------|--------------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## Voir aussi  
 [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)