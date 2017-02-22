---
title: "La gestion des Associations de fichiers de c&#244;te &#224; c&#244;te | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verbes, la configuration par défaut"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# La gestion des Associations de fichiers de c&#244;te &#224; c&#244;te
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si votre VSPackage fournit des associations de fichiers, vous devez décider comment gérer côte à côte les installations auxquelles une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelée pour ouvrir un fichier.  les formats de fichier incompatibles composent le problème.  
  
 Les utilisateurs s'attendent à ce qu'une nouvelle version d'un produit soit compatible avec les versions antérieures, afin que les fichiers existants puissent être chargés dans une nouvelle version sans les données enregistrées.  Idéalement, votre VSPackage peut charger et d'enregistrer les formats de fichier des versions antérieures.  Si ce n'est pas le cas, vous devez donner de mettre à niveau le format de fichier à la nouvelle version de votre VSPackage.  Le côté incliné de cette approche est que le fichier mis à jour ne peut pas être ouvert dans la version antérieure.  
  
 Pour éviter ce problème, vous pouvez modifier les extensions lorsque les formats de fichier sont incompatibles.  Par exemple, la version 1 de votre VSPackage peut utiliser l'extension, .mypkg10, et la version 2 peut utiliser l'extension, .mypkg20.  cette différence identifie le VSPackage qui ouvre un fichier particulier.  Si vous ajoutez plus récent VSPackages à la liste des programmes associés à une ancienne extension, les utilisateurs peuvent cliquer avec le bouton droit sur le fichier et choisir pour l'ouvrir dans un VSPackage plus récent.  À ce stade, votre VSPackage peut offrir de mettre à niveau le fichier vers le nouveau format ou d'ouvrir le fichier et pour assurer la compatibilité avec les versions antérieures du VSPackage.  
  
> [!NOTE]
>  Vous pouvez combiner ces approches.  Par exemple, vous pouvez garantir la compatibilité descendante en chargeant un fichier et plus anciennes donner de mettre à niveau le format de fichier lorsque l'utilisateur enregistre.  
  
## rencontrer le problème  
 Si vous souhaitez multiple côte à côte VSPackages pour utiliser la même extension, sélectionnez la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associée à l'extension.  Voici deux possibilités :  
  
-   Ouvrez le fichier dans la version la plus récente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installé sur l'ordinateur d'un utilisateur.  
  
     Dans cette approche, votre programme d'installation est chargé de déterminer la version la plus récente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et d'inclusion que dans l'entrée du Registre entrée pour l'association de fichier.  Dans un package Windows Installer, vous pouvez inclure des actions personnalisées pour définir une propriété qui indique la version la plus récente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  Dans ce contexte, « dernier » signifie « dernière version prise en charge. » Ces entrées de programme d'installation ne détectent pas automatiquement une version suivante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Les entrées de [Détecter la configuration système requise](../extensibility/internals/detecting-system-requirements.md) et dans [Commandes doivent être exécutés après l'Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) sont semblables à celles présentées ici et sont requises pour prendre en charge les versions supplémentaires de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Les lignes suivantes dans la table CustomAction définissez la propriété de DEVENV\_EXE\_LATEST pour être une propriété définie par les tableaux d'AppSearch et de RegLocator traités dans [Commandes doivent être exécutés après l'Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md).  Les lignes de la table d'InstallExecuteSequence planifier les actions personnalisées haut dans la séquence d'exécuter.  Les valeurs de la colonne de la condition effectuent le travail de logique :  
  
    -   Visual Studio .NET 2002 est la version la plus récente s'il s'agit de la seule présente version.  
  
    -   Visual Studio .NET 2003 est la version la plus récente que si elle est présente et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est pas présent.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est la version la plus récente s'il s'agit de la seule présente version.  
  
     Le résultat .NET est que DEVENV\_EXE\_LATEST contient le chemin d'accès de la version la plus récente du fichier devenv.exe.  
  
    ### Lignes de table CustomAction qui déterminent la version la plus récente de Visual Studio  
  
    |Action|Type|Source|Cible|  
    |------------|----------|------------|-----------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2002\]|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2003\]|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2005\]|  
  
    ### Lignes de table d'InstallExecuteSequence qui déterminent la version la plus récente de Visual Studio  
  
    |Action|Condition|séquence|  
    |------------|---------------|--------------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 AND NOT \(DEVENV\_EXE\_2003 OR DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003 AND NOT DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     Vous pouvez utiliser la propriété de DEVENV\_EXE\_LATEST dans le tableau de Registre du package Windows Installer pour écrire le HKEY\_CLASSES\_ROOT \\*ProgId*\\Shell\\Open\\Command key's default value, \[DEVENV\_EXE\_LATEST\] « %1 "  
  
-   Exécutez un programme partagé de lancement qui peut réaliser le meilleur choix des versions disponibles d'un VSPackage.  
  
     Les développeurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avez choisi cette approche pour gérer les exigences complexes plusieurs formats des solutions et des projets qui résultent de plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dans cette approche, vous enregistrez un programme de lancement en tant que gestionnaire d'extension.  Le lancement examine le fichier et décide que la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage peuvent traiter ce fichier particulier.  Par exemple, si un utilisateur ouvre un fichier qui a été en dernier enregistré par une version particulière de votre VSPackage, le lancement peut lancer ce VSPackage dans la version correspondante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En outre, un utilisateur peut configurer le lancement pour démarrer toujours la dernière version.  Un lanceur peut également demander un utilisateur à mettre à niveau le format du fichier.  Si le format du fichier inclut un numéro de version, le lancement peut informer l'utilisateur si le format de fichier est une version plus loin qu'un ou plusieurs des VSPackages installé.  
  
     Le lancement doit être dans un composant Windows Installer qui est partagé avec toutes les versions de votre VSPackage.  Ce processus s'assure que la version la plus récente est installée et n'est pas supprimé jusqu'à ce que toutes les versions de votre VSPackage soient désinstallées.  De cette façon, les associations de fichiers et d'autres entrées de Registre du composant de lancement sont conservées même si une version du VSPackage est désinstallée.  
  
## Désinstallation et associations de fichiers  
 Désinstallation un VSPackage qui écrit des entrées du Registre pour des associations de fichiers supprime les associations de fichier.  par conséquent, l'extension n'a aucun programme associé.  Windows Installer « ne récupère pas » les entrées du Registre qui ont été ajoutées lorsque le VSPackage a été installé.  Voici quelques techniques de résoudre des associations de fichiers d'un utilisateur :  
  
-   Utilisez un composant partagé de lancement comme décrit précédemment.  
  
-   Indiquez l'utilisateur exécuter une réparation de la version du VSPackage que l'utilisateur souhaite posséder l'association de fichier.  
  
-   fournissez un programme exécutable distinct qui réécrit les entrées du Registre appropriées.  
  
-   Fournissez les options de configuration la page ou dans la boîte de dialogue qui permettent aux utilisateurs de choisir des associations de fichiers et libérer les associations perdues.  Indiquez les utilisateurs l'exécuter après la désinstallation.  
  
## Voir aussi  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Inscription des verbes pour les Extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)